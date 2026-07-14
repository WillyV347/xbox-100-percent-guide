# Xbox 100% Completion Guide — Claude Skill

A [Claude](https://claude.com/claude-code) skill that generates an **optimal, phase-by-phase route to 100% completion and all achievements** for any Xbox game.

Point it at a game, and Claude researches the current achievement list, flags every missable, front-loads the upgrades that make the rest of the game easier, and lays out a route that minimizes backtracking — grounded in what's actually reachable at each point in the game, not just a raw collectible dump.

## What it does

When you name an Xbox game and ask how to 100% it, the skill drives Claude through a disciplined process:

1. **Research the game** — web-searches for the current achievement list, missables, completion requirements, exploits, and exact collectible counts (never relies on training data alone, since these change over time).
2. **Identify missables first** — extracts every missable achievement into a table with its trigger point and the exact action required, flagging any that conflict (i.e. require multiple playthroughs).
3. **Identify power-unlocks** — surfaces upgrades and rewards (infinite sprint, fireproof status, money/XP exploits, etc.) worth front-loading even when they feel like a detour.
4. **Identify area-gated content** — determines what's reachable now vs. locked behind story progress, so it never tells you to sweep an area you can't fully access yet.
5. **Build the phased route** — orders everything by missable protection → power-unlocks → accessible sweeps → minimal backtracking → story gating.
6. **Enforce clarity standards** — names areas explicitly, defines jargon on first use, states precise collectible counts, and separates *achievements* from *100% requirements*.
7. **Surface exploits and bugs** — including whether they disable achievements and whether they've been patched.

### Output format

Every guide is presented in a consistent, scannable order:

1. **Missables table** — always first, so you know what to protect before doing anything
2. **Power-unlocks summary** — what to do early and why
3. **Phased route** — phase by phase, with missable warnings inline
4. **Time estimate** — story and full 100%, when sources provide one
5. **Useful tools** — maps, trackers, and interactive checklists

## Installation

### Option A — install the packaged skill

Download [`xbox-100-percent-guide.skill`](xbox-100-percent-guide.skill) and add it to your Claude skills. The `.skill` file is a ZIP archive containing the skill's `SKILL.md`.

### Option B — use the source directly

Copy the [`xbox-100-percent-guide/`](xbox-100-percent-guide/) folder into your Claude skills directory (for Claude Code, that's typically `~/.claude/skills/`):

```bash
git clone https://github.com/WillyV347/xbox-100-percent-guide.git
cp -r xbox-100-percent-guide/xbox-100-percent-guide ~/.claude/skills/
```

## Usage

Once installed, the skill triggers automatically whenever you name a game plus any completion, achievement, or roadmap intent. For example:

- "How do I 100% GTA: Vice City?"
- "What are the missable achievements in Fallout 3?"
- "Give me an optimal order to do everything in Sleeping Dogs."
- "Best way to play Red Dead Redemption for all achievements."
- "What should I do first in Saints Row?"

Claude will research the specific game and produce the full guide.

## Repository layout

```
.
├── README.md
├── LICENSE
├── xbox-100-percent-guide.skill   # packaged skill (ZIP), for direct install
└── xbox-100-percent-guide/
    └── SKILL.md                   # browsable skill source
```

## License

Released under the [MIT License](LICENSE).
