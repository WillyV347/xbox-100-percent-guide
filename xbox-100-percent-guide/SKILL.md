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
  this skill. Also triggers on requests to sync, import, or check the player's existing Xbox
  achievements against a guide — "sync my achievements," "what do I already have," "update my
  progress from my Xbox profile," "start the guide from where I actually am."
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
  troubleshooting-focused searches instead (see Step 3).
- 100% completion requirements (story missions, collectibles, side missions, vehicle missions,
  etc.) — enumerate every distinct category explicitly, not just the obvious ones. Side-job
  systems are easy to under-count: a game can have half a dozen distinct side-mission businesses
  (e.g., trucking, valet, courier, quarry work) that a completion-percentage source lists but a
  generic achievement-list source doesn't. Cross-check an authoritative "what counts toward 100%"
  breakdown against the achievement list — they are usually different sources, and content that
  matters for one can be totally absent from the other.
- Cumulative, whole-game requirements — anything satisfied by *how the player plays* over
  dozens of hours rather than by a task at one point in the route: max proficiency/level with
  every weapon, total distance or usage counts, per-category kill totals, skill mastery bars.
  These must be identified up front, because the cheap way to satisfy them is a habit adopted
  from hour one ("once a weapon hits max level, switch to another and keep rotating") and the
  expensive way is discovering them at the end and grinding. See Step 7 for how the guide
  routes these.
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
  *acquired* versus where the mission is best *completed* — see Step 5, they're often different.
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

## Step 2: Sync the Player's Earned Achievements

Before building the route, offer to pull the player's *actual* achievement state for this game
from their Xbox profile, so the guide starts from what they already have instead of assuming a
fresh save. Offer it — never require it, and never block the guide on it. A player who declines,
or whose sync fails, still gets the full guide; it just starts unsynced.

A sync changes the guide in four concrete ways, which is the reason to do it at all:

- **Earned achievements start checked** and visually marked as already banked, so the player
  isn't re-reading tasks they finished two years ago.
- **Missable warnings the player already satisfied stop shouting.** An already-earned missable
  is no longer a risk and should read as resolved rather than as a live warning. The inverse
  case — an unearned missable whose window has already closed — is the loudest thing in the
  guide; see "when the sync says a window already closed" below.
- **The route opens where the player actually is.** Unlock timestamps plus which story
  achievements are already earned locate them in the game; the phase they're in opens by
  default instead of Phase 1.
- **Skipped power-unlocks get re-evaluated.** A player 40 missions deep who never did the
  front-loaded upgrades from Phase 1 needs to know which are still worth a detour now and which
  have been overtaken by their progress — a different answer from "do these first."

### What a sync can and cannot tell you

**Xbox achievements are profile-wide and permanent; in-game 100% completion is save-bound.**
These are two different progress tracks, and conflating them is the fastest way to produce a
confidently wrong guide. An achievement earned on an earlier save, a different console, or years
ago is banked forever and never needs doing again — but the *content behind it* may still be
unfinished on the save the player is actually on, and it still counts toward that save's 100%
stat. Therefore:

- Sync results may pre-check **achievement items**. They must never auto-check a **story
  mission, a collectible sweep, or a 100%-completion task** on the strength of an achievement
  alone.
- Where an achievement is banked but the underlying content still matters for save-bound 100%,
  leave the task checkable and say so in its note: "achievement already on your profile — you
  still need this on your current save for the 100% stat."
- If the synced data obviously describes a different playthrough (unlock dates years apart, or
  late-game achievements with none of the early ones), say so plainly and ask whether this is a
  fresh save before pre-checking anything.

Where the service returns **progression** data rather than just earned/not-earned, use it — a
partially-progressed collectible achievement gives an exact "you have 37 of 100" the checklist
can state outright, instead of making the player recount from scratch.

### How to sync — in preference order

Ask which path the player wants; don't pick one silently. **In every path the player
authenticates themselves — never ask for, type, or store their Microsoft account password.**

1. **A personal Xbox API key (simplest, no password ever involved).** The player creates their
   own key at a third-party Xbox Live API service — OpenXBL (`xbl.io`) is the common one, free
   tier 150 requests/hour at time of writing — and hands you the key. Every request carries an
   `x-authorization: <key>` header; responses carry `X-RateLimit-Remaining`, and a 429 means the
   hourly cap is hit. The paths below are from OpenXBL's own OpenAPI spec
   (`github.com/OpenXBL/Docs`), which is the thing to re-check if any of them 404 — a wrong path
   is indistinguishable from "this player has earned nothing":

   | Call | Purpose |
   | --- | --- |
   | `GET /api/v2/account` | The key owner's own gamertag, XUID, gamerscore — always start here |
   | `GET /api/v2/player/titleHistory` | Games the player has actually launched, with title IDs — resolve the game from this, never from a guessed title ID |
   | `GET /api/v2/achievements/player/{xuid}/title/{titleId}` | Per-title achievement list, **Xbox One/Series titles** |
   | `GET /api/v2/achievements/x360/{xuid}/title/{titleId}` | Per-title achievement list, **Xbox 360 titles** — a separate path, see the generation gotcha below |
   | `GET /api/v2/achievements/stats/{titleId}` | The player's stats for a title, where progression numbers live |
   | `GET /api/v2/achievements/title/{titleId}/{continuationToken}` | Paging, when a title's list is long enough to be truncated |

   Base URL `https://xbl.io` (`https://api.xbl.io` also serves the same `/api/v2/` routes).
2. **The official Xbox Live REST endpoint**, if the player has or wants to set up an XSTS token:
   `GET https://achievements.xboxlive.com/users/xuid({xuid})/achievements`, with
   `Authorization: XBL3.0 x=<userhash>;<xsts-token>` and `x-xbl-contract-version: 2`, filtered
   by the `titleId` query parameter (`unlockedOnly`, `orderBy=UnlockTime`, and paging parameters
   are also supported). It only ever returns the caller's own achievements — the XUID must match
   the authenticated user or the service returns 403. Obtaining the XSTS token means running the
   Microsoft-account OAuth chain, in practice via a tool like `xbox-webapi-python` plus an Azure
   AD app registration the player creates themselves ("Personal Microsoft accounts only,"
   redirect URI `http://localhost/auth/callback`). The player runs the sign-in; you never see
   the password.
3. **A signed-in browser session**, when browser automation is available and the player is
   already signed in to their Xbox account — read the game's achievement list off their own
   profile page. The player does the signing in. Do not type credentials into the page, and do
   not follow a sign-in link that came from anywhere other than the player.
4. **Manual, always available as a fallback:** screenshots of the in-game or console achievement
   list, a pasted list of earned achievement names, or a public TrueAchievements / Xbox profile
   the player links. Slower, zero setup, and it works when every API path is blocked.

**The GDK Achievements Manager (`XblAchievementsManager*`) is not one of these paths**, despite
being the first thing an achievements search surfaces. It is an in-title C/C++ API compiled into
a GDK game, operating on an authenticated `XUser` inside that game's own process, and it only
ever sees the achievements of *the title it is built into*. It is the API a game uses to read
and update its own achievements — not a way for a player or a tool to read a profile from
outside. Same for the rest of XSAPI's in-title surface. If a player links that documentation,
say why it doesn't apply and offer the paths above instead.

### Sync gotchas that produce silently wrong guides

- **Xbox 360-era titles and Xbox One/Series titles sit behind different achievement endpoints
  with different schemas** — on OpenXBL, literally `.../achievements/x360/{xuid}/title/{titleId}`
  versus `.../achievements/player/{xuid}/title/{titleId}`. A 360-era game — the back catalogue
  this skill gets asked about most — queried against the modern endpoint comes back empty, which
  reads exactly like "this player has earned nothing." Match the endpoint family to the title's
  generation, and if a result is empty, try the other family before believing it. Backward-
  compatible titles played on a modern console are the genuinely ambiguous case: check both.
- **An empty or failed sync is not "zero achievements earned."** Same rule as Step 1's
  fetch-verification note, applied to the player's own data: a non-result is unverified, not a
  verified zero. Never pre-check or pre-*un*check anything on the strength of a call that didn't
  clearly succeed — say the sync failed, and build the guide unsynced.
- **Resolve the title from the player's own title history, not from a guessed title ID.**
  Remasters, regional SKUs, and definitive/complete editions are separate titles with separate
  achievement lists; the one sitting in the player's history is the one they're actually playing.
- **Never write the API key, XSTS token, or XUID into the generated HTML file.** The guide is a
  file the player may share, and it's generated once rather than calling any service live — bake
  the *results* in as data, never the credential that fetched them. Treat the achievement data
  itself as the player's personal data: use it for this guide, don't send it anywhere else.

### When the sync says a window already closed

If the sync shows a missable achievement unearned *and* the player is already past the point
where it was obtainable, that is the single most important fact in the guide and it goes at the
top, above the missables box, stated plainly. Then research the actual remedy for that specific
achievement rather than defaulting to "start over": some are recoverable in New Game+, in a
chapter/mission replay mode, or from an earlier manual save; some are genuinely gone for this
save file. Give the specific answer, and if it is "a second playthrough," say what a cleanup run
would need to cover so the player can judge the cost.

### Re-syncing later

The player lives in this file for 50-200 hours, so a sync is not a one-time event. When they
come back and ask to re-sync, re-run it and **merge, never overwrite**: anything the player
checked by hand stays checked even if it isn't in the synced set (they may have done the work
before the achievement popped, or the item may be a 100%-stat task with no achievement attached
at all). A sync can only *add* checks and update progress counts — it never unchecks. Then say
what changed ("8 new since your last sync, you're now in Phase 4") instead of silently rewriting
their file.

---

## Step 3: Identify Missables First

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

## Step 4: Identify Power-Unlocks

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

## Step 5: Check Cross-System Interactions

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

## Step 6: Identify Area-Gated Content

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

## Step 7: Build the Phased Route

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
10. **Every deferral must land somewhere.** Any time an item's own text defers part of the
    task to later ("the last 2 need X access," "a few won't count until region Y opens,"
    "save it for later," "the rest later"), the guide must contain an actual completion step
    in the correct later phase — a real checkbox that sends the player back to finish the
    deferred remainder. The deferring line acknowledges the split; only the later step closes
    it. Stating the deferral without adding the follow-up step is one of the easiest ways a
    guide silently drops content: the task *reads* as handled, but no line anywhere actually
    completes it. When writing any deferral, add the matching later step in the same editing
    pass — don't trust a future pass to remember. (The pre-presentation sweep in Output
    Format exists to catch the ones that slip through anyway.)
11. **The cleanup phase must be earned, item by item.** A final "post-story cleanup" phase is
    only for content that verifiably must (or measurably best) happens late. It is not the
    default home for anything lacking an obvious story trigger — see the dedicated audit
    section below.
12. **Ongoing whole-game requirements are routed as a habit, not an end-phase task.** State
    the behavior early, checkpoint it mid-route, verify it at the end — see the dedicated
    section below.

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

### Audit the cleanup phase — nothing lands there by default

Guides built with this skill tend to end with a "post-story cleanup" phase that catches
whatever isn't tied to a specific story mission. The phase itself is legitimate — but it has a
gravity problem: side content ends up dumped there *by default*, not because anything gates it
late, but because it's easier to lump anything without an obvious story trigger into the
catch-all than to research where it's actually reachable. In practice much of that content is
available from very early in the game, or unlocks at a specific earlier point, and belongs in
that phase instead.

**For every item in the cleanup phase, verify via research when it actually becomes
available** — the same evidence standard as any other fact in the guide, not an assumption in
either direction. Then:

- **If nothing forces it late**, move it to the earliest phase where it's actually reachable
  (earliest-reachable is the ceiling; the other ordering principles — grouping by area,
  money-before-spending, and so on — still decide the exact placement within that window). The
  cleanup phase keeps only a one-line verification for it ("done in Phase X if you followed
  along"), never a line presenting it as new work.
- **If a real mechanical reason keeps it late or bundled, leave it — and state the reason
  explicitly** in the item or its note, so the placement reads as a verified decision rather
  than a thing nobody checked. Real reasons include: an achievement that requires several
  sub-parts completed in one sitting or one session; a fixed reward that another achievement's
  resource requirement depends on (see Step 5); content genuinely only reachable near or after
  the end of the story.

Both failure modes are the same underlying bug — unresearched placement. "Spread everything
out" is exactly as capable of being wrong as "dump everything at the end"; the audit is
per-item research, and moving an item without checking is just as lazy as leaving it without
checking. Watch especially for repeatable side activities (minigames, races, fares/courier-type
jobs): some are story-gated and fine to leave late, but others have no gate at all or unlock
simply by reaching a place the player passes through early — those must never sit in the
cleanup phase as a vague "you'll also need to do this eventually."

### Ongoing whole-game requirements: state the habit early, verify late

Some requirements are satisfied by *how the player plays for the whole game*, not by a task at
a point in the route — max level/proficiency with every weapon, cumulative distance or usage
totals, per-weapon kill counts, skill mastery bars (identified during Step 1 research). These
get a three-part treatment:

- **Introduce the habit in Phase 1 as its own visible item**: what the requirement is and the
  concrete in-flow behavior that satisfies it for free — e.g., "all weapons must reach max
  level for 100%: once a weapon maxes, switch to another and keep rotating; don't keep using a
  maxed weapon out of comfort." Naming the requirement without naming the behavior is what
  produces the end-game grind.
- **Checkpoint it at natural milestones** (phase boundaries work well): "by the end of this
  phase you should have roughly N of M weapons maxed — if you're behind, rotate more
  aggressively." Checkpoints go in phase notes or a short item, so drift is caught mid-game
  rather than discovered at the end.
- **The end-phase line is a verification plus a targeted top-up, never the task itself**:
  "check the stats page; for any weapon still short, grind it now at [specific efficient
  spot]." If the habit was followed, this line costs minutes. The guide must never present the
  whole requirement as end-phase work.

---

## Step 8: Terminology and Clarity Standards

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

## Step 9: Known Exploits and Bugs

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
2. **Search bar** — sticky/pinned so it stays reachable while scrolling, since the document runs
   to hundreds of items. Filters the checklist live as the player types. This is a load-bearing
   feature, not a nicety — see the dedicated section below for the mechanics, which are easy to
   get wrong in a way that makes search look functional while finding nothing.
3. **Missables box** — always immediately after the header, before any phase content. A visually
   distinct callout (not just another section) listing every missable with what triggers it and
   the exact action required, including any systemic (non-story) missables. Rendered as plain
   bullets with no checkboxes (see Step 3) — the protective action gets its checkbox inline in
   the phase where it applies. If a game has no true missables (some don't), say so explicitly
   here rather than omitting the box. Each missable may carry a collapsible note (see Content
   depth standard) for the safe-handling explanation, but the warning text itself stays visible
   without expanding anything.
4. **Phases, as collapsible accordions** — one per phase, each showing a live `done/total`
   fraction in its collapsed header so the player can see progress without opening it. First
   (or current, if known) phase open by default, rest collapsed, so the player isn't scrolling
   past phases they've already finished. Power-unlocks fold into the phase where they're
   front-loaded, per Step 4. Phase **titles** are proper title case ("Alderney Unlocked," not
   "Alderney unlocked"); the smaller descriptive sub-caption under the title (e.g. "missions
   52-88") can stay as a plain lowercase caption, matching the reference file.
5. **Time estimate** — story completion and full 100% estimate, if sources provide one.
6. **Footer** — a "Tools" list (map/tracker sites, save-checker sites) and a "Known stuck-at-X%
   culprits" list (the specific things that commonly cause a player to plateau just under 100%,
   e.g. one missed collectible category, a stat that silently fails to register, a cheat that
   was used once and forgot about). Both sections should have real, specific entries, not
   placeholders.

### The search bar — most of its work happens inside collapsed content

A finished guide is several hundred items long and, by design, **mostly collapsed**: phases are
accordions, bundled missions hide in sub-lists, and every location, jargon definition, and
sequencing reason lives in a collapsed note. That structure is what makes the file scannable —
and it's exactly what makes search non-trivial, because **the naive implementation searches only
what's currently on screen and therefore finds almost nothing.** A search box that returns "no
matches" for a term that's demonstrably in the file is worse than no search box; the player
concludes the content isn't there.

So:

- **Search the full dataset, not the rendered DOM.** Match against every item's visible text
  *and* its note text, plus phase titles, phase notes, and the missables box. Notes are the
  highest-value target: when a player searches "bowling alley," "fireproof," or "ambulance,"
  the answer is usually a location or definition the skill deliberately tucked into a note.
- **Reveal matches automatically.** A hit inside a collapsed phase opens that phase; a hit inside
  a bundled mission sub-list opens the parent; a hit inside a note expands (or at minimum flags)
  that note. Filtering without auto-expanding is the same bug as not searching notes at all.
- **Keep matches in context.** A lone child row reading "Drive-By" tells the player nothing.
  Show the ancestor chain — phase, then parent item, then the matching row — so every result is
  locatable in the route.
- **Highlight the matched substring** in the results, case-insensitively.
- **Show a live match count** ("14 matches"), and a real empty state naming the term ("No matches
  for 'stunt jump'") rather than a blank list.
- **Clearing search restores the player's previous expand/collapse state**, not everything-open
  and not everything-closed. Snapshot the state when a search begins, restore it on clear. A
  player working in Phase 4 who searches for something and clears should land back in Phase 4.
- **Escape clears; a `/` or Ctrl/Cmd-K shortcut focuses the box.** Include a visible clear (×)
  button too — not every player will guess the keyboard path.

### Search is a view, never a mutation

Filtering must not touch progress state in any way: no checkbox changes, nothing written to the
storage blob, no altered totals. The header percentage keeps reporting whole-guide progress while
a filter is active — a progress bar that appears to leap to 100% because the player filtered down
to three completed items is alarming and wrong. Per-phase `done/total` fractions likewise stay
absolute. If it's useful to show how much of the *filtered set* is done, label it separately and
unmistakably ("3/14 shown"), never by repurposing the real numbers.

The same view-state machinery makes a small set of filter toggles nearly free, and they pair
naturally with search: **Hide completed** (the single most useful one late in a playthrough,
when most of the file is checked off), and — when Step 2 produced a sync — **Hide already
earned**. Both are optional; if included, they follow every rule above, especially the one about
never touching real progress numbers.

### Synced state in the checklist — when Step 2 produced a sync

If the player synced their achievements, the file has to make earned-vs-remaining legible at a
glance without collapsing the two progress tracks into one:

- **Earned achievement items render checked and visibly marked as banked** — a small "earned"
  badge carrying the unlock date, styled distinctly from an ordinary hand-checked box, so the
  player can always tell what came from their profile and what they ticked themselves.
- **The header shows both numbers, each labelled**: guide progress (checked/total — the route
  the player is working through) and achievements earned (n/total, plus gamerscore if the sync
  returned it). A single number pretending to be both is exactly the bug this prevents.
- **A sync line in the header** states when the sync ran and that the file is a snapshot as of
  then, with a one-line note on how to ask for a re-sync.
- **Resolved missables leave the warning voice.** In the missables box, an already-earned
  missable renders dimmed/struck through and labelled "already earned — no longer a risk," so
  it stays readable without competing with live risks. A missable whose window has closed
  unearned is the loudest thing on the page (see Step 2).
- **Hand-checked state survives every re-sync.** Store synced-earned and player-checked as two
  separate fields in the progress blob rather than one boolean, so a re-sync can merge instead
  of clobbering (see Persistence below — it's still one blob, just with two fields per item).
- **No API key, token, or XUID appears anywhere in the file**, and the file makes no live calls
  to any Xbox service — the sync happens at build time and its results are baked in as data.

### Item granularity and ordering — this is the part most likely to be gotten wrong

The player checks this off **in the exact order they'll hit it in-game, one line at a time.**
That does not mean "one line per mission":

- **Bundle uneventful missions together — as a parent line with child rows.** A run of
  consecutive story missions that unlock nothing and aren't missable becomes ONE parent line
  ("Play missions 7-17") with each mission as its own checkable child row beneath it, never a
  parenthetical list of names (see the bundling section in Step 7). Only break a mission out
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

### Sweep for orphaned deferrals — every "later" needs a real step

A guide's own text will sometimes defer part of a task to a later point ("sweep what you can,
a few near the border won't count until the next area opens," "do levels 1-6, the last 2 need
a later unlock"). The recurring bug: the deferral gets stated, but the follow-up step never
gets written — the task is acknowledged and then dropped, and the player is left stranded just
short of 100% with the guide reading as if everything was covered. A related form of the same
bug: a wrap-up or recap section later in the guide describes something as fully done in an
earlier section when it was only partially done there, with no mention of where (or whether)
the rest happened.

Run this sweep on the finished guide **every time before presenting it — including after any
edit — not as a one-time fix.** It's exactly the kind of loop that's easy to write and then
forget to close:

- **Search the full document for deferral phrasing.** Patterns like "won't count/register
  until," "needs … access," "of [0-9]+ levels," "save … for later," "the rest later," "come
  back when/after," "until … opens/unlocks," "for now." Use a regex or a manual scan, but
  actually enumerate the matches — don't rely on remembering what was deferred.
- **For each match, find the actual completion step elsewhere in the document.** It must be a
  real checkbox item in the correct later phase — an acknowledgment, a note, or a mention in a
  recap does not count as completion. If no such step exists, add one in the right later
  section before presenting.
- **Check every summary/recap claim against what actually happened.** If a recap or wrap-up
  says a category was completed in an earlier section, verify that section actually completes
  it in full. Partial completion earlier plus a recap claiming full completion is the same bug
  wearing different clothes.

### Line-by-line dependency check — every mention needs a home

The deferral sweep above catches the cases where the guide *says* "later." This check catches the
much larger class where it doesn't say anything at all: a line names a thing — a vehicle, a
weapon, an unlock, an amount of cash, a stat threshold, a location, an ability, a side activity,
an NPC, an item — and simply assumes it into existence. Nothing in the text sounds unfinished, so
the deferral-phrase regex won't flag it. The player only discovers the hole when they're standing
in the mission with no way to do it, or when they hit 99% because a noun that appeared once in an
unlock description never became a task.

**Go line by line — every checkbox item, every note, every phase note, every missable entry — and
for each thing the line mentions, resolve it in one of two directions.**

**Backward (prerequisites): does the player already have it at this point in the route?** For
every requirement a line implies, the acquisition must be either folded into that same line ("go
get the ambulance from Dillimore General, bring it to Angel Pine") or completed by an earlier line
the player has already checked off. If neither is true, the line is unplayable as written — add
the acquisition step, or move the line to after whatever provides it. Things that hide as silent
prerequisites:

- A required vehicle, weapon, tool, or outfit the route never told the player to obtain
- Cash, currency, or materials the route never had the player earn before a purchase item
- A skill/stat level, license, or proficiency gate on an activity
- Map or region access, a safehouse, a garage, a fast-travel unlock
- An ability, perk, or companion introduced by a mission placed later than this line

**Forward (mentions): does the thing named have its own real completion step somewhere?** Every
noun the guide introduces as something that exists and matters must eventually appear as an
actual checkbox item — not just as a phrase inside another item's text. The highest-risk source
is unlock descriptions: "(gym unlocks)," "also unlocks Freight Train," "opens up the chop shop"
each name a whole content category that will silently never be done if it never receives its own
line. Also check anything named in a note as "you'll want this for X," any activity mentioned as
existing in an area sweep, and any achievement referenced in passing.

Resolution is one of exactly three things, and "it's implied" is not among them:

1. **The line itself completes it** — the acquisition or the task is folded into that same step.
2. **Another line completes it**, and that line is in the correct position (earlier for a
   prerequisite, later for a deferred or unlocked thing). Name it if the connection isn't
   obvious: "you bought this in Phase 2."
3. **It's explicitly out of scope**, stated as such — not required for 100%, not achievement-
   linked, currently unobtainable. Say that on the line, so it reads as a decision rather than
   an omission.

Run this as an actual enumeration, not an impression. Working through the document once, listing
the dependencies each line raises and ticking each against a real step, is the check; reading the
guide and feeling like it hangs together is not. Do it every time before presenting, including
after edits — moving or rewriting a single item can strand a prerequisite that was satisfied by
whatever used to sit above it.

### Assumed-completion check — every "you've already done X" needs an earlier line that did X

The dependency check above resolves things a line *needs*. This one catches the mirror-image bug:
a line that treats an action as **already performed** when no earlier line ever told the player to
perform it. The guide says "now that the garage is upgraded," "with all 12 tapes collected," "sell
the cars you've been stockpiling," "you should be at max muscle by now" — and the route never
contained the step. Unlike the deferral sweep, nothing here reads as unfinished; it reads as
*finished*, which is worse, because the player trusts it and moves on. They discover the gap only
when the assumed thing turns out not to exist.

This is not the same as a missing prerequisite. A prerequisite hole leaves the player unable to
start a task and they notice immediately. An assumed completion quietly writes a task out of the
guide entirely: the noun was mentioned in the past tense, so it never got its own checkbox, and
the player finishes the whole route still missing it.

**Scan the finished guide for past-tense and possessive framing, and for each one find the step
that earned it.** The phrasings that carry this bug:

- "now that you've …", "with X done/unlocked/built", "after you finished …"
- "the X you collected/bought/unlocked earlier", "your X" for anything acquirable
- "you should have X by now", "by this point you'll have …", "assuming max X"
- "sell/use/spend the X you've accumulated" for money, materials, or stock
- Phase intros summarizing the previous phase's state — these are the densest source, because
  they're written last and describe an idealized version of the route rather than the real one

For every match, the earlier step must be a **real checkbox item the player has actually checked
off** at that point in the route, not a mention inside another item's note, not an unlock listed
in passing, and not something a later phase happens to cover. Three legitimate resolutions:

1. **An earlier line does it** — confirm it exists and sits before this line. Name it if the
   connection isn't obvious.
2. **Add the missing step** in the correct earlier phase, then verify it's reachable there.
3. **Rewrite the line to stop assuming it** — turn "sell the cars you've stockpiled" into an
   instruction that includes the stockpiling, or drop the past-tense framing.

Two things this check should specifically look at, because they fail quietly:

- **Ongoing/accumulating requirements** (money totals, stat maxes, collectible counts, reputation
  levels). A later line assuming a threshold — "you'll have the $200k for the airport by now" —
  only holds if the route actually generated it. Trace the arithmetic, don't assume the player
  played efficiently.
- **Anything the player was told was optional earlier.** If an earlier step is presented as
  optional and a later line assumes it's done, that's a contradiction — either make the earlier
  step required, or make the later line handle its absence.

Run this every time before presenting, including after edits — the same edit that moves an item
later can turn a correct past-tense reference into a false one.

### Before presenting: walk it like a player, not a writer

Once the guide is built, this is the last gate, after everything above, before showing it to
the person. Re-read it start to finish as if actually playing, one line at a time, checking:

- Does the sequence of checkboxes match how the game is actually played, with nothing skipped
  and nothing implied twice (the overlapping-items test from Step 7, principle 7)?
- Does every location, vehicle, or target named on a checkbox line actually exist where the
  guide says it does (the location-research requirement from Step 1)?
- Does anything referencing a later point in the game appear before something referencing an
  earlier one (the position-desync check from Step 7, principle 8)?
- Would a player who has never seen this game get stuck or confused by any single line without
  opening its note? Does a "child" item actually belong after its parent? Is anything a bare
  FYI wearing a checkbox?
- Does every "later" / "won't count until" / "the rest" promise in the guide's own text have a
  matching real completion step in a later phase (the orphaned-deferral sweep above), and does
  every recap claim match what the earlier sections actually completed?
- **Line by line: does every dependency a line raises resolve?** For each item, is every
  prerequisite it implies (vehicle, cash, unlock, region access, stat level) either acquired in
  that same line or already completed by an earlier one — and does every thing the line names
  (especially inside unlock descriptions like "gym unlocks") have its own real checkbox somewhere
  later, or an explicit out-of-scope statement? Enumerate them; don't eyeball it (the dependency
  check above).
- **Does every line that speaks of an action in the past tense point at a real earlier step that
  performed it?** "Now that you've …", "the X you bought earlier", "you should have $200k by
  now", and phase intros recapping the previous phase all assert work was done — each one needs
  an actual earlier checkbox, not a mention, and accumulating totals need the route to genuinely
  produce them (the assumed-completion check above).
- **Is everything required for 100% actually in the document, and is every achievement
  covered?** Cross-check the full achievement list and the 100%-requirements breakdown from
  Step 1 against the finished guide, entry by entry — every achievement must appear somewhere
  (as a task, inside a task's note, or as an explicit "not required for 100%" / "currently
  unobtainable" callout), and every 100% category must have real covering steps, not just a
  mention. "It's probably in there somewhere" is not a check; enumerate the list and tick each
  entry off against the document.
- **Test the search bar against collapsed content specifically.** Pick a term that appears only
  inside a collapsed note (a location name, a jargon definition) and one that appears only in a
  bundled mission sub-list, and confirm each is actually found and revealed. Then confirm
  clearing the search restores the expand/collapse state the player had beforehand, and that no
  progress number moved while a filter was active. Searching for a term you already know is
  visible on screen proves nothing — that's the case that works even when the feature is broken.
- If the guide was synced (Step 2): did anything auto-check a story mission, collectible sweep,
  or save-bound 100% task on the strength of a profile-wide achievement? Does the header show
  guide progress and achievements-earned as two labelled numbers rather than one? Is the file
  free of any API key, token, or XUID?
- Is every item still sitting in the final cleanup phase there for a stated, verified reason,
  with everything else moved to its earliest reachable phase (the cleanup-phase audit from
  Step 7)? And does every ongoing whole-game requirement have its habit stated in Phase 1,
  checkpoints along the route, and only a verification-plus-top-up line at the end?

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
- The deferral sweep only catches lines that *admit* something is unfinished. The bigger hole is
  the line that admits nothing: it names a vehicle, an amount of cash, a region, or an unlocked
  activity and quietly assumes it. Read as prose it's fine; played as a checklist the player
  either can't start the task (no prerequisite) or never does the thing at all (a noun that
  appeared once and never became a step). Both directions have to be resolved per line —
  backward to an earlier step that provides it, forward to a later step that completes it — and
  it has to be an enumeration, because the failure mode of this check is that everything *feels*
  covered.
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
- A guide deferred parts of tasks in its own text ("do levels 1-6 now, the last 2 need a later
  unlock"; "sweep what you can, a few near the border won't count until the next area opens")
  and then never added the follow-up step anywhere — the deferral was stated, the loop never
  closed, and a wrap-up checklist near the end even claimed the whole category was finished in
  the earlier section. Deferral text *reads* like handling, which is exactly why it slips
  through: the writer feels the task is covered, the player ends up stranded at 99%. The fix
  that sticks is mechanical, not attentional: sweep the finished guide for deferral phrases
  and demand a real completion step for each match, every time, before presenting (see the
  orphaned-deferrals section in Output Format).
- The final cleanup phase exerts gravity on anything without an obvious story trigger. In one
  guide, three repeatable side activities — a stadium minigame available from the very start of
  the game, a race unlocked simply by reaching a landmark the player passes through in an early
  region, and a repeatable fare-pickup job with no gate at all — had zero mention anywhere
  except a vague "you'll also need to do these eventually" in the cleanup phase, because no
  research was ever done into when they actually become available. Availability is a
  researchable fact per item, never a default. The fix runs in both directions: other content
  genuinely does belong late (single-sitting multi-part achievements, reward dependencies,
  end-game-only access), so the audit is "verify each and state the reason," never "move
  everything earlier."
- Whole-game cumulative requirements (all weapons to max level, usage totals, mastery bars)
  are cheapest as a habit from hour one — "once a weapon maxes, switch to the next" — and most
  expensive as an end-phase grind. State the habit early as its own checklist line, checkpoint
  it at phase boundaries, and make the end-phase line a stats-page verification with a targeted
  top-up, not the task itself.
- The structure that makes these guides scannable — collapsed accordions, bundled sub-lists,
  notes hidden behind a toggle — is the same structure that breaks a naively-built search box.
  Most of the file's text is off-screen at any moment, so a search that filters rendered rows
  finds a fraction of the real matches and confidently reports nothing for the rest. Search the
  data, not the DOM, and auto-expand what matches. The tell that it was never tested properly:
  every term the author tried happened to be visible on screen already.
- A filter is a view, not an edit. A progress bar that jumps because the player filtered the list
  is a genuine scare — they're 80 hours into this file. Keep real progress numbers absolute while
  filtering, and label any filtered-subset count so distinctly it can't be mistaken for the real
  one.
- The first result for "Xbox achievements API" is the GDK/XSAPI Achievements Manager, and it is
  the wrong tool for this skill in a way that isn't obvious until you read who it's *for*: it's
  a C/C++ API compiled into a game, running against an `XUser` inside that game's own process,
  and it can only ever see the title it's built into. Reading a player's profile from outside is
  a different problem with different answers (a personal API key, an XSTS token, a signed-in
  browser, or screenshots). Check whether an API is aimed at game code or at player tooling
  before designing a feature around it.
- Profile-wide achievements and save-bound 100% completion are two different progress tracks.
  A synced achievement earned on an old save is banked forever, but the content behind it can
  still be unfinished on the save the player is on — so a sync may pre-check achievement items
  and must never pre-check missions, sweeps, or 100% tasks. Getting this wrong produces a guide
  that tells a player they've already done things they haven't.
- An empty achievement sync is not a verified zero. Xbox 360-era titles answer on a different
  endpoint family than Xbox One/Series titles, so querying a back-catalogue game the modern way
  returns nothing at all — identical in shape to "this player has earned nothing," and far more
  likely. Same discipline as an empty web fetch: unverified, not verified-absent.
- A re-sync merges, it never overwrites. Players check things by hand that no achievement covers
  (100%-stat tasks) and things they finished before the achievement popped; a sync that
  overwrites state punishes exactly the players who used the checklist most carefully.
- The lessons above skew toward GTA-style open-world games because that's where this skill was
  battle-tested. Don't let that narrow the skill's scope: for each new game, translate the
  concepts (missions → quests/chapters/races, islands → gated acts, vehicle missions →
  repeatable side activities with permanent rewards) instead of pattern-matching for
  GTA-specific structures and concluding a step doesn't apply.
