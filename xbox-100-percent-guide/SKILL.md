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
  achievements." Also applies when the user asks to turn an existing guide into an interactive
  checklist, or to revise/fix ordering, formatting, or accuracy in a guide already produced by
  this skill.
---

# Xbox 100% Completion Guide Skill

Generate an optimal, phase-by-phase guide for 100% completing a named Xbox game and unlocking
all achievements. The goal is a route that minimizes backtracking, front-loads upgrades and
power-unlocks that make later content easier, protects the player from missables, and — just as
important — produces a checklist where checking items off top to bottom actually tracks real
progress through the game, not a loosely-ordered pile of true facts.

**The deliverable is always an interactive HTML checklist artifact** (checkboxes, persistent
progress, collapsible notes), not a static markdown file or a plain chat response — see Output
Format below.

This skill applies to **any Xbox game** — open-world sandboxes, RPGs, shooters, racers,
platformers, indies, multiplayer titles. Many examples below come from GTA-style open-world
games because that's where the skill was battle-tested, but every principle generalizes: read
"missions" as the game's own progress unit (quests, chapters, levels, races, operations),
"islands" as any gated region or act, and "vehicle missions" as any repeatable side activity
with a permanent reward. Don't skip a step because the game "doesn't have that" — translate
the concept to the game's own systems instead.

---

## Step 1: Research the Game

Before writing anything, web-search for current, accurate information. Do not rely on training
data alone — achievement lists, missables, and exploit patching change over time.

Search for:
- Full achievement list with descriptions
- Missable achievements (anything tied to a specific mission, choice, or time window) — and not
  just story-mission missables. Check whether any long-term systems (relationships, reputations,
  companions) can be permanently lost through ordinary play (a bad interaction, a death, a
  decision) rather than only through a one-time story trigger. These are easy to miss because
  they don't show up in a simple achievement-list search; they surface in mechanic-specific or
  troubleshooting-focused searches instead (see Step 2).
- 100% completion requirements (story missions, collectibles, side missions, vehicle missions,
  etc.) — enumerate every distinct category explicitly, not just the obvious ones. Side-job
  systems are easy to under-count: a game can have half a dozen distinct side-mission businesses
  (e.g., trucking, valet, courier, quarry work) that a completion-percentage source lists but a
  generic achievement-list source doesn't. Cross-check an authoritative "what counts toward 100%"
  breakdown against the achievement list — they are usually different sources, and content that
  matters for one can be totally absent from the other.
- Known exploits or efficiency tricks (e.g., money/XP glitches, sequence breaks) — get the
  specific, verified method (exact target, exact button, exact condition), not a vague
  paraphrase. "Bet on horses" is not a method; "bet on the horse with the [specific marker],
  it has the worst odds, that's the point" is.
- Collectible counts per area/region (exact numbers, not approximations), and what reward each
  collectible category actually grants (cash, weapons, stat unlocks) — this often changes how
  early it's worth prioritizing them.
- Vehicle missions, minigames, or side content and what they unlock
- **Where required vehicles, items, or NPCs actually spawn**, by name of location, not just
  "steal a truck." Community guides frequently get this wrong for small/rural locations
  specifically — a vehicle being conveniently available in the same small town as an unrelated
  side mission is a claim to verify, not assume, and it's worth checking more than one source
  when a location seems suspiciously convenient. Separately verify where the vehicle is best
  *acquired* versus where the mission is best *completed* — see Step 4, they're often different.
- Any known bugs, crashes, or platform-specific issues that affect completion
- Whether any achievement is discontinued or currently unobtainable (server shutdowns, delisted
  DLC, removed events) — for multiplayer/online achievements, also check server population and
  whether boosting is realistically possible. A 100% route that dead-ends on a dead server
  needs to say so up front, not at the end.
- Specific locations for location-dependent tasks (see "Add locations" under Output Format) —
  the exact venue, its neighborhood, and which candidate is best given where the player will be
  at that point in the route

Use at least 2-3 sources (achievement guides, wikis, community guides). Cross-reference counts
and missable details — sources often disagree. When sources genuinely disagree on a specific
number (a threshold, a cap, an exact count) and the disagreement can't be resolved, say so and
give the range or the safer/more conservative figure, rather than picking one source arbitrarily
and stating it as settled fact.

**Verify that a fetch or search actually returned content before treating it as ground truth.**
A tool call that returns empty is not a source, it's a non-result — don't reconstruct plausible-
sounding specifics (mission numbers, exact sequences, precise thresholds) from general knowledge
and present them with the same confidence as a verified fetch. If a numbered sequence can't be
verified against an actual source, present the guide as sequential checklist steps (1, 2, 3…)
instead of claiming to know the game's own internal numbering, and say plainly that the step
numbers are the guide's own, not the game's.

---

## Step 2: Identify Missables First

Before building the route, extract every missable achievement and flag:
- Which mission or story window it occurs in
- Exactly what the player must do (or avoid) to trigger it
- Whether it conflicts with any other achievement (e.g., kill vs. spare choices)
- Whether it's a **systemic** missable rather than a one-time story trigger — e.g., a
  relationship, faction standing, or companion that can be permanently lost through normal play
  (dying, a bad choice, neglect) with no story flag warning the player it's about to happen.
  These deserve the same prominence as story-tied missables, and the guide should state plainly
  what the safe practice is (e.g., "do X before seriously engaging with Y, it neutralizes the
  risk").

Present missables in a clear table, in prose or as a list, up top before any phase content.
**Missables are always plain bullets, never checkbox items**, even in the HTML checklist
build. They're warnings to internalize before you start, not tasks to mark done — the actual
protective action still lives (and gets its own checkbox) inside the specific phase step where
it applies. Duplicating them as checkboxes at the top invites the player to "complete" a
warning instead of reading it.

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
- Companion/relationship perks that reduce the cost of death or failure (e.g., a perk that
  prevents item loss on death or arrest) — worth calling out specifically before the guide's
  most punishing or combat-heavy stretch, not just "whenever you get around to it"
- The same logic in any genre: early traversal or ability unlocks in action-adventures, a
  weapon/gear tier that trivializes a difficulty achievement, an XP/loot multiplier in an RPG,
  or a practice mode that makes a hard minigame achievement cheaper to attempt

These should happen in Phase 1 or Phase 2 of the guide, not after the story.

---

## Step 4: Check Cross-System Interactions

Before finalizing any ordering, actively look for places where two systems interact in a way
that changes what "the right order" means. Don't stop at "is this missable" and "does this
unlock something" — also check:

- **Does grinding stat A accidentally fight against stat B**, or does the guide's own sequencing
  make the player do the same underlying work twice? (E.g., an achievement that maxes a stat the
  hard way right before a piece of equipment that would have done it for free as a side effect.)
  Verify the actual mechanic rather than assuming the intuitive-sounding interaction is real —
  it's easy to assume a cosmetic/physical stat affects a numeric stat it doesn't actually touch.
- **Does an achievement's resource requirement (cash, currency, materials) get satisfied by a
  guaranteed reward elsewhere**, making a separate grind unnecessary? If 100% completion or a
  late-game unlock deposits a specific amount of currency, sequence spending *before* that
  reward and let the reward backfill any "have X amount" requirement, instead of telling the
  player to bank that amount twice.
- **Are there daily/session caps on a grindable stat or activity?** If so, say so, and give the
  standard workaround (often: save at a safehouse/hub to skip an in-game cooldown) instead of
  letting the player assume one long session will finish it.
- **Does the order in which the player acquires protective perks matter** relative to the
  riskiest, most failure-prone stretch of the game? If a perk mitigates death/failure
  consequences, place the acquisition of that perk immediately before the section it protects,
  not as a passing mention somewhere earlier.
- **Is the best place to acquire a required vehicle/item different from the best place to
  actually use it?** Many vehicle-based side missions have a specific location that makes the
  mission itself fastest (low traffic, convenient objective spawns) that is *not* where the
  vehicle spawns. Verify both independently — don't assume the vehicle spawns wherever the
  mission is easiest, and don't assume the guide should be organized around wherever the
  vehicle happens to be available first. Place the task at its best **completion** location in
  the route, and fold the acquisition into that same step as a "go get it from X, bring it
  here" instruction, rather than defaulting to whichever location the vehicle happens to be
  available at earliest. If fetching it is genuinely risky (a fragile or rollover-prone
  vehicle, a long drive through traffic), say so and give the specific hazard to watch for, not
  just "drive it over."

This step is what separates "a list of true facts about the game" from "a list of true facts in
an order that actually helps." When in doubt, ask: if the player does these two things in the
order I've written, does the second one cost more, less, or the same as it would the other way
around? If the answer is "more," the order is wrong.

---

## Step 5: Identify Area-Gated Content

Many open world games lock content behind story progression or map access. Before writing
the route, determine:

- What content is accessible from the start vs. what requires story progress to unlock
- Which collectibles, jumps, rampages, or side missions are physically blocked early
- Which vehicle missions require specific vehicles that only spawn in locked areas
- In non-open-world games, the same check applies to chapter-locked levels, point-of-no-return
  cutoffs, and NG+-only content — "area" is whatever slice of the game can become temporarily
  or permanently unreachable

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

## Step 6: Build the Phased Route

**Before writing the route, do a research pass aimed specifically at the *sequence* — not just
individual facts.** Step 1 verifies that facts (achievement triggers, counts, mechanics) are
accurate; this is a separate check on whether the *order* you're about to present is the
order the game actually unlocks things in. Search for the game's mission list or story
progression specifically (e.g., "[game] mission order," "[game] walkthrough chapter list") and
confirm which mission unlocks which region/vehicle/side-content before asserting it — a chain
of individually-true facts can still describe a false sequence if two of them are reversed.
Only present a specific numbered order once it's confirmed this way; otherwise say so and use
the guide's own sequential step numbers rather than implying you've confirmed the game's actual
internal ordering (see Step 1's fetch-verification note, same principle, applied to sequence
rather than single facts).

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
6. **No unordered buckets.** Never leave a group of tasks as "any order" or "do these
   whenever" by default — that's a decision not to think it through, not a neutral choice.
   Actually reason through what the best order is (money-builders before spending, safe wins
   before risky all-or-nothing ones, low-cost tasks before their prerequisites decay, etc.) and
   commit to it, with a one-line reason. Only leave something genuinely unordered when it
   reflects a real mechanic (e.g., "the game itself randomly assigns these, there's nothing to
   sequence"), and say that explicitly so it reads as a verified fact, not a shrug.
7. **No overlapping checklist items.** If the guide will be checked off item by item (a literal
   checklist, or presented as one), every item must represent a distinct, non-overlapping slice
   of progress. Never write an umbrella item like "play missions 1–28" alongside separate items
   for things that happen *inside* that same range — checking the umbrella item implies the
   whole range is done, which contradicts the separate items still sitting below it unchecked.
   Instead, break the range into consecutive non-overlapping chunks: a single mission gets its
   own line when something is tied to it, and an uneventful stretch between two callouts gets
   one connecting line ("play missions X–Y") that stops exactly where the next callout begins.
   The test: if the player checks every box top to bottom in order, does that sequence match
   how the game is actually played, with nothing skipped and nothing double-counted?
8. **When editing an item, re-check its position, not just its content.** Moving a task's
   *content* to a new phase or reordering its wording doesn't automatically fix its *position*
   in the list. Re-verify where the edited item now sits relative to everything else after any
   edit — an item can be perfectly correct in isolation and still be wrong if it ends up
   referencing a later point in the game than the item above it.
9. **Item granularity: one mission, one row.** An uneventful stretch of missions still gets
   each mission named individually as its own child row under a connecting parent line, never
   crammed into a parenthetical on the parent itself. See the dedicated section below for the
   exact mechanic.

### Bundled missions get their own sub-list, never a parenthetical

This is a specific, easy-to-violate case of the granularity principle above, worth spelling out
on its own because it's the anti-pattern that recurs most often:

**Wrong:** `Play missions 7 through 17 (Nines and AK's, Drive-By, Sweet's Girl, Cesar
Vialpando, Home Invasion, Catalyst, Robbing Uncle Sam, OG Loc, Running Dog, Wrong Side of the
Tracks, Just Business).`

This crams eleven distinct missions into a parenthetical on a single line. The player can only
check off "did the whole stretch" as one lump action, there's no way to track partial progress
through it, and a long parenthetical is harder to scan than a short list.

**Right:** the parent line states only the range (`Play missions 7 through 17.`), and each
mission gets its own child row nested underneath it — `Nines and AK's`, `Drive-By`, `Sweet's
Girl`, and so on, one per line, each its own checkbox. The parent collapses them visually
(collapsed by default with a small toggle to expand), but each is independently checkable.

This applies to every bundle, however short — consistency matters more than saving one toggle
click on a two-mission bundle. It applies even when nothing noteworthy happens in a given
mission — "uneventful" is not a reason to compress missions together into prose. It only stops
applying when a stretch is being described in passing rather than presented as checklist steps
at all (e.g., a note mentioning "the rest of the Y questline" for context, not as its own line
item).

When an item bundling several missions already has other children (e.g., a note attached to
whichever mission unlocks an asset), add the missing mission names as additional children
rather than leaving them out of the sub-list — every mission in the stated range should have
its own row, whether or not it individually has anything special attached to it.

---

## Step 7: Terminology and Clarity Standards

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
- **Don't invent false precision.** If a mission's official in-game number, an exact stat
  threshold, or a precise mechanic detail isn't verified, either verify it before stating it
  or flag the uncertainty in the guide itself. A confident wrong number is worse than an honest
  "sources put this between X and Y."

---

## Step 8: Known Exploits and Bugs

If any relevant exploits or known bugs exist:
- Describe them clearly (what they do, how to execute them, the specific target/condition
  that makes them work)
- State whether they disable achievements (many games flag cheat/exploit use)
- Note any patches that have removed them, and when
- Flag any bugs that can prevent 100% (e.g., crashes during specific missions, collectibles
  that fail to register) and how to mitigate them (save frequency, graphics settings, etc.)
- Flag the common "stuck at 99%"-style culprits specifically — these are usually the same
  handful of overlooked categories every time (one missed property/collectible, a challenge
  whose completion doesn't show in the stats menu, a side-job category the player didn't
  realize existed). List them explicitly rather than a generic "double check everything."

---

## Output Format

**The final guide is always delivered as a single, self-contained interactive HTML checklist
file, not a static markdown document or plain chat response.** Every item gets a checkbox,
progress persists across sessions via the storage API, missables stay pinned and visible, and
phases collapse into an accordion so the player can jump straight to wherever they are. This is
the standard deliverable for this skill, not one option among several — build it this way from
the first draft rather than starting with markdown and converting later. In environments with a
file outputs directory, build it with `create_file` into `/mnt/user-data/outputs/` and share it
with `present_files`. Only skip the HTML build if the person explicitly asks for plain
text/markdown instead.

This is a real, personal tool the player will keep open in a browser tab for 50-200+ hours
across many sessions, checking off one line at a time while actually playing. Every structural
decision below exists to serve that use case. Treat a prior guide built for a different game as
the reference for quality bar and structure (ask if one exists in outputs/uploads before
starting from scratch) — a first draft that looks like a wall of markdown pasted into HTML
divs is not acceptable and will need to be redone.

### Required structure

1. **Header** — game title, a large, prominent overall completion percentage computed live
   from checked/total across every item, and a progress bar that fills as items are checked —
   give the bar some visual character tied to the game's identity (a texture, a shape, a
   motif) rather than a plain rounded rect; this is one of the few places a signature flourish
   earns its place. Plus a small persistent save-status indicator (see Persistence below) and
   controls: Expand all / Collapse all / Reset progress (with a confirm step, never a bare
   `confirm()` dialog — build a two-click arm/confirm on the button itself, since modal dialogs
   can be blocked in sandboxed contexts).
2. **Missables box** — always immediately after the header, before any phase content. A visually
   distinct callout (not just another section) listing every missable with what triggers it and
   the exact action required, including any systemic (non-story) missables. Rendered as plain
   bullets with no checkboxes (see Step 2) — the protective action gets its checkbox inline in
   the phase where it applies. If a game has no true missables (some don't), say so explicitly
   here rather than omitting the box. Each missable may carry a collapsible note (see Content
   depth standard) for the safe-handling explanation, but the warning text itself stays visible
   without expanding anything.
3. **Phases, as collapsible accordions** — one per phase, each showing a live `done/total`
   fraction in its collapsed header so the player can see progress without opening it. First
   (or current, if known) phase open by default, rest collapsed, so the player isn't scrolling
   past phases they've already finished. Power-unlocks fold into the phase where they're
   front-loaded, per Step 3. Phase **titles** are proper title case ("Alderney Unlocked," not
   "Alderney unlocked"); the smaller descriptive sub-caption under the title (e.g. "missions
   52-88") can stay as a plain lowercase caption, matching the reference file.
4. **Time estimate** — story completion and full 100% estimate, if sources provide one.
5. **Footer** — a "Tools" list (map/tracker sites, save-checker sites) and a "Known stuck-at-X%
   culprits" list (the specific things that commonly cause a player to plateau just under 100%,
   e.g. one missed collectible category, a stat that silently fails to register, a cheat that
   was used once and forgot about). Both sections should have real, specific entries, not
   placeholders.

### Item granularity and ordering — this is the part most likely to be gotten wrong

The player checks this off **in the exact order they'll hit it in-game, one line at a time.**
That does not mean "one line per mission":

- **Bundle uneventful missions together — as a parent line with child rows.** A run of
  consecutive story missions that unlock nothing and aren't missable becomes ONE parent line
  ("Play missions 7-17") with each mission as its own checkable child row beneath it, never a
  parenthetical list of names (see the bundling section in Step 6). Only break a mission out
  onto its own top-level line when something is tied to it — it's missable, it unlocks a side
  system, it's a hard area/story gate, or it's otherwise notable. Keep nesting to one level
  deep for readability.
- **Side content nests under the mission that unlocks it, as a child item, not as a sibling
  and not under a separate "Side Content" heading.** A parent line ("Play mission 6 'Drive-Thru'
  (gym unlocks)") gets child lines directly under it for what just opened up. This keeps strict
  play order intact while still grouping logically — the player expands the mission, clears
  what it unlocked, moves to the next. Do not split a phase into "Story missions" / "Side
  content" / "Achievements" sections — that was tried and rejected, it forces the player to
  jump around instead of reading top to bottom.
- **Flag missables twice**: once inline at the exact line where the window opens or closes
  (a short tagged label like "MISSABLE — ...") and once in the top-of-page missables box. The
  inline flag is what actually protects the player in the moment; the box is the heads-up.
- **When something has no specific trigger** (available from the start, no mission gates it),
  say so and place it at the top of the phase/DLC rather than inventing a false trigger point.
  Collectible sweeps that are genuinely background tasks across a whole phase (not a single
  completable moment) get one line noting what's reachable now, with the full dedicated sweep
  placed wherever it actually becomes finishable.
- **A nested "child" reminder must be something to do after its parent, never before.** If a
  warning only makes sense before the parent line happens (e.g. "finish X before this mission
  closes the window"), it is not a child task — put it on the parent item itself, as a note or
  in the visible text, not as a checkbox the player would tick after already passing the point
  it warns about.

### Only checklist items that are actual to-dos — no FYI-only checkboxes

Every checkbox must be something the player *does*. Context, background, and caveats are not
tasks and must never get their own checkbox. Concretely:

- Give every phase/DLC its own `note` field (rendered once, above its item list, not as a
  list item) for anything the player needs to know but doesn't need to check off: "this map is
  fully open from mission 1," "these achievements are profile-wide, no rush," population/server
  notes, etc. A line like "Profile-wide, not save-bound, no rush to do this during the story
  route" is a note, never a checkbox.
- Item-level asides work the same way through the existing note-toggle mechanism — if a
  sentence is explaining rather than instructing, it belongs in a note, not as a sibling
  checkbox next to the real task.
- Test for every candidate line: "what does checking this box represent the player having
  *done*?" If the honest answer is "nothing, it's just context," it doesn't get a checkbox.

### Explain thoroughly, in as few words as possible

A short line is good; a short line that assumes knowledge the player doesn't have is not. Don't
ship a bare achievement name and a fragment ("Cut Your Teeth — one rank promotion") without
making sure a first-time player would know what to actually do — what "rank" means here, how
it's earned, where. Prefer: keep the visible line as short as the reference file's style, but
back every non-obvious one with a note that answers "what do I actually do, in plain terms" in
one or two sentences. This applies especially to multiplayer achievements, minigames, and
anything named after in-game jargon.

### Add locations whenever they're needed or would help

If a task happens at a specific place (a shop, a landmark, a district), name it — "Homebrew
Café, Beechwood City" beats "any internet café." When more than one valid location exists,
don't just name one arbitrarily: work out and recommend the *best* one — closest to wherever
the player will actually be at that point in the route (their current safehouse, the mission
they just finished, an area they're already passing through), or otherwise the most convenient
(everything in one stop, open earliest, cheapest). "Any bar with a pool table" is a cop-out if
research can turn up the specific bar, its neighborhood, and why it's the right pick right now.
Look this up during research (Step 1) — don't leave it vague, and don't assume two different
activities share a location just because they're the same "type" of venue; verify each one.

### Content depth standard

Match the depth of a well-run community wiki, not a bare task list. For every item, prefer
including (via an expandable note, see below, so the main line stays scannable):

- Exact locations, spawn points, or landmarks when it saves the player a search
- The *reason* for a sequencing choice when it isn't obvious ("do X before Y because Z")
- Known bugs, disambiguation between conflicting community sources, and common failure modes
- Efficient techniques/exploits worth calling out explicitly

Use a small expandable "(i)" note toggle on any line that needs this extra detail or a
plain-English definition of jargon (assume the player may be new to this game — define terms
like "vigilante missions" or "triathlons" on first use via this same mechanism). The visible
line stays short; depth lives one tap away. Nothing the player actually needs to *not miss*
gets hidden behind a collapsed note — only context and reasoning does. The test: if you deleted
every note, would the player still be able to complete everything correctly, just without
knowing why? If not, something that belongs on the visible line got buried in a note.

### Visual design

Give the file a distinct visual identity tied to the game's own setting and tone — a real color
palette and font pairing (Google Fonts are fine), not a generic default dashboard look. This
should read as a made-for-this-game reference tool, the kind of thing a fan site would build,
not a templated to-do list. Pick a signature visual element tied to the game (a texture, a
recurring shape, a stat-screen convention the game itself uses) and build the palette and type
choices around it. **Never reuse a previous game's exact palette/font pairing for a new
game** — the per-game visual identity is a deliberate, permanent feature of these guides, not
an incidental style choice. Reuse the *structure* (accordion phases, missables box, nested
children, footer) across every game; vary the *look* every time.

### Persistence — read this before writing any storage code

`window.storage` (get/set/delete/list) is the only persistence mechanism available in this
environment and it does work here — **never use `localStorage` or `sessionStorage`, they are
not supported and will silently fail or be blocked.** `window.storage` calls can still fail
transiently (an "Internal server error" is a real but usually transient failure, not a sign the
API is unavailable), so:

- Combine all checklist state into one JSON blob under one key (e.g. `gamename-progress`) and
  rewrite the whole blob on each change, rather than one storage call per item — per-item keys
  multiply the number of storage calls for no benefit and make rate-limiting more likely.
- **Debounce/queue writes.** If a save is already in flight when another change comes in, queue
  it rather than firing a second overlapping write — concurrent writes to the same key are a
  plausible cause of intermittent storage errors, not just bad luck.
- Wrap every `save()` in a retry loop (2-3 attempts with a short backoff, e.g. 600ms *
  attempt number) before giving up.
- Show real status text next to the reset control: "Saving…" while in flight, "Saved" briefly
  on success, "Could not save, will retry on your next check" on exhausted retries. Never just
  swallow the error silently — a console.error the player will never see is not a fallback, it
  just hides the failure from the one person who could notice it.
- On load, a failed/missing read is the **expected, normal state for a first-time user** — treat
  it as "no saved progress yet," not an error to surface.

### Validate the code before presenting

**Validate generated JS syntax before presenting the file**, especially after any edit to
the checklist's text content. The most common self-inflicted bug in hand-authored item text
is an unescaped apostrophe inside a single-quoted string ("you're", "don't", "wasn't"),
which silently breaks the entire script. Run a syntax check (e.g., `node --check`) after
writing or editing the data, not just after the first draft.

### Before presenting: walk it like a player, not a writer

Once the guide is built, this is the last gate, after everything above, before showing it to
the person. Re-read it start to finish as if actually playing, one line at a time, checking:

- Does the sequence of checkboxes match how the game is actually played, with nothing skipped
  and nothing implied twice (the overlapping-items test from Step 6, principle 7)?
- Does every location, vehicle, or target named on a checkbox line actually exist where the
  guide says it does (the location-research requirement from Step 1)?
- Does anything referencing a later point in the game appear before something referencing an
  earlier one (the position-desync check from Step 6, principle 8)?
- Would a player who has never seen this game get stuck or confused by any single line without
  opening its note? Does a "child" item actually belong after its parent? Is anything a bare
  FYI wearing a checkbox?

This pass is not optional and not the same thing as validating JS syntax — syntax validation
confirms the file runs, this pass confirms the file is *right*. Do both. Fix what you find, and
only present the guide after this pass, not before it.

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
- A tool call that returns no content is not the same as a tool call that confirms something
  is absent. Treat a silent/empty fetch as "unverified," not as license to fill the gap with a
  plausible-sounding invented detail (a mission number, an exact sequence) stated with full
  confidence. When this happened in practice, it required a full re-verification pass and a
  correction to the player after the fact — cheaper to verify once than to correct twice.
- Ask "does checking these boxes in order match how the game is actually played" as a final
  pass over any checklist-formatted guide, independent of whether each individual fact in it is
  true. A guide can be 100% factually accurate and still be structurally wrong if its checkable
  units overlap or its groupings default to "any order" instead of a reasoned sequence.
- Systemic missables (a relationship, reputation, or companion that can be permanently lost
  through ordinary play rather than a single story trigger) are easy to miss on a first research
  pass because they don't show up in a plain achievement-list search — they surface in
  mechanic-specific or "can I lose X" style searches. Do a dedicated pass for these, don't
  assume the achievement list search caught everything missable.
- A real bug from practice: an item was rewritten to fix its wording, but its position in the
  list wasn't rechecked, and it ended up sitting right after an item referencing a much later
  mission (an "at mission 22" line immediately followed by a "complete mission 1" line).
  Content and position are two different things to verify; fixing one doesn't fix the other.
- The deliverable is the interactive HTML checklist described in Output Format above, not a
  markdown writeup. A markdown file (or an HTML file that's just markdown-shaped prose in
  divs) is the wrong artifact even if the content inside it is accurate, and will need a full
  rebuild — get the format right on the first pass. The reference bar is a prior guide for
  another game if one exists in outputs/uploads, check before starting from scratch.
- Splitting a phase into separate "Story Missions" / "Side Content" / "Achievements"
  sub-sections was tried and explicitly rejected by a player: it breaks the one-line-at-a-time
  play-order experience. Nest side content as children of the mission that unlocks it instead.
- A missables table alone isn't enough — the player also needs the missable flagged inline at
  the exact point it occurs in the phase list, not just summarized at the top.
- Every story mission belongs in the checklist (bundled where uneventful, broken out where
  notable) — a guide that only tracks achievements and skips the story missions themselves is
  incomplete, even though achievements were the original ask.
- `window.storage` is the only working persistence layer here; reaching for `localStorage` as
  a "fix" when a save error appears is the wrong move; the file was already using it correctly
  and the real gap was missing retry/backoff and swallowing the error instead of surfacing it
  or degrading gracefully.
- Matching a prior game's *structure* does not mean matching its *look* — a player explicitly
  wants a different visual theme per game while the underlying format (accordion, missables
  box, nesting, footer) stays consistent. Don't collapse those two things together.
- A bundled mission line ("Play missions 2-10") still needs every mission individually
  checkable — as a collapsed nested sub-list under that line, not as names crammed into a
  parenthetical on the summary line itself.
- Phase titles need real title case ("Alderney Unlocked"), not sentence case — small detail,
  easy to get wrong by treating the title field like the descriptive sub-caption beneath it.
- FYI/context lines snuck in as checkboxes repeatedly (multiplayer's intro paragraph, "this
  whole map is open from mission 1" for each DLC) because there was nowhere else to put them —
  the fix was adding a real phase-level `note` field rendered above the item list, not a
  reminder to "try harder" at spotting these. Structure the data model so non-actionable
  content has a home that isn't a checkbox.
- A terse achievement line ("Cut Your Teeth — one rank promotion") can be simultaneously short
  and unclear if the player doesn't already know the game's systems. Short main line, note for
  the actual explanation, every time something isn't self-evident.
- Locations get missed by default unless specifically checked for during research — police
  computer access (needs a law enforcement vehicle, not "any police station"), bowling alley
  name, bar name for darts/pool, golf course name, cage fighting arena location all had to be
  added on a later pass. Look them up in Step 1, don't wait to be asked.
- The player-simulation pass caught a real logic bug: a reminder ("finish X before this closes")
  had been nested as a child of the mission that closes the window, so reading top-to-bottom the
  player would hit the reminder *after* it stopped being useful. A child item must always make
  sense as a thing to do after its parent; a "do this first" warning belongs on the parent
  itself, not as a child beneath it. This is exactly the class of bug the mandatory walk-through
  pass exists to catch — do the pass for real, don't skip to presenting.
- When a person says "re-read the skill" after a complaint, check whether the complaint is
  actually covered by the skill text (missables table, story missions, output format all are)
  before assuming it's a net-new gap — but also be honest when something genuinely isn't in the
  skill yet (like first-time-player jargon notes were not, explicitly, until this revision)
  rather than implying it was there all along.
- Don't assume two activities of the same "type" share a venue — pool and darts both happen at
  bars in GTA IV, but pool is only at Homebrew Café while darts is at a completely different
  location (Steinway Beer Garden); they got wrongly bundled as "any bar has both" until checked
  individually. Verify each activity's location separately, even when it seems like they'd
  naturally be in the same place.
- "Any bar" and "any police station" both slipped through even after the locations rule was
  added, because a plausible-sounding generic wasn't checked against whether a specific best
  answer existed. The fix that stuck: for every location-dependent item, explicitly work out
  what's closest to where the player actually is at that point in the route (e.g. the bowling
  alley that happens to border the starting apartment), not just "a valid one somewhere."
- Vehicle or item spawn locations reported by community guides can be wrong or inconsistent,
  especially for small or rural in-game locations. A vehicle being conveniently available in
  the same small town as an unrelated task is a claim to verify against more than one source,
  not an assumption to build a route around (a fire truck turned out not to exist in a town
  where multiple guides implied it did, only the ambulance was actually there).
- When the best place to *acquire* something differs from the best place to *use* it, name
  both locations explicitly and place the task at the completion site with a "get it from X,
  bring it to Y" instruction, rather than collapsing them into a single location for tidiness.
- Money-generating exploits belong first among a cluster of related tasks, not just documented
  somewhere in the guide, so the cash they produce is actually available for whatever spending
  comes later in that same cluster.
- All-or-nothing or high-risk achievements (max-bet gambles, one-shot bets) belong last in a
  cluster of similar tasks, done only after safer wins have built a cushion — not first.
- Side-content categories can hide inside a mission's unlock description ("also unlocks Freight
  Train") without ever becoming their own actionable checklist line. Audit unlock descriptions
  specifically for nouns that never received their own bullet anywhere in the guide.
- A side-content "category" can have more real instances than a first pass assumes (three gym
  trainers across three cities in one game, not the one most guides lead with). When a source
  describes something as a category or a set, confirm the actual count before assuming one
  instance covers it.
- Daily or session caps on a grindable stat need their reset mechanism named explicitly (e.g.,
  "save at a hub twice to skip the cooldown"), not just flagged as existing.
- If a stat-interaction concern turns out to be based on a mechanic that isn't real (a physical
  stat assumed to affect a numeric one it doesn't actually touch), correct the misconception
  explicitly in the guide rather than just quietly adjusting the recommended order — otherwise
  the guide implies a false mechanic even while giving correct advice.
- A guaranteed late-game reward (a fixed cash grant on hitting 100%, for example) can satisfy
  an earlier achievement's resource requirement. Sequence spending before that reward lands and
  let it backfill the requirement, instead of telling the player to accumulate the same amount
  twice.
- "I already did X out of the recommended order" from the player is not a mistake to smooth
  over, it's a cue to check whether that order was a hard requirement or just the suggested
  path, and to give a concrete next step from wherever the player actually is right now.
- Editing a skill file directly inside a sandboxed session is not the same as it being saved to
  the user's actual profile. Only a packaged `.skill` file, installed through the client's own
  "Save skill" action, persists across sessions — a direct file edit only updates the copy
  mounted for the current session. When a user questions whether an update "took," this
  distinction is the first thing to check, before re-asserting that a file looks correct.
- When a user provides a concrete, itemized list of what should have changed, verify it
  claim-by-claim (grep, line count, diff) rather than responding with general reassurance.
  "I checked and it's fine" is much weaker than showing the actual count, checksum, or line
  that proves (or disproves) each specific claim — and weaker reassurance repeated twice is
  not the same as escalating the rigor of the check.
- Re-verifying a prior conclusion with the same shallow method (a keyword grep, a quick
  skim) a second time is not a stronger signal than checking it once properly. When a player
  pushes back more than once on the same claim, escalate the rigor of the check itself (full
  read, checksum, exact count) rather than repeating the same spot-check and getting the same
  answer.
- The lessons above skew toward GTA-style open-world games because that's where this skill was
  battle-tested. Don't let that narrow the skill's scope: for each new game, translate the
  concepts (missions → quests/chapters/races, islands → gated acts, vehicle missions →
  repeatable side activities with permanent rewards) instead of pattern-matching for
  GTA-specific structures and concluding a step doesn't apply.
