---
name: xbox-100-percent-guide
description: >
  Generate an optimal 100% completion and all-achievements guide for any Xbox game. Use whenever
  the user names a specific game and wants 100% completion, all achievements, a platinum roadmap,
  or asks what order to do everything in. Triggers on "how do I 100% X", "missable achievements
  in X", "optimal order for X", "completion guide for X", "what should I do first in X", and
  casual phrasings like "I want to do everything in X" or "best way to play X for all
  achievements" — any named game plus completion, achievement, or roadmap intent. Also applies
  when the user asks to turn an existing guide into an interactive checklist, or to revise
  ordering, formatting, or accuracy in a guide this skill already produced. Also triggers on
  syncing, importing, or checking the player's existing Xbox achievements against a guide —
  "sync my achievements," "what do I already have," "update my progress from my Xbox profile,"
  "start the guide from where I actually am."
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
- **The best method for each non-trivial task, and what that method itself requires.** Research
  doesn't stop at "what does this achievement ask for" — it has to reach "what's the fast way to
  do it, and what does the fast way need?" The community's recommended method is usually tied to
  a specific place, crowd, enemy type, vehicle, weapon, or upgrade, and *that* has prerequisites
  the achievement's own description doesn't mention. Capture them, because they, not the
  achievement, determine how early the task can sensibly be routed (see "Earliest reachable is a
  ceiling" in Step 7). An achievement with no gate at all whose only good method sits behind a
  late-game region is the standard shape of this. **Ask about the closing edge too — "does anything
  later remove this method?"** A method relying on a region still being locked, on the player still
  being low-level, or on an NPC or vehicle that later dies or stops spawning gives the task a
  *window* rather than a start point. These are invisible to a missables search, because the
  achievement itself never becomes unobtainable — only the cheap way to earn it does.
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

### Read the community's solution threads, not just the achievement descriptions

Achievement lists, wikis, and completion breakdowns tell you **what** each achievement requires.
They almost never tell you **when in a playthrough to do it**. That information does exist, and it
lives in one specific place: the top-voted solutions on the achievement's own page at a tracking
site — **TrueAchievements** (open the achievement page with its guides/solutions shown, e.g. the
`?showguides=1` view) and **PowerPyx**, plus their equivalents (TrueTrophies, PSNProfiles) when
they cover the same game.

Those threads are written by people who finished the game and then wrote down what they wished
they'd known going in, so they routinely carry the one thing a description structurally cannot:
placement. "Do this after mission X." "Wait until you have Y." "Don't bother before Z." That is
precisely the method-prerequisite and method-window information Step 1 already demands — the
solution thread is usually where it actually lives, and it is invisible from the achievement list.

For every non-trivial achievement:

- **Open the achievement's own page with solutions visible and read the top-voted solution**, not
  just the achievement blurb or a summary page that aggregates blurbs.
- **Extract any placement advice**: a named mission, a named unlock, a "much easier once you
  have…" condition, a warning that it gets harder later.
- **When the community's recommended placement disagrees with the order you derived, that's a
  conflict to resolve, not noise to discard.** Assume they know something your ordering doesn't —
  usually a specific vehicle, weapon, location, or scripted setup that one mission hands over for
  free. Work out what it is, then either adopt their placement or keep yours **and record the
  reason in the item's note**. Silently keeping your own ordering against the top-voted solution
  is how a guide ends up confidently worse than the free advice it was built from.
**These sites 403 plain fetch tools — use a browser instead.** TrueAchievements (and its
TrueSteamAchievements/TrueTrophies siblings) reject automated fetches, so a fetch-style tool
returns HTTP 403 and looks exactly like "no such page." That is a bot-protection response to the
*tool*, not a restriction on the content: the pages are public and load normally in a real browser
session. Open a browser pane at the URL and read the rendered text instead — the solutions,
vote counts and comments all come through. Two things that keep this cheap:

- **The URL form has nothing to do with the block.** Tested directly: the bare
  `trueachievements.com/a21053`, the full slug URL, and the `?showguides=1` variant all return 403
  to a fetch tool, and all render fine in a browser. Don't waste calls trying URL variations to
  find one that slips through — there isn't one. (The bare URL is still the one to *use*, simply
  because it's shortest and the top-voted solution already sits near the top of the rendered text
  without the query suffix.)
- **Cap the text you pull.** The top solution plus its vote count sits in roughly the first
  1,500-2,000 characters. Read that much per achievement rather than whole pages, and navigate
  straight to the next achievement URL in the same tab.

**Read the status code before deciding what went wrong — 403 and 404 need opposite responses.**
A **403** means the server refused *this tool*: the page exists, the content is public, switch to
a browser. A **404** means the server answered normally and the path is wrong: fix the URL, and do
not reach for a browser, which will fail identically. Treating a 404 as a block sends you to open a
browser session to work around a typo; treating a 403 as a dead link discards a source that was
available the whole time. A guessed guide URL that 404s is especially worth re-checking, since
tracking sites restructure paths and not every site covers every game.

If a source still can't be read, it is **unverified, not absent** — say so plainly and leave the
item flagged rather than inventing a rationale for the placement you already had. That is the same
rule as any other empty fetch, and the easiest one to rationalize away, because a 403 arrives
exactly when the existing placement looks perfectly reasonable.

### Which achievement site, and start with the walkthrough

All of this is **supplemental to** the research already specified above, never a replacement for it.
Use whichever of these cover the game:

| Source | Use it for | Notes |
| --- | --- | --- |
| **TrueAchievements** | Xbox titles — the primary source | Two distinct surfaces: a structured game *walkthrough*, and per-achievement *solution threads*. Both matter, and they answer different questions. |
| **PowerPyx** | Modern multiplatform titles | Roadmap-style, often the entire game on one page, which makes it the cheapest read when it exists. Coverage skews recent — confirm the game is covered rather than assuming. |
| **PlayStationTrophies.org** | Anything with a PlayStation release | Trophy names map 1:1 to achievement names for the same game, so its guides transfer directly. Useful when TrueAchievements' solutions are thin. |

**Start with the TrueAchievements walkthrough overview. It is one read that plans every other
read.** The URL is standard per game: `trueachievements.com/game/<Game-Slug>/walkthrough` — e.g.
`.../game/Grand-Theft-Auto-4/walkthrough`. That single page returns:

- Headline counts: achievements, gamerscore, estimated time, **playthroughs required**
- **Missable and unobtainable counts** — a direct numeric cross-check against the missables work in
  Step 3. If your research found four missables and the walkthrough says two, one of you is wrong;
  resolve it rather than averaging. Same for a non-zero unobtainable count.
- Online-only count, which sizes the multiplayer problem before you commit to it
- A numbered **table of contents** with a page per section (overview, general hints, story
  walkthrough, 100% completion, miscellaneous, online, one per DLC). This mirrors the phase
  structure this skill builds, and the story-walkthrough and 100%-completion pages carry ordering
  advice that is exactly what Step 7 is trying to derive — read them before writing the route.
- A **Full Achievement Breakdown** tagging every achievement by type: *Main Storyline, Story
  Completed, Collectable, Cumulative, Time/Date, Missable, Buggy, Time Consuming, Level, Viral,
  Online / Versus / Cooperative, Players Required.*

That breakdown is the triage input for everything below.

**Then take the achievement list page, which is where the per-achievement URLs live.** It sits at
`trueachievements.com/game/<Game-Slug>/achievements` and lists all achievements with their
descriptions and, next to each, a **guide count** ("9 guides", "3 guides"). Two things come from it:

- **The links are how you reach individual achievement pages.** Those pages are addressed by
  opaque numeric ID (`trueachievements.com/a21053`), and the ID is *not* derivable from the
  achievement's name — so collect the links from this page rather than guessing URLs. A guessed ID
  lands on a different achievement in a different game, which is worse than a 404 because it
  returns confident, plausible, wrong content.
- **Guide count is a second triage signal, and a good one.** Many guides means the community found
  the method contested or non-obvious and kept adding better ones; one or two means it is
  straightforward and the top solution will only confirm what you already know. Combine it with the
  type tags: a Collectable or Time Consuming achievement carrying nine guides is the strongest
  possible case for a deep read, while a Main Storyline achievement with two is the weakest.

### Triage before deep-reading — most achievements never need a solution thread

Reading a solution thread for all 60-70 achievements is enormously wasteful, because for a large
fraction of them the placement is already forced and no thread can move it. Decide per achievement
*before* fetching anything.

**Skip the per-achievement read when:**

- It's tagged **Main Storyline** or **Story Completed** — the story dictates its position, full stop
- Its placement is already fixed by a gate you have verified (region unlock, chapter, act)
- It's a whole-game cumulative stat this skill already routes as a habit — the habit *is* the
  answer, and placement isn't the question
- It's trivially satisfied in passing by content already in the route

**Deep-read the top solution when:**

- Tagged **Missable** or **Buggy** — highest cost of getting it wrong, so these come first
- Tagged **Collectable**, **Time Consuming**, or **Cumulative** — where an efficient method or a
  good sweep order saves hours
- Tagged **Time/Date** — these frequently carry a window (see method windows in Step 7)
- It has no story gate and its method is a *choice*: grinds, minigames, skill challenges,
  location-dependent tasks
- **You placed it by inference rather than by a verified gate.** Your own uncertainty is a triage
  signal, and the cheapest one you have.

On a 60-70 achievement list this typically leaves 15-25 warranting a deep read. **Record which
achievements you triaged out and why**, so a later pass extends the work instead of repeating it,
and so a wrong triage call is auditable rather than invisible.

### Keeping browser reads cheap

- **One tab, navigate sequentially by URL, never re-read a page.**
- **Cap each achievement page at roughly 1,500-2,000 characters.** The top-voted solution and its
  vote count sit near the top of the rendered text; everything past that is comments and lower-
  voted duplicates.
- **Stop as soon as the top solution confirms placement you already derived.** Reading the
  remaining nine guides cannot change the answer.
- **Prefer one walkthrough page over N achievement pages for a cluster.** All the online
  achievements, or a whole DLC, are usually covered on a single walkthrough page — one read
  instead of ten.
- The walkthrough offers a **Full Printer-Friendly Version** concatenating every page. That is one
  navigation instead of eight, but it is long — read it in capped slices, not whole.
- Prefer PowerPyx when it covers the game and you need broad roadmap context, since a single page
  often replaces a dozen individual lookups.

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
- **Does anything advance on elapsed time rather than on player action?** In-game days passing,
  a business or property accruing income, a build/craft/crop timer, a stock price moving, a
  letter or phone call arriving some days after a trigger, a relationship cooling off, a
  real-time cooldown on a repeatable job, a vehicle or spawn refreshing. These are not tasks,
  they are clocks, and the only sequencing question that matters is **how early the clock can be
  started** — research the earliest point in the route where the timer can be set running, the
  same evidence standard as any other fact. A timer started at its earliest legal point is free;
  the same timer started where its reward gets collected costs the player the entire wait.
  **Then check whether the timers are independent or chained**: several separate clocks can all
  run at once, but a sequence where each step is gated on time since the *previous* step (visit
  an NPC, wait, visit again, wait, visit again) can't be parallelized at all — it needs the
  route rearranged around it instead. Establish how many links the chain has and how much time
  each gap needs, because that's what the route has to fill. See the dedicated section in
  Step 7 for how both cases get written into the route.
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

### Play order is the spine — grouping is presentation, and it never reorders anything

Before any of the principles below: the checklist's primary job is to be **the exact sequence
the player executes in-game, top to bottom.** Everything else this skill specifies about
structure — nesting side content under the mission that unlocks it, bundling uneventful missions
into a parent line, phase accordions, collapsible notes — is presentation layered on top of that
sequence. It exists to make several hundred items scannable and to show *why* an item sits where
it does. It is never a reason to move an item away from the point where the player actually does
it.

**When grouping and play order disagree, play order wins and the group gets broken up.** Every
time, without weighing it as a tradeoff.

The practical consequence is that nesting is legal only when the children genuinely *are* the
next things the player does after the parent. If a piece of side content unlocked by mission 6
is best done immediately, it nests under mission 6. If it's best done 40 items later — because
of area access, a resource it needs, a timer, or simple efficiency — it is not a child of
mission 6 at all. It's its own item at its own correct position, carrying a note that names
what unlocked it ("opened up by 'Drive-Thru' back in Phase 1"). The unlock relationship is
information; the position is the instruction. Encode the relationship in a note, never by
dragging the item out of its place in the route.

This is what makes the checklist a route rather than an outline, and it's the rule that decides
the time-gated cases further down.

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
13. **Waiting is never a step.** Anything that advances on elapsed time gets started at the
    earliest point the route allows and then runs *underneath* the rest of the route. Where a
    chain of steps is gated on time between each one, the clock can't move — so the links get
    interleaved into the route with real work between them, never written out as a contiguous
    block. The player is never parked in front of a clock, and two waits never sit next to each
    other — see the dedicated section below.

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

### Earliest reachable is a ceiling, not a target

The cleanup audit below pushes content *forward*, because a catch-all end phase collects
anything nobody researched. That correction has its own failure mode: an item gets yanked to the
front on the strength of "it's technically possible there," which is a different question from
"it's sensible there," and only the second one decides placement.

The bug is nearly always that availability was assessed on **the task** when it should have been
assessed on **the method**. Most tasks have a best way to do them — a specific spot, a reliable
crowd, a particular vehicle or weapon, a farming route, a repeatable encounter — and *that method
carries prerequisites the raw task doesn't*. The task looks ungated, so an audit stamps it
"available from the start" and drops it in Phase 1, where the only version the player can
actually attempt is the slow, miserable one.

A worked example, generalizable to any genre: an achievement for landing a number of melee
counters has no gate whatsoever — the player can punch a pedestrian five minutes in. But the
method that makes it quick is a particular place where NPCs reliably fight back rather than
fleeing, and in GTA IV that place (the Higgins Helitours queue, Fishmarket South) is in Algonquin,
across bridges the story hasn't opened yet. Placed "as early as possible," the item lands before
mission 6 and asks the player to do a version of the task that's dramatically worse — or to
attempt it somewhere they can't yet legally reach. The achievement was ungated; the good method
never was.

**Place every item at the earliest point where its best method is available and the player is
already going to be nearby** — not the earliest point the task is technically possible. Doing
something earlier is the wrong call when "earlier" means:

- **A worse method** — grinding the slow way because the efficient spot, crowd, tool, vehicle, or
  enemy type isn't accessible yet
- **A dedicated trip** — crossing the map, or backtracking to a prior region/act, for something
  the player would pass on the way to something else later. Principle 4 (minimize backtracking)
  does not lose to "earlier"
- **A harder attempt** — a difficulty-, combat-, or skill-gated task tried before the gear,
  upgrades, levels, abilities, or perks that make it routine
- **Paying full price** for something that gets cheap or free later, or spending a resource the
  route hasn't generated yet
- **Grinding a stat, currency, or resource** that a later mission or reward simply hands over

Translate that across genres rather than pattern-matching the example: in an RPG it's a bounty
best cleared once a class ability trivializes it; in a shooter, a weapon-specific challenge best
saved for the map where that weapon is issued; in a racer, a time trial best run after the car
upgrade the campaign gives you anyway; in a platformer, a collectible best swept after the
traversal ability that turns a precision jump into a walk.

#### Method windows close as well as open

The prerequisites above are all about a method becoming *available*. The mirror case is a method
that **expires**, and it is easy to miss entirely because the achievement itself never becomes
unobtainable — only the cheap way to get it does. Nothing in a missables search surfaces these,
because nothing is being permanently lost; the player just quietly ends up doing a five-minute
task the forty-minute way.

The usual causes, in any genre:

- **A method that depends on something still being locked.** Trespassing into a region the story
  hasn't opened often triggers an instant maximum alert state, a unique enemy, or a boundary
  behaviour that simply stops existing once that region unlocks normally.
- **A method that depends on the player still being weak or low-level** — scaled enemies, a
  tutorial-grade encounter, an early-game spawn table that stops appearing.
- **A method that depends on a character, faction, vendor, or vehicle** that dies, leaves,
  turns hostile, or stops spawning after a story beat.
- **A method that depends on an unpatched or unfinished world state** — a structure that gets
  destroyed in a cutscene, an area that becomes a mission-only interior, a shop that closes.

**Research the closing edge, not just the opening one.** For every method, ask both "what does
this need?" and "does anything later take it away?" A method with both an opening and a closing
gate defines a *window*, and the task belongs inside that window — which is frequently neither
the earliest nor the latest point in the route.

**A closing window is flagged like a missable, because it behaves like one.** Put the warning
inline at the task ("easy only until mission N — after that you're doing the hard version") *and*
inline on the step that closes it ("finishing this mission ends the cheap method for X — make
sure it's checked off above"). The achievement is not missable, so it does not belong in the
missables box as a lost-forever risk; the cost is real, though, and the player has to see it
coming from both sides.

**Two things still outrank all of this** — they're principles 1 and 2, and they're deliberately
willing to pay the cost: **missables** and **power-unlocks** go early even when early is
expensive. A missable done the hard way beats a missable lost, and a power-unlock's entire value
is the hours it saves everything after it.

Everything else resolves by honestly comparing the cost both ways. The reason to do things early
is a small post-story cleanup, not earliness as a virtue: a task the player will fly straight
past in Phase 5 costs nothing to leave in Phase 5, while the same task in Phase 1 can cost a
cross-map trip and a harder attempt. **When early and late are genuinely comparable, go early** —
that's what keeps the cleanup phase small. When they aren't, go where it's cheap.

**Then record the decision in the item's note** ("left until Phase 4 — the Helitours crowd is the
fast way to do this and Algonquin isn't open before then"). An unexplained late item is
indistinguishable from an unresearched one, and the next pass over the guide will drag it forward
again on exactly the reasoning this section exists to stop.

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
  **by its best method** — never merely the earliest phase where the task is technically
  possible (see the ceiling section above; this is the single most common way this audit
  overcorrects). Earliest-reachable is the ceiling, not the target: the other ordering
  principles — grouping by area, minimizing backtracking, money-before-spending, and so on —
  still decide the exact placement within that window. The cleanup phase keeps only a one-line
  verification for it ("done in Phase X if you followed along"), never a line presenting it as
  new work.
- **If a real mechanical reason keeps it late or bundled, leave it — and state the reason
  explicitly** in the item or its note, so the placement reads as a verified decision rather
  than a thing nobody checked. Real reasons include: an achievement that requires several
  sub-parts completed in one sitting or one session; a fixed reward that another achievement's
  resource requirement depends on (see Step 5); content genuinely only reachable near or after
  the end of the story; and **the early version being materially worse than the late one** — the
  efficient location, crowd, vehicle, weapon, or upgrade that makes the task quick isn't
  available yet, so doing it early means doing a harder task for the same reward.

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

### Waiting is never a step — elapsed time runs underneath the route

Elapsed-time requirements (identified in Step 5) are the one category where a guide can be
completely accurate and still waste hours of the player's life. The failure looks like this:

**Wrong:**

```
□ Wait a few in-game days for the property to start paying out.
□ Wait a few in-game days for the newspaper to run the story.
□ Wait a few in-game days for Sofia to call about the next job.
```

Three clocks that could all have been ticking simultaneously since Phase 2, run one after
another while the player does nothing. **Back-to-back waits are almost never a property of the
game — they're a drafting artifact.** They appear because the guide was written in the order
rewards get *collected*, so each timer was started at the line where its payoff is claimed,
which serializes clocks that the game itself runs in parallel. Even a single isolated "wait"
step is usually the same bug in smaller form.

Three things fix it, in this order:

- **Start every clock at its earliest legal point.** Research when the timer can first be set
  running — buying the property, triggering the phone call, planting the thing, making the
  deposit — and put *that* action in the earliest phase where it's reachable. This is the whole
  fix; the other two only clean up what's left.
- **Let it run underneath real work.** Once started, the route keeps going with actual tasks and
  the collection line appears later, wherever the player is genuinely nearby again (all the
  usual grouping and backtracking rules still decide exactly where). Concurrent timers collapse
  into one window sized by the longest one, not a queue.
- **Only if the window genuinely can't be filled**, name the game's own cheapest way to burn the
  clock — sleeping at a safehouse, saving to advance six hours, a fast-travel leg — as *one*
  line, not one per timer, and say how much time it needs to cover. "Wait a few in-game days"
  with no mechanism is never acceptable; if the player must pass time, tell them the fastest way
  the game provides.

**How this renders in the checklist:** the *start* is a real checkbox ("Buy the Vank Hoff Hotel
— income accrues from here"). The *collection* is a real checkbox later. The wait itself gets no
checkbox at all — it is not something the player does (the no-FYI-checkbox rule in Output
Format), so it lives as a note on the collection line: "needs ~5 in-game days; you started this
back in Phase 2 and the missions since have covered it."

**Then verify the window is actually covered.** If the intervening route is shorter than the
timer, the note is a lie — move the start earlier, move the collection later, or add the
explicit pass-time line. Checking this means counting the real steps between start and
collection, not assuming they add up.

#### Dependent chains: the clock can't move, so the route has to

Everything above assumes the timers are **independent** — several clocks that could have been
running at once. The harder case is a **dependent chain**, where each wait is gated on the step
before it: talk to an NPC, wait a few in-game days, talk to them again, wait a few more, talk to
them a third time. Nothing can be started earlier, because link 2 doesn't exist until link 1 has
happened and the days have passed. Starting the clock early is not available as a fix here, and
a guide that only knows that fix will write the chain out as three adjacent checkboxes with two
waits wedged between them — which is exactly the thing that reads as "sit there and do nothing"
three times in a row.

**For a dependent chain, the links are interleaved into the route, never listed as a contiguous
block.** Each link goes at the point in the route where the required time has *already accrued
through normal play*, so the intervening steps are real tasks the player was going to do anyway.
The wait is then invisible: by the time they reach link 2's line, the days have passed.

This is not an exception to the nesting rule — it *is* the nesting rule, applied correctly. Per
the spine principle above, a child item is only a child when it's genuinely the next thing the
player does; links 2, 3, and 4 of a timed chain are not, so they were never eligible to nest
under link 1 in the first place. Holding the chain together as one visual block would be
grouping overriding play order, which is the thing that never happens.

Splitting does cost discoverability, and that cost is paid the same way any out-of-position
relationship is paid for — in notes, not by moving items:

- **The first link carries the map of the whole chain** in its note: how many links, roughly how
  much in-game time each gap needs, and where each subsequent link sits in the route ("4 visits
  total, ~3 in-game days between each; the next three are in Phase 3 after the docks missions,
  Phase 4 opening, and Phase 4 after the airport"). The player should never be surprised by a
  link appearing, or wonder whether they missed one.
- **Every later link carries a back-pointer**: "visit 3 of 4 — you did visit 2 in Phase 3; enough
  days have passed since then." Without it, a lone "talk to X again" line 60 items later reads as
  an orphan or a duplicate.
- **Count the intervening steps for every gap, not just the first one.** Each individual gap has
  to be covered by the work actually sitting between those two links. A chain can be correctly
  interleaved at the front and collapse into back-to-back links at the end, where the route runs
  out of nearby tasks — that tail is where this bug survives an inattentive check.
- **If a gap genuinely can't be filled** — the player has cleared everything reachable in that
  window — that specific gap gets the named pass-time mechanism from above, and only that gap.
  One unavoidable "sleep twice at the safehouse to cover the remaining two days" is a fine
  outcome; three of them in a row means the interleaving was never done.
- **The chain still has to satisfy the deferral and dependency rules** (Step 7 principle 10, and
  the line-by-line dependency check): every link is a real checkbox in a real phase, and the
  final link is what closes the loop — the first link's note describing the rest of the chain
  does not count as completing it.

The test for a dependent chain is the same one as everywhere else, applied to time instead of
content: **if the player checks these boxes top to bottom in order, are they ever standing still?**
If two links of a chain touch, or if only a lone pass-time line separates them, the chain wasn't
interleaved — it was transcribed.

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
  **This nesting only applies when the unlocked content is genuinely what the player does
  next.** Per the spine principle in Step 7, play order outranks grouping without exception: if
  the best time to do the unlocked thing is much later in the route, it does not become a child
  here — it goes at its correct position with a note naming what unlocked it. Nesting shows the
  relationship *when the relationship and the order happen to agree*; it is never the reason an
  item sits somewhere.
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

### Premise-change sweep — carried-over prose outlives the rule that justified it

The three checks above hunt for facts that don't resolve. This one hunts for **prose that was true
under a premise the guide no longer follows.** Whenever a structural rule changes — the routing
model, a pacing or timer assumption, a grouping policy, phase boundaries, whether content is
save-bound or profile-wide — every sentence written to *explain* the old rule survives the edit
untouched and quietly becomes a contradiction.

It hides better than any other class of error, for a mechanical reason: **nobody re-reads what
they didn't consciously edit.** The diff shows the items that moved. It does not show the
paragraph three phases away whose job was to tell the player why items sit where they do.

The concentration is predictable. Sweep these first:

- **Phase notes and phase intros** — their entire purpose is to state the phase's governing logic,
  so they are pure premise, and they are the densest source by a wide margin
- **The top-of-guide framing** — the paragraph explaining how to use the route at all
- **Recap, wrap-up, and final-sweep sections** — written to summarize a route that has since changed
- **Any item note whose job is to justify a placement** ("this waits until now because…")

**The sweep is mechanical, and you have to name the vocabulary before you start editing.** Write
down the words the old premise used, then grep every note for them and confirm each hit is still
true. If the routing rule moved from "everything at its earliest unlock" to "everything at its
cheapest method," the vocabulary is *unlocks*, *earliest*, *as soon as*, *where it becomes
available*. Enumerate the matches; don't rely on remembering which paragraphs described the rule.

**Sweep every premise the guide asserts, not only the one you just changed.** This is the part
that gets skipped, and it's where the surviving bugs are. A guide states several structural
premises — is there a clock on this save, is the map open, is progress save-bound or profile-wide,
does side content bank for later — and any of them can be contradicted by a note written under an
earlier draft, with no recent edit to draw attention to it. So the sweep runs in two directions:

- **Against the current rules** — each note still true under what the guide now does.
- **Against each other** — no two notes asserting incompatible premises. A phase note reading
  "clock target leaving this phase: under 16 hours" is not detectably wrong on its own; it is
  wrong because another phase note says there is no clock on this save at all. Contradictions
  between notes are invisible to a check that reads each note in isolation, which is how they
  survive several passes.

List the guide's premises explicitly, then check every note against the list. Grepping only the
vocabulary of the rule you happened to edit will pass a guide that still contradicts itself
somewhere else.

### Never write positional cross-references

A note that points at another item **by position** — "two steps above," "the confirmation step
below," "the next item," "three rows down" — is a fact about the current ordering, not about the
game. Every reorder invalidates it silently: nothing errors, the sentence still reads fluently,
and it now points somewhere else or nowhere. Since this skill reorders items constantly (method
windows, chain interleaving, cleanup audits, play-order corrections), positional references are
guaranteed to rot, and they rot in the notes nobody re-reads.

**Name the thing, not its distance.** "You unlocked Roman's taxi earlier in this phase when you
pushed his Like past 90%" survives any reordering; "you unlocked it two steps above" does not.
Where the reference genuinely needs locating, name the phase or the item's own title — both
travel with the item — never a count of rows or a relative direction.

This applies to the guide's own text, not to phase names: "in Phase 2" is stable because phases
are named units, while "two items up" is not. Sweep for the pattern before presenting; it is a
short, high-precision regex (`\b(two|three|\d+) (steps?|rows?|items?) (above|below)\b`, plus
"the next/previous step"), and every hit is a defect.

Two things this sweep specifically catches:

- **A summary that still describes the old route.** "Everything else went into the phase where it
  unlocked" reads as reassurance and is now simply false — and it is exactly the sentence a player
  uses to decide whether to trust the ordering.
- **Grammatical seams from targeted replacements.** Patching a clause inside a carried-over
  sentence frequently leaves a broken or double-conjunction sentence. Re-read the *whole* sentence
  after any in-place edit, not the fragment you replaced.

This is Step 7's principle 8 — re-check position after editing content — applied to prose instead
of items. Same failure, different surface: the thing you edited is fine, and the thing that
described it is now wrong.

### Before presenting: walk it like a player, not a writer

Once the guide is built, this is the last gate, after everything above, before showing it to
the person. Re-read it start to finish as if actually playing, one line at a time, checking:

- Does the sequence of checkboxes match how the game is actually played, with nothing skipped
  and nothing implied twice (the overlapping-items test from Step 7, principle 7)?
- **Is anything sitting where it sits because of grouping rather than play order?** For every
  nested child, ask whether the player really does it right after the parent — if the honest
  answer is "later, but it belongs to that mission," it's mis-positioned: move it to where it's
  actually done and put the unlock relationship in a note (the spine principle in Step 7).
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
- **Did any structural premise change during this revision, and does the prose still match it?**
  Re-read every phase note, phase intro, and recap against the *current* rules, including the ones
  carried over unedited — those are where the contradiction lives, because they were never
  consciously re-read. Grep for the old premise's vocabulary and confirm each hit (the
  premise-change sweep above). List the guide's premises and check every note against **all** of
  them, and against each other — a stale "clock target: under 16 hours" is only detectable against
  another note saying there is no clock on this save.
- **Does the missable count match the walkthrough's?** TrueAchievements' walkthrough overview
  states missable and unobtainable counts outright. Compare them against Step 3's findings; a
  mismatch is an unresolved research conflict, not a rounding difference.
- **Has every achievement's placement been reconciled against the top community solution?** Go
  achievement by achievement against TrueAchievements/PowerPyx solution threads — not the
  descriptions, the solutions — and for each one either match their recommended placement or carry
  a stated reason for differing. An item sitting in a phase the top-voted solution says is the
  wrong one, with no note explaining the choice, is an unresearched placement wearing a confident
  face. Unreachable sources stay flagged as unverified rather than silently ratifying what you had.
- **Does any note point at another item by position?** "Two steps above," "the step below," "the
  next item" — every hit is a defect, because this skill reorders constantly and the reference
  rots silently. Name the item or its phase instead.
- **Is the player ever told to wait?** No two elapsed-time waits may sit adjacent; no timer may
  start later in the route than it could have; every wait note must point at real intervening
  steps that actually fill the window (count them, don't assume); and any genuinely unavoidable
  pass-time line must name the game's own fastest mechanism for it rather than saying "wait a
  few days" (the waiting section in Step 7).
- **Are any time-gated chains sitting as a contiguous block?** For every sequence where each
  step is gated on time since the one before it, confirm the links are interleaved through the
  route with real tasks in *every* gap — check the last gaps as carefully as the first, since a
  chain that runs out of nearby work collapses at its tail. Confirm the first link's note maps
  the whole chain and every later link points back to the previous one (the dependent-chain
  section in Step 7).
- **Is anything placed early that's genuinely cheaper later?** For every item moved forward, check
  that its *best method* — not just the task — is available there and that the player is already
  nearby. An early placement that forces a cross-map trip, a worse grinding spot, or a fight
  without the gear that trivializes it is a regression, not an optimization (the ceiling section
  in Step 7). Missables and power-unlocks are the standing exceptions and go early regardless.
- **Does any task's cheap method expire, and is the task inside that window?** Check both edges,
  not just the opening one — a method that needs a region still locked, an NPC still alive, or the
  player still low-level defines a window, and the task has to sit inside it with the closing edge
  flagged both on the task and on the step that closes it (method windows, Step 7). **When
  auditing an existing guide, an item's own note is a claim to verify, not evidence** — a note
  asserting why a placement is correct is precisely the thing under audit, and re-reading it
  proves nothing. Verify the placement against a source, not against the guide's own reasoning.
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
- A real complaint from use: a guide had several "wait a few in-game days" steps back to back.
  That was never a fact about the game — it was an artifact of writing the route in the order
  rewards are *collected*, which starts each timer at its own payoff line and serializes clocks
  the game runs in parallel. Elapsed time is the one requirement that costs nothing when started
  early and costs the full wait when started late, so the fix is positional, not cosmetic: find
  the earliest point each timer can be set running, put the start there, and keep writing real
  steps underneath it. Shortening the stated wait, or merging three waits into one shorter wait,
  fixes the symptom and leaves the bug. Adjacent waits in a draft are a signal to go back and
  ask where each clock *could* have started.
- The cleanup-phase audit overcorrects. Told to move anything not genuinely gated late to its
  earliest reachable phase, a guide starts placing items at the earliest point they're
  *technically possible*, which is a different and much weaker claim. The tell from real use:
  GTA IV's "Finish Him" (melee counters) landed before mission 6, because countering a pedestrian
  is ungated — while the method everyone actually uses is the Higgins Helitours queue in
  Fishmarket South, Algonquin, an island the story hasn't opened at that point. **Availability
  has to be assessed on the method, not the task.** Most tasks have a best way to do them, that
  way is tied to a place/crowd/vehicle/weapon/upgrade, and the tie carries prerequisites the
  achievement description never mentions. Same shape in any genre: the bounty that's trivial once
  a class ability lands, the weapon challenge best saved for the map that issues that weapon, the
  time trial best run after the campaign hands over the car.
- Methods expire, and nothing in a missables search will tell you. GTA IV's One Man Army (survive
  five minutes at six stars) is the case that exposed this: the community method is to steal a
  helicopter from Higgins Helitours in Algonquin and fly over Alderney *while Alderney is still
  locked*, because entering a locked island grants six stars instantly and nothing on the ground
  can touch a helicopter circling at altitude. That needs Algonquin open (mission 31) and Alderney
  still shut (mission 38) — a window of exactly seven missions. Earlier there is no helicopter;
  later the trick is gone forever and the task becomes a firefight in a safehouse lobby. The
  achievement is never unobtainable, so no missables research surfaces it; the player just
  silently does a five-minute task the hard way. Research both edges of a method, not just the
  opening one, and flag the closing edge on the task *and* on the step that closes it.
- Changing a routing rule silently invalidates the prose that explained the old one, and the
  explanation is never in the diff. Moving two items out of Phase 1 to their cheaper method
  windows left three phase notes still telling the player "side content sits in the phase where it
  actually unlocks" and "everything else went into the phase where it unlocked" — reassurance that
  had become false, sitting in the exact paragraphs a player reads to decide whether to trust the
  ordering. Phase notes are the densest source because they are pure premise: their whole job is to
  state the phase's governing logic. The fix is mechanical, not attentional — name the old
  premise's vocabulary, grep every note for it, confirm each hit. A related tell from the same
  edit: replacing a clause inside a carried-over sentence left an ungrammatical double-conjunction
  seam, because only the fragment was re-read and not the sentence around it.
- The placement information this skill spends the most effort deriving is often already written
  down, for free, in the top-voted solution thread on the achievement's own TrueAchievements or
  PowerPyx page — and nowhere else. Achievement lists and wikis describe *what* an achievement
  needs; solution threads are where finished players say *when to do it* ("best done after mission
  X," "wait until you have Y"). A guide can pass every internal check in this skill, be entirely
  factually accurate, and still place an achievement in a phase the community consensus says is the
  wrong one — because none of the internal checks ever consult that consensus. Read the solutions
  per achievement, and treat disagreement as a conflict to resolve and record, never as noise.
  GTA IV's Wheelie Rider was the case that surfaced this: the guide had it in Phase 1 on a
  reasonable-sounding "any bike, airport runway" method, while the top TrueAchievements solution
  says to use a *scooter*, because a moped physically cannot loop over backwards, which turns a
  balancing act into holding one stick — and no airport trip. Note what the reconciliation
  actually produced: the thread framed its advice as "after mission X" because that mission hands
  you a scooter, but the transferable insight was the vehicle, not the mission. Read the solution
  for its *mechanism*, then decide placement yourself — adopting "do it after mission X" verbatim
  would have moved the item four phases later for no reason once you can get the same vehicle
  earlier.
- The expensive way to use solution threads is to read all 65 of them. The cheap way is to read
  the walkthrough overview *first* — one page that reports missable and unobtainable counts,
  playthroughs required, a section-by-section table of contents, and a breakdown tagging every
  achievement by type (Main Storyline, Collectable, Cumulative, Missable, Buggy, Time Consuming,
  Time/Date…). Those tags are a ready-made triage list: story-tagged achievements have forced
  placements and need no thread at all, while Missable/Buggy/Collectable/Time-Consuming ones are
  where a thread actually changes the route. Roughly a third of a list warrants a deep read, and
  deciding which third costs one page.
- A source that states a count you also researched is a free correctness check, not just content.
  The walkthrough's "Missable Achievements: 2" is directly comparable to Step 3's output; if the
  numbers differ, one of them is wrong and the disagreement is the finding.
- Don't hunt for a URL form that slips past a block. Tested on TrueAchievements: bare, full-slug
  and `?showguides=1` URLs all 403 a fetch tool and all render in a browser — the block keys on the
  tool, not the address. And read the code: 403 means "wrong tool, page is fine, use a browser,"
  while 404 means "the server answered and your path is wrong, fix the URL." Confusing them costs
  either a pointless browser session or a discarded source that was reachable all along.
- A fetch tool returning 403 is a statement about the tool, not the content. TrueAchievements and
  its sibling sites block automated fetches while serving the same pages normally to a browser, so
  a 403 there is not "unavailable" — it means use a browser pane and read the rendered text. Two
  achievement placements in one session were nearly left unverified on the strength of a 403 that
  a browser resolved in seconds.
- A premise sweep that greps only the rule you just changed will pass a guide that still
  contradicts itself elsewhere. A stale "clock target leaving this phase: under 16 hours" survived
  a full premise sweep because the sweep was built from *routing* vocabulary, while that line is a
  *timer* premise — and it isn't wrong in isolation at all. It's wrong only against another phase
  note stating there is no clock on this save. Enumerate every premise the guide asserts, then
  check notes against the list and against each other; contradictions between notes are invisible
  to any check that reads one note at a time.
- **Positional cross-references rot on every reorder.** "You unlocked it two steps above" was
  written when it was roughly true, then an unrelated item moved and it silently began pointing at
  the wrong thing — no error, no broken render, a sentence that still reads fine. This skill
  reorders constantly (method windows, chain interleaving, cleanup audits), so these are guaranteed
  to break. Name the item or its phase, never a count of rows or a direction. It's a cheap regex to
  sweep for and every hit is a real defect.
- When a collaborator reports that a defect "came back," check whether it was ever actually fixed
  in the artifact you were handed before accepting the diagnosis. A stale line in an exported file
  usually means the export predated the fix, not that a regenerator reintroduced it — and those two
  causes lead to completely different remedies. Verify provenance against the file as received; the
  substantive complaint (that the line is wrong and was missed) can be entirely valid while the
  proposed mechanism is not.
- **When auditing a guide, its own notes are claims under audit, not evidence.** A placement that
  came with a confident justification got waved through on a review pass purely because the
  justification read well — the note asserted a method that the research did not actually support,
  and re-reading the note "confirmed" it. A guide's stated reasoning can only be checked against a
  source; checking it against itself always passes.
- Early placement is a means, not a virtue. The goal is a small post-story cleanup, so a task the
  player will pass anyway in Phase 5 costs nothing left in Phase 5, while the same task in Phase 1
  can cost a dedicated cross-map trip and a harder attempt for identical reward. Compare the real
  cost both ways: comparable → go early; not comparable → go where it's cheap, and write the
  reason into the note, or the next audit drags it forward again. Missables and power-unlocks are
  the two standing exceptions — they go early even when early is expensive, because a lost
  missable is unrecoverable and a power-unlock pays back across everything after it.
- The checklist is a route first and an outline second, and that precedence has to be stated
  rather than assumed. Nesting, bundling, and phase accordions are presentation — they exist to
  make hundreds of items scannable and to show why an item sits where it does. Left unranked,
  they quietly start deciding *position*: content gets held next to the mission that unlocked it
  because that reads tidily, even when the player shouldn't do it for another 40 items. The rule
  is that play order wins every time and the group gets broken up, with the unlock relationship
  preserved in a note. An item's position is an instruction; its grouping is only information.
- There are two shapes of waiting and only one of them has an easy fix. Independent timers get
  started early and run in parallel. A **dependent chain** — interact with an NPC, wait a few
  in-game days, interact again, wait again — can't be parallelized at all, because each link only
  exists once the previous one happened. Writing that chain out as consecutive checklist items is
  the version of this bug that survives the "start the clock early" fix, because there is no
  earlier clock to start. The route is what moves: each link goes where the required days have
  already accrued through normal play, with real tasks between, the first link's note mapping the
  whole chain and each later link pointing back to the previous one. Watch the *tail* of a chain
  specifically — interleaving is easy at the start and collapses at the end, once the route runs
  out of nearby work.
- If the player genuinely must pass time with nothing to do, that's a mechanic question, not a
  shrug: name the game's own fastest way to advance the clock (sleep at a safehouse, save to
  advance six hours, a fast-travel leg) and how much of the window it covers. "Wait a few in-game
  days" tells the player something is required without telling them how to do it, which is the
  same failure as "any bar with a pool table."
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
