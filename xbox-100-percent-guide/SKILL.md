---
name: xbox-100-percent-guide
description: >
  Generate an optimal 100% completion and all-achievements guide for any Xbox game. Use this skill
  whenever the user names a specific Xbox game and wants to know how to get 100% completion,
  all achievements, a platinum roadmap, or asks "what order should I do everything in." Also
  triggers on phrases like "how do I 100% X", "missable achievements in X", "optimal order for
  X", "completion guide for X", or "what should I do first in X". Always use this skill when
  the request involves a named game plus any completion, achievement, or roadmap intent — even
  if phrased casually like "I want to do everything in X" or "best way to play X for all
  achievements."
---

# Xbox 100% Completion Guide Skill

Generate an optimal, phase-by-phase guide for 100% completing a named Xbox game and unlocking
all achievements. The goal is a route that minimizes backtracking, front-loads upgrades and
power-unlocks that make later content easier, and protects the player from missables.

---

## Step 1: Research the Game

Before writing anything, web-search for current, accurate information. Do not rely on training
data alone — achievement lists, missables, and exploit patching change over time.

Search for:
- Full achievement list with descriptions
- Missable achievements (anything tied to a specific mission, choice, or time window)
- 100% completion requirements (story missions, collectibles, side missions, vehicle missions,
  etc.)
- Known exploits or efficiency tricks (e.g., money/XP glitches, sequence breaks)
- Collectible counts per area/region (exact numbers, not approximations)
- Vehicle missions, minigames, or side content and what they unlock
- Any known bugs, crashes, or platform-specific issues that affect completion

Use at least 2-3 sources (achievement guides, wikis, community guides). Cross-reference counts
and missable details — sources often disagree.

---

## Step 2: Identify Missables First

Before building the route, extract every missable achievement and flag:
- Which mission or story window it occurs in
- Exactly what the player must do (or avoid) to trigger it
- Whether it conflicts with any other achievement (e.g., kill vs. spare choices)

Present missables in a clear table:

| Achievement | Trigger Point | What to Do |
|---|---|---|
| [Name] | [Mission/window] | [Exact required action] |

If any missables conflict with each other (requiring multiple playthroughs), flag this
prominently at the top of the guide.

---

## Step 3: Identify Power-Unlocks

Before building the route, identify upgrades, rewards, or unlocks that make the rest of the
game significantly easier. These should be front-loaded even if they feel like a detour.

Common examples:
- Vehicle missions that unlock infinite sprint, fireproof status, max armor (e.g., Paramedic,
  Firefighter, Vigilante in GTA-style games)
- Collectibles that unlock weapons, vehicles, or abilities at safehouses
- Exploit missions that generate large amounts of money or XP early
- Minigames that unlock permanent stat boosts

These should happen in Phase 1 or Phase 2 of the guide, not after the story.

---

## Step 4: Identify Area-Gated Content

Many open world games lock content behind story progression or map access. Before writing
the route, determine:

- What content is accessible from the start vs. what requires story progress to unlock
- Which collectibles, jumps, rampages, or side missions are physically blocked early
- Which vehicle missions require specific vehicles that only spawn in locked areas

**Do not tell the player to sweep areas they cannot fully access yet.** Only instruct a
collectible or content sweep once the player has full access to that area. If access is
partial, state exactly what is and is not reachable.

For example: "There are X collectibles in this area. You can reach Y of them now on foot.
The remaining Z require a helicopter / story unlock / specific vehicle — come back for those
in Phase N."

This was a key clarification from real use: telling a player to collect all hidden packages
on Island 1 when they are on mission 1 is incorrect — many are physically inaccessible.
Always ground collectible sweeps in what is actually reachable at that point in the route.

---

## Step 5: Build the Phased Route

Structure the guide in clear phases. Each phase should have a single governing logic
(e.g., "before story," "Island 1 accessible content," "post-mainland unlock," etc.).

### Phase structure template:

**PHASE [N] — [Governing logic / what unlocks this phase]**

State what is now available that wasn't before. Then list tasks in the order that makes
the most sense given available content and efficiency.

For each task, include:
- What to do
- Why now (what it unlocks or enables)
- Any critical save points or missable warnings inline

### Ordering principles (apply in priority order):

1. **Missable protection first.** Flag saves before any missable. Never let the player
   reach a missable without a prior warning in the route.
2. **Power-unlocks early.** Any upgrade that helps across the whole game should happen
   in Phase 1 or 2, not after the story.
3. **Area sweeps only when accessible.** Never assign a full area sweep until the player
   has complete access. Partial sweeps are fine — be explicit about what's included.
4. **Minimize backtracking.** Group content by area. If a vehicle or tool is needed for
   multiple tasks, do them together.
5. **Story gating awareness.** Some side content only unlocks after specific story missions.
   Place those tasks in the correct phase, not before the unlock.

---

## Step 6: Terminology and Clarity Standards

Use consistent, plain terms throughout:

- **Name areas explicitly** (e.g., "Vice City Beach / East Island," "Vice City Mainland /
  West Island") rather than shorthand like "Island 1" or "Island 2" without defining them.
  Define any shorthand on first use: "Vice City Beach (the starting island, also called
  Island 1 in some guides)."
- **Define jargon on first use.** Not all players know what "vehicle missions," "rampages,"
  or "stunt jumps" are in a given game. One-line definition on first mention.
- **State collectible counts precisely** — total in area, reachable now, and what blocks
  the rest. Never say "grab all X collectibles" if some are inaccessible.
- **Separate achievements from 100% requirements.** Some achievements are not required
  for 100% completion and vice versa. Be explicit about which category each task falls into.

---

## Step 7: Known Exploits and Bugs

If any relevant exploits or known bugs exist:
- Describe them clearly (what they do, how to execute them)
- State whether they disable achievements (many games flag cheat/exploit use)
- Note any patches that have removed them, and when
- Flag any bugs that can prevent 100% (e.g., crashes during specific missions, collectibles
  that fail to register) and how to mitigate them (save frequency, graphics settings, etc.)

---

## Output Format

Present the guide in this order:

1. **Missables table** — always first, so the player knows what to protect before anything
   else
2. **Power-unlocks summary** — what to do early and why
3. **Phased route** — phase by phase, with missable warnings inline
4. **Time estimate** — story completion and full 100% estimate, if sources provide one
5. **Useful tools** — any recommended maps, trackers, or external resources (e.g., MapGenie,
   GTASnP, interactive checklists)

Keep the guide scannable. Use headers for phases, inline bold for missable warnings, and
tables for missables and collectible counts. Avoid walls of prose.

---

## Key Lessons From Real Use

- Players may be at mission 1 when asking for this guide. Do not front-load the guide with
  content sweeps that require mid-game progress to complete.
- Collectible sweeps should always specify how many are reachable *right now*, not just the
  total count.
- Area names in guides often differ from what players see on the map in-game. Use the
  in-game name first, then note the guide shorthand if needed.
- Vehicle missions (Paramedic, Taxi, Firefighter, etc.) are often skipped by players
  rushing story — but their upgrades (infinite sprint, fireproof, etc.) are significant
  enough to call out explicitly and early.
- Some games have exploit-based money/XP grinds that trivialize later content. These are
  worth flagging even if the player doesn't ask, as they can save significant time.
