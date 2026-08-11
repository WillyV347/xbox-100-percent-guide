# Xbox 100% Completion Guide — LLM Skill

An LLM skill that generates an **optimal, phase-by-phase route to 100% completion and all achievements** for any Xbox game. Works with [Claude](https://claude.com/claude-code) out of the box, and with **any LLM or agent that can follow a markdown instruction file** — a custom GPT, a Gemini Gem, an open-source agent framework, or a plain system prompt.

Point it at a game, and the model researches the current achievement list, flags every missable, front-loads the upgrades that make the rest of the game easier, and lays out a route that minimizes backtracking — grounded in what's actually reachable at each point in the game, not just a raw collectible dump.

## What it does

When you name an Xbox game and ask how to 100% it, the skill drives the model through a disciplined process:

1. **Research the game** — web-searches for the current achievement list, missables (including systemic ones like losable companions or reputations), per-category completion requirements, verified exploit methods, exact collectible counts, and specific locations for location-dependent tasks (never relies on training data alone, since these change over time). Crucially it reads the **top-voted solution threads** on TrueAchievements, PowerPyx and PlayStationTrophies.org (whichever cover the game), not just achievement descriptions — descriptions say *what* an achievement needs, solutions say *when to do it*, and that placement advice exists nowhere else. Where the community's recommended placement disagrees with the derived order, the guide resolves the conflict and records the reason rather than silently keeping its own.

   It starts from the TrueAchievements **game walkthrough** (`trueachievements.com/game/<Game-Slug>/walkthrough`), which in a single page gives missable and unobtainable counts to cross-check against its own research, playthroughs required, a section-by-section table of contents carrying ordering advice, and a breakdown tagging every achievement by type. Those tags drive a **triage pass** so token cost stays bounded on big lists: story-tagged achievements have forced placements and get no further research, while Missable, Buggy, Collectable, Time Consuming and Time/Date ones — plus anything placed by inference rather than a verified gate — get their solution thread read. Typically 15-25 of a 60-70 achievement list warrant the deep read, and which ones get recorded so a later pass extends rather than repeats the work.

   Because this is the most search-heavy part of the process, the skill asks for the deepest research surface available before it starts rather than after — on Claude that means prompting you to switch on [Research](https://support.claude.com/en/articles/11088861-use-research-on-claude) (the **+** button, then **Research**), with the trade-off stated: it runs many interconnected searches and returns a cited report in minutes, and it spends usage limits faster. You decide; declining just means more turns. Where no such mode exists — Claude Code, API sessions, other agents — it says so and runs the sweep explicitly instead of letting "researched" imply more than one search bought. Either way the result is treated as a source to cross-check, not a verdict, and its citations get read for the sites this step actually depends on, since a research pass quietly routes around anything it couldn't fetch and looks equally complete either way.
2. **Sync your earned achievements** — optionally pulls your real achievement state for the game from your Xbox profile, so the guide starts from what you already have (see [Syncing your achievements](#syncing-your-achievements) below).
3. **Identify missables first** — extracts every missable achievement with its trigger point and the exact action required, flagging any that conflict (i.e. require multiple playthroughs).
4. **Identify power-unlocks** — surfaces upgrades and rewards (infinite sprint, fireproof status, money/XP exploits, protective perks, etc.) worth front-loading even when they feel like a detour.
5. **Check cross-system interactions** — catches orderings where one task accidentally fights another: redundant grinds, resource requirements backfilled by guaranteed rewards, daily caps, acquire-vs-use location mismatches, and anything that advances on elapsed time rather than player action.
6. **Identify area-gated content** — determines what's reachable now vs. locked behind story progress, so it never tells you to sweep an area you can't fully access yet.
7. **Build the phased route** — verifies the actual unlock *sequence* against sources, then orders everything by missable protection → power-unlocks → accessible sweeps → minimal backtracking → story gating, with no unordered "do these whenever" buckets and no overlapping checklist items. Audits the final "post-story cleanup" phase item by item so nothing lands there by default — content that isn't genuinely gated late moves to the earliest phase where it's reachable *by its best method*, and whatever verifiably stays late says why. Earliest-reachable is a ceiling, not a target: availability is judged on the method rather than the task, since an ungated achievement whose only fast approach needs a late-game region, vehicle, or upgrade isn't really available early — only a worse version of it is. Methods expire as well as unlock — one needing a region still locked, an NPC still alive, or you still low-level gives a task a *window* rather than a start point, and the closing edge gets flagged like a missable even though the achievement itself never becomes unobtainable. Missables and power-unlocks are the standing exceptions and go early regardless. Moving an item away from where a source put it is treated as a claim needing evidence in *both* directions — pushing something later out of caution is asserting a gate nobody found, and it's the move that escapes notice, since placing a task too early fails loudly the moment you try it while placing it too late just costs you a trip you never learn was avoidable. So any override records what the source said, what the guide does instead and why, and whether that reason is verified or assumed — otherwise it disappears into the file within one edit and reads exactly like a researched placement. Routes whole-game cumulative requirements (e.g. max every weapon) as an early habit with mid-route checkpoints, not an end-game grind. Never parks you waiting: anything left *pending* — property income, build timers, a call or message that arrives later, an activity that has to trigger, something gated on a counter of missions rather than on days, a restock, an unlock that lands at the next sign-in — is started at the earliest point it can be and left to resolve underneath real steps, so they overlap instead of queueing into back-to-back "wait a few in-game days" instructions. Each one also records what actually advances it (time alone, progress you're making anyway, or a specific action like sleeping or re-entering an area) and what the arrival looks like, so a pending reward isn't mistaken for a failed step. Where the steps are chained rather than independent — see an NPC, wait days, see them again, wait again — the links get interleaved through the route so the days pass while you're doing other things, each one noting where the previous link was. It also checks that you actually *have control* everywhere it puts work: where one mission runs straight into the next with no player action in between, the gap between them exists in the mission list and not in the game, so nothing gets scheduled there — and since those handoffs routinely move you to a new hub or strip a loadout, anything on the far side of one is re-checked rather than assumed to still be within reach.
8. **Enforce clarity standards** — names areas explicitly, defines jargon on first use, states precise collectible counts, separates *achievements* from *100% requirements*, and never invents false precision. Every item also has to be **executable from its own line**: what you do in the ten seconds after reading it — where you go, what you interact with, and what confirms it worked — has to be answerable from that item alone, or it's incomplete even though nothing in it is false. Items naming a *system* rather than a place (a website, a companion app, an in-game terminal, a storefront, a submenu) get checked twice, since naming the system isn't explaining how to reach it or whether you have to leave the game to do it. And where the confirmation is delayed or invisible — a mailed reward, a stat that only updates on a summary screen, a counter with no in-game tracker — the line says so, because an action that looks like it silently failed gets retried or abandoned.
9. **Surface exploits and bugs** — including whether they disable achievements, whether they've been patched, and the known "stuck at 99%" culprits.
10. **Gate every item as it's written** — a per-item checklist runs on every mission, child row, side activity and achievement task before it's committed to the guide, and again on any item edited later: is it a real to-do, is it in the right place, does the player have control there, can they execute it from that line alone, does it close its prerequisites forward and backward, does every concrete detail trace to a source. The end-of-build verification sweeps still run, but they're file-level — they catch contradictions *between* items, not a single row that quietly skipped a rule.

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

It stays in force after that, too. Follow-up turns about a guide it built — "why is this in Phase 3," "where exactly is that terminal," "I already did X out of order," "add the DLC," "re-sync me," "this theme doesn't look like the game," "this step didn't work" — re-enter the same process rather than being answered from memory of the build: the answer gets researched, it goes *into* the file as well as into the reply (a question you had to ask is a line that failed the executability test), and every verification pass re-runs, since a one-line edit is still an edit round.

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
