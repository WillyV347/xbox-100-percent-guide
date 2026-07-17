# Xbox 100% Completion Guide — LLM Skill

An LLM skill that generates an **optimal, phase-by-phase route to 100% completion and all achievements** for any Xbox game. Works with [Claude](https://claude.com/claude-code) out of the box, and with **any LLM or agent that can follow a markdown instruction file** — a custom GPT, a Gemini Gem, an open-source agent framework, or a plain system prompt.

Point it at a game, and the model researches the current achievement list, flags every missable, front-loads the upgrades that make the rest of the game easier, and lays out a route that minimizes backtracking — grounded in what's actually reachable at each point in the game, not just a raw collectible dump.

## What it does

When you name an Xbox game and ask how to 100% it, the skill drives the model through a disciplined process:

1. **Research the game** — web-searches for the current achievement list, missables (including systemic ones like losable companions or reputations), per-category completion requirements, verified exploit methods, exact collectible counts, and specific locations for location-dependent tasks (never relies on training data alone, since these change over time).
2. **Identify missables first** — extracts every missable achievement with its trigger point and the exact action required, flagging any that conflict (i.e. require multiple playthroughs).
3. **Identify power-unlocks** — surfaces upgrades and rewards (infinite sprint, fireproof status, money/XP exploits, protective perks, etc.) worth front-loading even when they feel like a detour.
4. **Check cross-system interactions** — catches orderings where one task accidentally fights another: redundant grinds, resource requirements backfilled by guaranteed rewards, daily caps, and acquire-vs-use location mismatches.
5. **Identify area-gated content** — determines what's reachable now vs. locked behind story progress, so it never tells you to sweep an area you can't fully access yet.
6. **Build the phased route** — verifies the actual unlock *sequence* against sources, then orders everything by missable protection → power-unlocks → accessible sweeps → minimal backtracking → story gating, with no unordered "do these whenever" buckets and no overlapping checklist items. Audits the final "post-story cleanup" phase item by item so nothing lands there by default — content that isn't genuinely gated late moves to the earliest phase where it's actually reachable, and whatever verifiably stays late says why. Routes whole-game cumulative requirements (e.g. max every weapon) as an early habit with mid-route checkpoints, not an end-game grind.
7. **Enforce clarity standards** — names areas explicitly, defines jargon on first use, states precise collectible counts, separates *achievements* from *100% requirements*, and never invents false precision.
8. **Surface exploits and bugs** — including whether they disable achievements, whether they've been patched, and the known "stuck at 99%" culprits.

### Output format

Every guide ships as a **single, self-contained interactive HTML checklist** — a real tool you keep open in a browser tab across a full playthrough, not a static writeup:

1. **Header** — live progress bar and count, with expand/collapse/reset controls
2. **Missables box** — pinned up top as plain warnings (never checkboxes), with each missable also flagged inline at the exact point it occurs in the route
3. **Phased route** — collapsible accordion phases with per-phase progress, side content nested under the mission that unlocks it, uneventful mission runs bundled with expandable sub-lists, and expandable notes for context and jargon
4. **Time estimate** — story and full 100%, when sources provide one
5. **Footer** — maps, trackers, and known stuck-at-99% culprits

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
