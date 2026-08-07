# Xbox 100% Completion Guide — LLM Skill

An LLM skill that generates an **optimal, phase-by-phase route to 100% completion and all achievements** for any Xbox game. Works with [Claude](https://claude.com/claude-code) out of the box, and with **any LLM or agent that can follow a markdown instruction file** — a custom GPT, a Gemini Gem, an open-source agent framework, or a plain system prompt.

Point it at a game, and the model researches the current achievement list, flags every missable, front-loads the upgrades that make the rest of the game easier, and lays out a route that minimizes backtracking — grounded in what's actually reachable at each point in the game, not just a raw collectible dump.

## What it does

When you name an Xbox game and ask how to 100% it, the skill drives the model through a disciplined process:

1. **Research the game** — web-searches for the current achievement list, missables (including systemic ones like losable companions or reputations), per-category completion requirements, verified exploit methods, exact collectible counts, and specific locations for location-dependent tasks (never relies on training data alone, since these change over time).
2. **Sync your earned achievements** — optionally pulls your real achievement state for the game from your Xbox profile, so the guide starts from what you already have (see [Syncing your achievements](#syncing-your-achievements) below).
3. **Identify missables first** — extracts every missable achievement with its trigger point and the exact action required, flagging any that conflict (i.e. require multiple playthroughs).
4. **Identify power-unlocks** — surfaces upgrades and rewards (infinite sprint, fireproof status, money/XP exploits, protective perks, etc.) worth front-loading even when they feel like a detour.
5. **Check cross-system interactions** — catches orderings where one task accidentally fights another: redundant grinds, resource requirements backfilled by guaranteed rewards, daily caps, acquire-vs-use location mismatches, and anything that advances on elapsed time rather than player action.
6. **Identify area-gated content** — determines what's reachable now vs. locked behind story progress, so it never tells you to sweep an area you can't fully access yet.
7. **Build the phased route** — verifies the actual unlock *sequence* against sources, then orders everything by missable protection → power-unlocks → accessible sweeps → minimal backtracking → story gating, with no unordered "do these whenever" buckets and no overlapping checklist items. Audits the final "post-story cleanup" phase item by item so nothing lands there by default — content that isn't genuinely gated late moves to the earliest phase where it's actually reachable, and whatever verifiably stays late says why. Routes whole-game cumulative requirements (e.g. max every weapon) as an early habit with mid-route checkpoints, not an end-game grind. Never parks you in front of a clock: anything that advances on elapsed time (property income, build timers, a call that arrives days later) is started at the earliest point it can be and left running underneath real steps, so timers overlap instead of queueing into back-to-back "wait a few in-game days" instructions. Where the steps are chained rather than independent — see an NPC, wait days, see them again, wait again — the links get interleaved through the route so the days pass while you're doing other things, each one noting where the previous link was.
8. **Enforce clarity standards** — names areas explicitly, defines jargon on first use, states precise collectible counts, separates *achievements* from *100% requirements*, and never invents false precision.
9. **Surface exploits and bugs** — including whether they disable achievements, whether they've been patched, and the known "stuck at 99%" culprits.

### Syncing your achievements

The guide can start from your real progress instead of assuming a fresh save. If you sync, earned achievements come pre-checked and badged with their unlock date, the route opens at the phase you're actually in, missables you've already earned stop reading as warnings, and any missable whose window has closed *unearned* gets pushed to the top of the page with the actual remedy researched (New Game+, mission replay, or an honest "this save can't get it").

Four ways to sync, in preference order — you authenticate yourself in all of them, and the model never asks for your Microsoft account password:

| Path | What it needs |
| --- | --- |
| **Personal API key** | A free key from a third-party Xbox Live API service such as [OpenXBL](https://xbl.io/) (150 requests/hour on the free tier) — see [setup](#setting-up-an-openxbl-key) below |
| **Official Xbox Live REST** | An XSTS token from the Microsoft-account OAuth chain — e.g. [`xbox-webapi-python`](https://github.com/OpenXbox/xbox-webapi-python) plus your own Azure AD app registration |
| **Signed-in browser** | Browser automation plus an Xbox session you signed in to yourself |
| **Manual** | Screenshots of the console achievement list, a pasted list, or a public TrueAchievements/Xbox profile |

Two things the skill is deliberately strict about. **Achievements are profile-wide and permanent; in-game 100% completion is save-bound** — so a sync pre-checks achievement items but never a mission, collectible sweep, or 100% task, because an achievement banked on an old save doesn't mean the content is done on your current one. And **re-syncing merges, it never overwrites** — anything you checked by hand stays checked, since plenty of 100% requirements have no achievement attached at all.

No API key, token, or XUID is ever written into the generated HTML file, and the file makes no live calls to any Xbox service — the sync runs at build time and its results are baked in as data, so the guide stays safe to share.

#### Setting up an OpenXBL key

1. Go to [xbl.io](https://xbl.io/) and sign in **with your own Microsoft account** — the same one your Xbox profile is on. This is a standard Microsoft OAuth consent screen; you're granting a read-only app access to your own profile, and no password is ever shared with the model.
2. In your profile, create an app and generate an **API key**. Copy it.
3. Paste the key into your session when the skill asks for it. Treat it like a password: it can read your Xbox profile data, and it's regenerable from the same page if it leaks.

Every request sends the key as an `x-authorization` header. The endpoints the skill uses, from [OpenXBL's OpenAPI spec](https://github.com/OpenXBL/Docs):

| Call | Purpose |
| --- | --- |
| `GET /api/v2/account` | Your gamertag, XUID, gamerscore |
| `GET /api/v2/player/titleHistory` | Games you've launched, with title IDs |
| `GET /api/v2/achievements/player/{xuid}/title/{titleId}` | Per-title achievements, **Xbox One/Series** |
| `GET /api/v2/achievements/x360/{xuid}/title/{titleId}` | Per-title achievements, **Xbox 360** |
| `GET /api/v2/achievements/stats/{titleId}` | Your stats for a title (progression numbers) |

Base URL `https://xbl.io`. Free tier is 150 requests/hour — a sync costs about three, so it's not a constraint in practice. Watch `X-RateLimit-Remaining`; a 429 means you're over.

The 360-vs-modern split matters more than it looks: a 360-era game queried against the modern endpoint returns nothing at all, which is indistinguishable from "you've earned nothing." The skill checks both families before believing an empty result.

Worth knowing if you go looking yourself: the GDK/XSAPI **Achievements Manager** (`XblAchievementsManager*`) is *not* a path to this. It's a C/C++ API compiled into a game, running against an authenticated user inside that game's own process, and it only ever sees the title it's built into — it's how a game reads and writes its own achievements, not how a player reads their profile from outside.

### Output format

Every guide ships as a **single, self-contained interactive HTML checklist** — a real tool you keep open in a browser tab across a full playthrough, not a static writeup:

1. **Header** — live progress bar and count, with expand/collapse/reset controls (and, if you synced, guide progress and achievements-earned shown as two separately labelled numbers, never merged into one)
2. **Search bar** — sticky, filters as you type, and searches *inside* collapsed phases, bundled mission sub-lists, and hidden notes, auto-expanding whatever matches. Since locations and jargon definitions deliberately live in collapsed notes, that's where searching for "bowling alley" or "fireproof" actually pays off. Clearing search restores the expand/collapse state you had, and filtering never touches your progress numbers
3. **Missables box** — pinned up top as plain warnings (never checkboxes), with each missable also flagged inline at the exact point it occurs in the route
4. **Phased route** — the exact order you play in, top to bottom. Collapsible accordion phases with per-phase progress, uneventful mission runs bundled with expandable sub-lists, and expandable notes for context and jargon. Side content nests under the mission that unlocks it *when that's genuinely what you do next* — grouping is presentation and never outranks play order, so anything best done later sits at its real position with a note naming what unlocked it
5. **Time estimate** — story and full 100%, when sources provide one
6. **Footer** — maps, trackers, and known stuck-at-99% culprits

Progress persists across sessions, and every guide gets its own visual identity drawn from the game's setting — the structure stays consistent between games, the look never repeats.

## Installation

### Option A — Claude: install the packaged skill

Download [`xbox-100-percent-guide.skill`](xbox-100-percent-guide.skill) and add it to your Claude skills. The `.skill` file is a ZIP archive containing the skill's `SKILL.md`.

### Option B — Claude Code: use the source directly

Copy the [`xbox-100-percent-guide/`](xbox-100-percent-guide/) folder into your Claude skills directory (typically `~/.claude/skills/`):

```bash
git clone https://github.com/WillyV347/xbox-100-percent-guide.git
cp -r xbox-100-percent-guide/xbox-100-percent-guide ~/.claude/skills/
```

### Option C — any other LLM or agent

The skill is plain markdown. Use the contents of [`SKILL.md`](xbox-100-percent-guide/SKILL.md) as a system prompt, custom instructions (custom GPT, Gemini Gem), or an agent's instruction file, and give the model web-search access so it can do the research steps.

A few implementation details assume Claude's sandboxed artifact environment and should be swapped for your platform's equivalents: the `window.storage` persistence API (in an ordinary browser page, `localStorage` is the right tool — the skill's ban on it applies only inside Claude artifacts, where it's blocked), and the `/mnt/user-data/outputs/` + `create_file`/`present_files` output flow (deliver the HTML file however your platform shares files). Everything else — the research discipline, route ordering, checklist structure, and verification passes — is platform-neutral.

## Usage

Once installed, the skill triggers automatically whenever you name a game plus any completion, achievement, or roadmap intent. For example:

- "How do I 100% GTA: Vice City?"
- "What are the missable achievements in Fallout 3?"
- "Give me an optimal order to do everything in Sleeping Dogs."
- "Best way to play Red Dead Redemption for all achievements."
- "What should I do first in Saints Row?"
- "Sync my Xbox achievements and start the Vice City guide from where I actually am."

The model will research the specific game and produce the full guide.

## Repository layout

```
.
├── README.md
├── LICENSE
├── xbox-100-percent-guide.skill   # packaged skill (ZIP), for direct install in Claude
└── xbox-100-percent-guide/
    └── SKILL.md                   # skill source — usable as a system prompt for any LLM
```

## License

Released under the [MIT License](LICENSE).
