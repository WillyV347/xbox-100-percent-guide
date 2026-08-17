---
name: xbox-100-percent-guide
description: >-
  Generate an optimal 100% completion and all-achievements guide for any Xbox game. Use whenever
  the user names a specific game and wants 100% completion, all achievements, a platinum roadmap,
  or asks what order to do everything in. Triggers on "how do I 100% X", "missable achievements
  in X", "optimal order for X", "completion guide for X", "what should I do first in X", and
  casual phrasings like "I want to do everything in X" — any named game plus completion,
  achievement, or roadmap intent. Also triggers on syncing or checking the player's existing Xbox
  achievements against a guide — "sync my achievements," "what do I already have," "start the
  guide from where I actually am." Stays in force for every follow-up turn about a guide it built,
  not just the request that started it: questions ("why is this in Phase 3"), corrections,
  additions ("add the DLC," "I already did X"), re-ordering, re-theming, and complaints all
  re-enter this skill rather than being answered from memory of the build.
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
platformers, indies, multiplayer titles. Many examples below are shaped like open-world action
games, because that's the genre this skill has been exercised on most, but every principle
generalizes: read "mission" as the game's own progress unit (quest, chapter, level, race, run,
match, turn, case), "region" as any slice that can be gated (act, level-select entry, difficulty
tier, unlocked character, faction path, playlist), and "side activity" as any repeatable optional
content with a reward. Don't skip a step because the game "doesn't have that" — translate the
concept to the game's own systems instead.

### Every turn after the first is still this skill

The build is the beginning of the job, not the job. A player lives in one of these files for
50-200 hours and comes back with questions, corrections, and additions the whole time — "why is
this in Phase 3," "where exactly is that terminal," "I already did X out of order," "add the DLC,"
"re-sync me," "this theme doesn't look like the game," "this step didn't work." **Every one of
those re-enters this skill.** They are not conversational follow-ups to be answered from memory of
the build; they are further work on the artifact, held to every standard below.

Concretely, on any follow-up turn:

- **Research the answer, don't recall it.** Whatever the question touches gets the same sourcing
  standard as Step 1 — including the per-game notes store, which is an input to verify against and
  never a substitute (see the standing-questions section below). "I built this guide, so I know"
  is exactly the confidence that ships an invented specific.
- **The answer's home is the artifact, not the reply.** If the player had to ask, the guide didn't
  say it. Answer them in chat *and* put the answer into the line that should have carried it —
  otherwise the same question is waiting for the next player, and the guide's own text now
  contradicts what you just told them. This is the executability rule in Output Format, arriving as
  a bug report.
- **Any edit re-runs the sweeps.** Every verification pass in Output Format applies after a
  revision round, not only after a fresh build — the defects this skill guards against are mostly
  *created* by editing (see "Every sweep re-runs after an edit round" and the walk-through pass).
  A one-line change is an edit round.
- **A player's report is evidence, and their proposed cause is a hypothesis.** "This is wrong" is
  almost always right about the symptom; check the mechanism against the file as it actually
  stands rather than accepting or dismissing the diagnosis wholesale.
- **Deliver the updated file, not a description of the update.** The deliverable never changes: an
  edited guide is a rebuilt HTML checklist handed over, not a chat message explaining what would
  change.

### This file never stores facts about a particular game

**No example in this skill names a real game, mission, character, achievement, or location, and
nothing learned while building one guide is written back here in those terms.** The skill is the
method; a game is the input. A lesson learned on one title gets recorded as the *pattern* that made
it fail — "an achievement whose enabling system stays inert until a mid-story mission switches it
on" — never as the title, the achievement name, or the mission that exposed it.

**Anonymizing the names is only half of it. An example also has to escape its genre.** Serial
numbers filed off a crime-sandbox example leave a crime-sandbox example: stolen police cars,
wanted levels, safehouses, districts, and stunt jumps still tell a reader building a roguelike,
a racing sim, a puzzle game, a fighting game, or a turn-based strategy campaign nothing they can
use — and worse, invite them to decide the step doesn't apply to their game at all. That is the
same defect as naming the title, arriving one level deeper.

So every example follows this shape:

- **State the mechanism first, in terms any game can have** — a system that is switched on later
  than the object that fronts it; a task whose fast method has prerequisites the task doesn't; a
  requirement that accrues on elapsed time rather than player action.
- **Then illustrate, and rotate the genre.** Where an illustration earns its place, prefer two or
  three short ones drawn from *different kinds of game* over a single long worked example from one.
  A reader should be able to find their own game's shape in at least one of them.
- **Write every illustration as an explicit hypothetical**, marked as invented — "say a game
  has…", "a hypothetical:", "picture a title where…" — or as a bracketed slot (`[the region that
  opens in Act 2]`) in sample guide text. Never as a flat assertion. An unmarked invented specific
  reads exactly like a researched fact, which is the failure this whole skill is built to prevent;
  a plausible detail stated plainly is indistinguishable from a verified one, and the next reader
  has no way to tell that "the enemy at the temple checkpoint" was made up to carry a point.
- **Check the spread across the file, not just within one section.** If most examples in this
  document could only occur in one genre, the file has drifted, regardless of how carefully each
  individual example was anonymized.

**Nothing in this file is a fact about any real game.** Every scenario, venue, enemy, item,
threshold, and mission number below is invented to illustrate a mechanism. None of it is research
output, none of it transfers to the game you are working on, and none of it may be reused as
though it were known — the game in front of you gets researched from scratch, every time, exactly
as Step 1 requires.

The rough spread to write against: open-world sandboxes, action-adventures, RPGs (western and
JRPG), shooters, roguelikes, racing games, platformers, fighting games, sports titles, strategy
and 4X, survival/crafting, sims and management games, puzzle games, rhythm games, visual novels,
live-service and multiplayer titles. Not every example needs to name one, but no example should
be *impossible* in most of them.

When adding to Key Lessons From Real Use, generalize *as you write the lesson*, not in a later
cleanup pass — both the names and the genre. The generalized version is also the more useful one:
it forces you to state which property of the situation caused the failure, which is the part that
transfers.

### The answers don't live here — the questions that produced them do

Every lesson in this file came from asking one specific question about one specific game, getting
an answer that contradicted what the guide already said, and fixing the guide. Removing the answers
is deliberate; **removing the questions would gut the skill.** So the questions are stated here as
standing work, to be asked again, from scratch, for the game in front of you.

They are not background reading. **Each one is a research task performed during generation** — in
Step 1 for most, and re-checked at the pre-presentation walk-through. None of them ever returns
"same as last time," which is exactly why the answers can't be cached in this file:

| Ask, of every… | The question | Wrong answer looks like |
| --- | --- | --- |
| item you're about to place in the earliest phase | Is the **system** behind this switched on yet, or is only the **object** present? | The thing is reachable from minute one, so it's Phase 1 — while the feature it fronts stays inert until a story beat |
| item you believe has no gate | What **evidence** says it's ungated? | "No trigger found," which is absence of evidence wearing the face of evidence of absence |
| non-trivial achievement | What is the community's **fast method**, and what does *that* method require? | Placing on the task's availability when the method is what's gated |
| item you're about to place anywhere | Which of the **five axes** — mission prerequisite, elapsed time, cyclic window, irreversible choice, trigger ownership — did you actually ask, and what did each return? | One confident answer on the loudest axis, read as clearance on all five |
| item you're about to route | Does the **player** initiate this, or does the **game**? | An arrival the game sends written as a place the player travels to, sitting inside a sweep |
| constraint you just researched | Is it on the **visible line**, or only in the note? | A window, a branch condition, or an unprompted trigger collapsed out of sight, met at the wrong hour with the wrong save |
| group you're about to put under one parent | Does **every member** share that gate, and that window? | One researched gate stretched over a category, and children inheriting a position none of them was checked for |
| item sitting next to its topical siblings | Where is **this one's** cheap method available, and has that window shut by here? | A category placed as a block, with the members whose shortcut expired quietly paying for the tidiness |
| dependency you just wrote into a line | Is this a **gate** (the mission comes first) or a **deadline** (the item comes first)? | Both directions written the same way in prose, and only the gate direction ever checked |
| availability fact you took from a walkthrough | Is there a **structured** source with this as a field — and do the guides agreeing on it have independent origins? | Four sources agreeing because all four are downstream of one, with the qualifier dropped somewhere in the retelling |
| method you've found | Does anything **later remove** it? | A start point recorded where the task actually has a window |
| location-dependent task | **Which** specific venue, level, or mode — and was it verified separately from the similar-looking one? | "Any bar," "any vendor," or two activities assumed to share a place because they're the same type |
| task needing an item | Is the best place to **acquire** it the same as the best place to **use** it? | One location named for both, because collapsing them read tidier |
| elapsed-time requirement | How **early** could this clock have been started? | A timer started at the line where its reward is collected |
| deep-read achievement | What does the top-voted solution say about **when** to do it? | A defensible-sounding placement that the community consensus contradicts, with no note explaining the difference |
| item you moved off a source's placement | What **evidence** made the source wrong — and does the note say so? | A relocation made out of caution, sitting afterwards where nothing distinguishes it from a researched one |
| finished guide | Does the **look** come from images of *this* entry, or from adjectives and franchise reputation? | A palette named and rationalized without ever viewing the game |
| count you researched | Does it **match** the walkthrough's stated count? | Two numbers that differ, averaged or ignored instead of resolved |
| set handed off to a map | Does anything about **when** these appear vary? | A complete, correct pin list backing a sweep the player can't finish yet |
| content category, one at a time | Does anything in **this category** advance on elapsed time? | One game-level "no timers here," with a dependent chain inside a category never questioned |
| source that supplied the **ordering** | Which of its timing claims did you verify **independently**? | A route transcribed from one voice, passing every later check against itself |
| source you couldn't read | **Which specific claims** now rest on something weaker, and does the player know? | "Some placements unverified" in a notes file, with the affected items unnamed |

The concrete findings these produce — the mission that switches on a system, the item that makes a
skill trick trivial, the venue for each minigame, the entry's real palette — are genuine research
output and worth keeping. **Keep them outside this file**: a per-game notes file, a memory entry,
whatever the environment offers. Two rules for that store:

- **It is an input to verify against, never a substitute for the research.** Games get patched,
  servers close, community consensus moves, and a cached answer is a claim of the same standing as
  a community guide's — useful as a starting point and a cross-check, not as ground truth. Treat a
  conflict between the notes and a live source the way Step 1 treats any source disagreement.
- **It never flows back into this file.** The skill takes the question; the notes take the answer.

---

## Step 1: Research the Game

Before writing anything, web-search for current, accurate information. Do not rely on training
data alone — achievement lists, missables, and exploit patching change over time.

**The standing questions in "The answers don't live here" above are part of this step**, not a
separate exercise: work the list for this game and record what each returns. If a per-game notes
file exists from an earlier session, read it now — as a starting point and a cross-check to
verify, never as a reason to skip a search.

Search for:
- Full achievement list with descriptions
- Missable achievements (anything tied to a specific mission, choice, or time window) — and not
  just story-mission missables. Check whether any long-term systems (relationships, reputations,
  companions) can be permanently lost through ordinary play (a bad interaction, a death, a
  decision) rather than only through a one-time story trigger. These are easy to miss because
  they don't show up in a simple achievement-list search; they surface in mechanic-specific or
  troubleshooting-focused searches instead (see Step 3).
- 100% completion requirements (story progress, collectibles, side content, repeatable activities,
  etc.) — enumerate every distinct category explicitly, not just the obvious ones. Side-activity
  systems are easy to under-count: a game can carry half a dozen distinct ones — a delivery job
  line, a contract board, an arena ladder, a fishing or farming system, a photo or research
  catalogue — that a completion-percentage source lists but a generic achievement-list source
  doesn't. Cross-check an authoritative "what counts toward 100%"
  breakdown against the achievement list — they are usually different sources, and content that
  matters for one can be totally absent from the other.
- **Which progress units run straight into the next one without handing control back**, and
  where the player ends up when control does return. A mission list looks like a list of
  separable entries; some of those boundaries don't exist in play, because one unit triggers the
  next directly — and the handoff often relocates the player or changes their loadout, party,
  vehicle, or access. The guide plans around the boundaries it can see, so a phantom one puts
  tasks in a gap the player never gets. Ask it of every boundary the route will place anything at
  (see the chaining section in Step 7); it's usually stated in passing in the same walkthrough
  and solution text already being read.
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
- **Which content the game initiates rather than the player** — anything delivered by a call, text,
  in-game email or letter, an ambient or random event, a visitor, a broadcast, an NPC who starts the
  conversation. The guide cannot schedule these, so what research has to return is different: not
  "where is the best place to do this" but **the earliest point it can arrive** and **what the
  arrival looks like**. This is invisible to an achievement-list search, because the description
  states the requirement and never who fires it; it is usually stated in passing in the same
  walkthrough and solution text already being read ("after mission X he'll ring you," "wait for the
  letter"). See the trigger-ownership axis in Step 7 for how these get routed.
- Known exploits or efficiency tricks (e.g., money/XP glitches, sequence breaks) — get the
  specific, verified method (exact target, exact button, exact condition), not a vague
  paraphrase. "Bet on horses" is not a method; "bet on the horse with the [specific marker],
  it has the worst odds, that's the point" is.
- Collectible counts per area/region (exact numbers, not approximations), and what reward each
  collectible category actually grants (cash, weapons, stat unlocks) — this often changes how
  early it's worth prioritizing them.
- Repeatable side activities, minigames, or optional content and what they unlock
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
- **The game's own visual identity — and you have to actually look at the game, not read about
  it.** This is a research target, not a thing to improvise at build time (see Visual Design under
  Output Format). Collect: the palette the game actually uses (HUD, menus, loading screens, key
  art, the setting's dominant colors), its typography (the logo's letterforms, the mission-title
  and stat-screen faces, and a Google Fonts pairing that evokes them), and any UI convention the
  game itself owns — a wanted-level star row, a radar disc, a mission-passed card, a stencilled
  crate, a handwritten journal page.

  **The mechanism matters here in a way it doesn't for the rest of Step 1.** Every other fact in
  this step is text and arrives correctly through a text search. A palette does not. Search
  results describe a game in adjectives, and an adjective is not a color — "gritty," "atmospheric,"
  "stylish," and "urban" all compress to the same dark-grey-plus-one-accent theme regardless of
  which game produced them, which is precisely how a guide ends up looking like every other guide.
  So: **view the game's screenshots and key art directly** — image search, the store page, a wiki's
  media gallery — and pull specific colors off what you see. **If you cannot view images in this
  environment, that is a limitation to state, not to route around**: say so and ask the player for
  a screenshot or for confirmation of the palette. Substituting a mood word for a color you never
  looked at is the same defect as inventing a mission number, and it fails the same way.
- Specific locations for location-dependent tasks (see "Add locations" under Output Format) —
  the exact venue, its neighborhood, and which candidate is best given where the player will be
  at that point in the route

Use at least 2-3 sources (achievement guides, wikis, community guides). Cross-reference counts
and missable details — sources often disagree. When sources genuinely disagree on a specific
number (a threshold, a cap, an exact count) and the disagreement can't be resolved, say so and
give the range or the safer/more conservative figure, rather than picking one source arbitrarily
and stating it as settled fact. **Count independent sources, not pages** — several guides
descended from one walkthrough are one source wearing three faces, and for availability facts
specifically a structured per-item table outranks all of them (see the section on reading the
table before the narrative, below).

### Use the deepest research surface available — and ask for it if it's off

Everything in this step is a multi-question, multi-source sweep: sixty-odd achievements, the
standing question list above, several sites that each answer a different part of it, and a pile of
counts to reconcile. That is exactly the shape a dedicated research mode is built for, and where
one exists it should be doing this work instead of a hand-rolled sequence of single searches.

**On Claude that mode is Research** (`support.claude.com/en/articles/11088861-use-research-on-claude`).
It runs many interconnected searches, decides what to look at next as it goes, and returns a cited
report in minutes. It's available on Pro, Max, Team and Enterprise plans, on the web, desktop and
mobile apps; the player switches it on with the **+** button at the bottom left of the chat and
selecting **Research**, and a blue indicator confirms it's active. Web search has to be enabled for
it to work at all.

Two things follow, and both of them are about *asking*:

- **It does not turn itself on, so prompt for it.** If a research mode is available and inactive,
  say so *before* starting the sweep rather than reporting it afterwards — and say both halves:
  what it buys here (per-achievement placement is the most search-heavy work in this skill, and the
  part most often cut short) and what it costs (it draws on the same usage limits and spends them
  faster, since it pulls many sources per question). Then let the player decide. A guide built
  without it is still held to every standard here; it just takes more turns to reach them.
- **Where there is no such mode, say so plainly and run the sweep by hand.** Claude Code sessions,
  API integrations, and other agents have no toggle to offer; there the sweep *is* the searches,
  fetches and browser reads specified through the rest of this step, performed explicitly. What is
  never acceptable is the third option: describing a single search as though it were a deep pass.
  That is the same fabrication this step's non-result rule exists to stop, aimed at your own
  process instead of at the game.

And two things a research mode does not change:

- **Its output is a source, not a verdict.** It gets the same treatment as any other source —
  cross-referenced against a second one, worked against the standing questions, and resolved rather
  than averaged where it conflicts. Its citations are the most useful thing it returns; follow them
  rather than trusting the summary written on top of them.
- **It does not automatically reach the sources this step depends on.** Read its citation list for
  the walkthrough overview and the per-achievement solution threads specifically. Anything absent
  is still owed, and the tracking sites that refuse automated fetches (below) are the likeliest
  gap — a research pass that couldn't read them will route around them to whatever it could read,
  and the report it produces looks complete either way. Open a browser pane for those.

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
- **The community placement is the default, and the burden of proof is on overriding it.** Reading
  a thread for its *mechanism* rather than its literal instruction is correct — but it creates a
  specific trap: you extract the principle ("the trick is the vehicle, not the mission"), apply the
  principle, and drop the fact that made the mission matter in the first place (the vehicle is
  hard to get any other way). The abstraction feels like insight and is actually loss of
  information. So: an override is only allowed on a **verified** reason. If your reason depends on
  a fact you have not checked — that an item spawns commonly, that a location is reachable, that an
  alternative is comparable — go and check it. If you cannot, **defer to the community placement**,
  because hundreds of people who finished the game landed on it and you have an untested hunch.
- **Hedging in the guide is not a substitute for verifying.** When you notice mid-reasoning that
  your placement rests on something unverified, the correct response is research, not a softening
  clause. Writing "if you can't find one, it's free later" launders your own uncertainty into the
  deliverable: the note reads as thorough, the guide looks researched, and the doubt has silently
  been transferred to the player, who is in the worst position to resolve it. A recorded reason
  built on an unchecked assumption is worse than no reason at all, precisely because it looks
  like diligence. If you catch yourself writing a hedge, that is the signal to open the source.
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

**Flagging it is where this used to stop, and flagging is not enough: a blocked primary source is
an open ticket, not a closed risk.** A line reading "couldn't reach the achievement site" records
that something went wrong and tells nobody what it cost — the affected placements then ship
looking exactly as confident as the verified ones, because nothing in the guide distinguishes
them. Four things actually close it out:

- **Escalate the tool before accepting the gap.** A block is a statement about one access path,
  not about the content, so exhaust the other paths first: a browser pane when a fetch tool
  failed, a different browser surface, the excerpt a search engine already has, a sibling site
  covering the same game (TrueTrophies, PlayStationTrophies, PowerPyx, a wiki that quotes the
  solution). Accepting the gap is the last move, never the first.
- **Name the specific claims that now rest on weaker sources.** Not "some placements are
  unverified" — the actual list, item by item: which achievements were going to be reconciled
  against that source, and what each one's placement currently rests on instead (your own
  inference, a secondary wiki, a count from a walkthrough page).
- **Surface that list to the person in your response, not only in a notes file.** A risk recorded
  where only the next builder will look has been filed, not communicated. The player is the one
  who can decide whether to accept a placement, check it themselves, or have you retry later, and
  they can only decide that if they know which items are affected.
- **Say what would resolve it.** "Re-run this when the site is reachable and these six placements
  get reconciled" turns a permanent-sounding limitation into a task with an owner.

The same treatment applies to any primary source that can't be read — a paywalled guide, a dead
wiki, a video whose transcript won't load, a map site that won't render. The failure mode never
changes: the gap gets logged somewhere that reads as diligence, and the claims resting on it are
indistinguishable from the researched ones by the time the guide is presented.

### Which achievement site, and start with the walkthrough

All of this is **supplemental to** the research already specified above, never a replacement for it.
Use whichever of these cover the game:

| Source | Use it for | Notes |
| --- | --- | --- |
| **TrueAchievements** | Xbox titles — the primary source | Two distinct surfaces: a structured game *walkthrough*, and per-achievement *solution threads*. Both matter, and they answer different questions. |
| **PowerPyx** | Modern multiplatform titles | Roadmap-style, often the entire game on one page, which makes it the cheapest read when it exists. Coverage skews recent — confirm the game is covered rather than assuming. |
| **PlayStationTrophies.org** | Anything with a PlayStation release | Trophy names map 1:1 to achievement names for the same game, so its guides transfer directly. Useful when TrueAchievements' solutions are thin. |

**Start with the TrueAchievements walkthrough overview. It is one read that plans every other
read.** The URL is standard per game: `trueachievements.com/game/<Game-Slug>/walkthrough`, where
the slug is the game's title in hyphenated title case.

**If that URL doesn't resolve, navigate to it rather than guessing again.** The slug is not
mechanically derivable from the title — subtitles and editions get dropped or reordered,
punctuation vanishes, and a Roman numeral is often silently converted to an Arabic digit (a title
ending `IV` becoming a slug ending `-4`) — so a 404 usually means the slug is wrong, not that
the walkthrough is missing (and per the status-code rule above, 404 means fix the URL, not switch
tools). The reliable path:

1. Open the game's achievement list page, `trueachievements.com/game/<Game-Slug>/achievements`.
2. If that slug is also wrong, search the web for the game plus "trueachievements" and follow any
   result onto the site — any page for the right game will do.
3. Use the game navigation bar at the top (*News · Forum · Clips · **Walkthrough** · Reviews ·
   Scores · DLC*) and follow the Walkthrough tab. That link carries the correct slug, which also
   gives you the right slug for every other page you'll need.

A game with no walkthrough is a real possibility — the tab will be absent or empty. That is a
genuine absence, not a broken URL: fall back to the achievement list plus per-achievement
solutions, and say the walkthrough wasn't available rather than silently skipping the cross-checks
it would have provided.

That single page returns:

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
  returns confident, plausible, wrong content. **Harvest every ID in one shot** rather than reading
  the page repeatedly: run a small script in the browser that maps achievement name to ID from the
  links, e.g. collect `href` matches of `/a<digits>/` with their link text into one object. That
  returns the whole game's ID table in a single compact result — every achievement on a 60-plus
  list in one object — and every later page is then a direct navigation.
- **Guide count is a second triage signal, and a good one.** Many guides means the community found
  the method contested or non-obvious and kept adding better ones; one or two means it is
  straightforward and the top solution will only confirm what you already know. Combine it with the
  type tags: a Collectable or Time Consuming achievement carrying nine guides is the strongest
  possible case for a deep read, while a Main Storyline achievement with two is the weakest.

### For availability data, read the table before the narrative

The sources above are mostly **prose**: a walkthrough page, a roadmap, a solution thread. Prose is
the right tool for *method* — the trick, the setup, the reason one approach beats another. It is
the wrong first stop for **availability**, which is the class of fact this skill spends most of its
effort on: unlock condition, time or weather window, prerequisites, rank or tier requirement,
which act or region something appears in.

**Where a wiki or database exposes per-item fields, read that table first.** Many games have one —
a wiki infobox with an "unlocked by" or "requires" row, a sortable list with availability columns,
a community database or tracker with per-entry prerequisites, an interactive map with per-pin
conditions, a datamined table. Two reasons it outranks the narrative version:

- **A field is answering the question directly.** A prose guide mentions availability only when the
  author happened to think it worth a sentence; a column has an entry for every row, so a blank is
  visible as a blank rather than hiding inside a paragraph that didn't come up.
- **Prose compresses and misremembers.** Writing a walkthrough means summarizing, and summarizing
  drops the qualifier — "available after the second act" is what "available after the second act,
  except the two in the northern zone" turns into by the third retelling. The exceptions are
  precisely what this skill needs, and they are the first thing prose loses.

**And agreement among prose sources is weak evidence when they share an ancestor.** The
cross-referencing rule in this step assumes independent sources; community guides frequently are
not. A wiki, three achievement guides, and a video description can all trace back to one original
walkthrough, and then "four sources agree" means one source said it four times. Consensus produced
that way is exactly as wrong as its ancestor and considerably more convincing.

So before treating agreement as confirmation, ask **whether these sources could have arrived at
this independently** — different authors, different eras, different methods of finding out
(datamining, a structured database, in-game testing, a first-hand playthrough) — and weight one
structured or first-hand source above several that read like each other. Where they *do* share an
ancestor, say so in the per-game notes: "three guides agree, all apparently downstream of the same
walkthrough" is a materially different confidence level from "three guides agree" and should never
be recorded as the second.

**None of this demotes solution threads, and the split is narrower than it first sounds.** A
structured source answers **when a thing is *available*** — the gate, the window, the prerequisite.
A solution thread answers **when it is *best*, and how** — which is a different question with a
different answer, and the thread remains the primary source for it, exactly as the solution-thread
section says. A table showing something is reachable in the opening act does not contradict a
top-voted solution saying to save it for later; the first is a constraint and the second is a
recommendation, and this skill routes on the second within the bounds of the first.

**Where they genuinely conflict on the fact — the table says a thing is gated and the thread says
do it before that gate — the structured field wins**, and this is the one place the
community-placement default in the solution-thread section does not apply. That default exists
because a thread's author finished the game and you didn't; it is about *judgment*, and it holds
completely for judgment. A gate is not judgment, it's a field, and the reason to prefer the field
is the compression problem above: prose states availability only in passing and sheds the qualifier
first, so a thread saying "do it in the opening act" is usually reporting where its author did it,
not asserting that nothing gates it. Resolve and record the disagreement like any other conflict —
name both sources and which won — rather than averaging them or quietly dropping one.

### A source shaped like the deliverable will silently replace the research

The most useful sources in the list above — a walkthrough's ordered story pages, a roadmap-style
guide covering the whole game in phases, a community "optimal route" post — arrive already in the
shape of the thing you are building. That is exactly what makes them hazardous. When a single
source supplies the ordering, the work collapses from research into transcription: the route gets
copied, every later check in this skill runs against the copy rather than against the game, and
the guide inherits both that source's coverage and its blind spots without ever registering that
it did.

Three mechanisms, none of which require the source to be bad:

- **Format carries authority its sourcing hasn't earned.** A numbered, ordered checklist reads as
  settled. The identical claim as prose in a forum post reads as one person's opinion and gets
  checked. Nothing about the numbering makes it more verified.
- **One voice produces no disagreements to surface.** The cross-referencing rule above works by
  catching sources that conflict. A single spine source cannot conflict with itself, so the whole
  mechanism reports clean while doing no work.
- **An ordered list encodes timing implicitly and never states it.** Position *is* the claim. If
  an item sits where it sits because of a story gate, an elapsed-time window, or a method that
  only exists later, the list shows the consequence of that gate and never the gate itself — so
  the reason can't be checked, can't be written into a note, and vanishes the moment anything
  reorders.

So: **when one source supplies the ordering, name it as the spine** — in the per-game notes, and
in the guide's own text wherever the ordering is load-bearing — and then **deliberately verify a
sample of its claims against independent sources.** Not a spot-check of whatever is cheapest to
confirm. **Weight the sample toward claims about timing and availability**, since those are the
ones the format hides: draw items from across the whole route rather than the opening, and include
at least one the spine places surprisingly early and one it places surprisingly late. Resolve any
disagreement the way Step 1 resolves every other source conflict. A clean sample means the spine
has earned its position; a dirty one has just shown you the class of error it was about to
propagate through every phase.

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
- **You believe it has no gate at all and you're about to place it early.** "Ungated" is the
  highest-confidence claim a guide makes and the least-evidenced one: no source ever *asserts* that
  an achievement is ungated, so the belief is only ever formed by failing to find a gate. That is
  absence of evidence wearing the face of evidence of absence — and it is the specific belief that
  puts items in Phase 1. The solution thread is where the gate actually gets stated, and it is
  usually the thread's **first sentence**, before any technique advice ("after you complete X you'll
  have access to Y"), which makes this the cheapest read on the whole list.

**Then split the deep-read candidates by what the open question actually is**, because half of
them are asking something a solution thread is the wrong tool for:

- **"Where are they?" — location and collectible enumeration.** Hidden pickups, audio logs,
  shrines, chests, landmarks, race gates, lore notes: any set scattered across a map or a set of
  levels. Do **not** spend
  achievement-page reads on these. What you need is an exhaustive location list, and that lives in
  a dedicated interactive map (MapGenie and its equivalents) or a wiki with map data — sources
  built for exactly this and far better at it than a prose solution. More importantly, **locations
  are not what the guide is supposed to supply.** Point the player at the map tool for the pins,
  and spend your own effort on the thing no map can do: **routing** — which members of the set are
  reachable in the area the player is standing in *right now*, so they sweep them while they're
  there instead of driving back later. That is per-phase reachable counts and area grouping
  (Step 6 and ordering principles 3 and 4), not coordinates.
- **"How and when?" — technique and efficiency.** Grinds, minigames, skill challenges, timed or
  counted tasks, repeatable side jobs, anything with a trick. Here the solution thread is exactly
  the right tool and a map is useless, because the answer is a *method*, not a coordinate: summon
  the vehicle instead of hunting for one, pick the easy variant of the job, use the equipment that
  cannot fail, exploit the spot where the crowd fights back.

The tell is simple: if knowing every location would finish the achievement, it's a map problem;
if you could know every location and still do it slowly and badly, it's a solution-thread problem.
On an open-world game this roughly halves the deep-read list, and it stops the guide from
reimplementing a map site badly inside collapsed notes.

**Triage is not one-way — a category routed to a map tool still owes the timing question.**
"Where are they" and "when do they become available" are independent questions, and answering the
first does not retire the second. A set can be exhaustively mapped — every pin placed, every count
confirmed — and still be gated: on elapsed time, on story progress, on a time-of-day or weather
window, on a rank or difficulty tier, on a faction state. A map answers none of that, because a
map is a spatial index and availability is a temporal fact. The failure is quiet and total: the
guide sends the player to sweep a set with a complete, correct list of locations, and a share of
them simply aren't there yet.

So **every category triaged out to a map, tracker, or other external tool gets one more question
before it leaves the deep-read list: does anything about *when* these appear vary?** If yes, it
re-enters the list **for timing only** — not for locations, which the map still owns. That read is
narrow and cheap, because you are not looking for where the items are; you are looking for the one
sentence saying some of them only show up after something else.

Hypothetical shapes, all invented, spread deliberately across genres: a collectible set where a
handful only spawn at night; a set whose last few only appear once a faction stops being hostile;
a photo or research catalogue whose subjects migrate by season; a set of race gates that only
populate once a vehicle class is unlocked; a shrine or challenge set with a subset walled off
until a chapter turns over; a card or unit collection where some entries only drop from an
end-game mode. In every one, the map is correct and a sweep instruction built on it is still
wrong.

On a 60-70 achievement list this typically leaves 15-25 warranting a deep read, and the split
above cuts the number of *solution threads* well below that. **Record which achievements you
triaged out and why** — including the timing answer for anything sent to a map — so a later pass
extends the work instead of repeating it, and so a wrong triage call is auditable rather than
invisible.

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

Common shapes, across genres:
- A repeatable side activity whose completion tiers hand over a permanent buff — infinite sprint,
  fire resistance, an armor or damage tier, a carry-capacity increase
- Collectible sets that unlock gear, abilities, or a base upgrade once a threshold is reached
- An early exploit, contract, or investment that generates outsized money, XP, or resources
- A minigame, trial, or training mode granting a permanent stat boost
- A perk, relic, or relationship that reduces the cost of death or failure (keeping your items on
  death, a free revive, a retry that doesn't reset the run) — worth calling out specifically
  before the guide's most punishing stretch, not "whenever you get around to it"
- Traversal and access unlocks that shrink every later trip: a double jump or grapple in a
  platformer, a mount or fast-travel network in an RPG, a better ship or engine in a space or
  racing game
- Anything that lowers the difficulty of a *later* achievement: a gear tier that trivializes a
  hard-mode run, an XP or loot multiplier, a practice or training mode that makes a demanding
  skill achievement cheaper to attempt, a unit or card that breaks a strategy game's mid-game

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
  standard workaround (often: resting, saving, or returning to a hub to roll the cooldown over)
  instead of letting the player assume one long session will finish it.
- **Does anything resolve on something other than the player doing it right now?** Elapsed time
  is the obvious case — in-game days passing, a business or property accruing income, a
  build/craft/crop timer, a stock price moving, a relationship cooling off, a real-time cooldown,
  a vehicle or spawn refreshing — but **the question is broader than clocks, and phrasing it as
  "does anything advance on elapsed time" is what makes the rest invisible.** Also count: a
  message, letter, call, or in-game email that arrives after a trigger; an activity, encounter,
  contact, or visitor that has to *fire* before it can be done; anything gated on a counter of
  missions, wins, levels, or purchases rather than on days; a vendor restock or job board that
  rolls over; a daily or weekly reset on a real-world clock; an unlock that only appears at the
  next sign-in or server sync; something that only changes the next time the player sleeps, saves,
  reloads, or re-enters an area. None of these are tasks — they are **pending outcomes**, and the
  sequencing question that matters is **how early the pending state can be created**, researched
  to the same evidence standard as any other fact. Started at its earliest legal point it is free;
  started where its reward gets collected it costs the player the entire wait. **Then establish
  what actually advances it** — time alone, progress the player is making anyway, or one specific
  action they must take — because that decides whether the route can absorb the wait or has to
  perform something. **And establish who collects it**: several of the shapes above are things the
  game brings to the player rather than things the player goes and gets, which changes where the
  line can sit at all rather than merely where it is cheapest (trigger ownership, Step 7). **And check whether they are independent or chained**: several can be pending
  at once, but a sequence where each step is gated on the *previous* one (visit an NPC, wait,
  visit again, wait, visit again) can't be parallelized at all — it needs the route rearranged
  around it instead. Establish how many links the chain has and what each gap needs, because
  that's what the route has to fill. See the dedicated section in Step 7 for how all of these get
  written into the route.

  **Ask this question per content category, never once for the whole game.** Asked at the game
  level it invites a single answer, and the answer is
  whichever clock is most visible — an income property, a crop, a research bar — after which the
  question feels answered and the search stops. So enumerate the game's content categories first,
  then ask it of each one separately: the progress line; every side activity, one at a time; every
  collectible set; relationships, companions, and factions; encounters, spawns, and enemy
  populations; unlocks, upgrades, and crafting; vendors, stock, and the economy; and anything the
  100%-requirements breakdown from Step 1 lists that none of those cover. Where the game has
  several instances of a category — four contract boards, three trainers, six shops — the question
  is asked of the category, and any instance that behaves differently is its own answer.

  The failure shape this prevents is specific: a game with no obvious economy timers reads as "no
  timers at all," while a dependent chain sits inside a category nobody ever questioned
  individually — a relationship that only deepens between in-game days, a vendor whose stock rolls
  over on a schedule, a repeatable job that only re-offers once a period passes, a set of
  encounters that fire at a fixed rate. Those are the expensive ones, because a chain discovered
  late can't be fixed by starting a clock early (see the dependent-chain section in Step 7) — the
  route has to be rearranged around it, which is cheap while the route is still being drafted and
  expensive afterwards.
- **Does the order in which the player acquires protective perks matter** relative to the
  riskiest, most failure-prone stretch of the game? If a perk mitigates death/failure
  consequences, place the acquisition of that perk immediately before the section it protects,
  not as a passing mention somewhere earlier.
- **Is the best place to *acquire* what a task needs different from the best place to *do* the
  task?** The two questions look like one and routinely have different answers: the spot that
  makes an activity fastest (a quiet area, dense objective spawns, a forgiving arena) is often not
  where the required vehicle, weapon, tool, mount, ingredient, or unit is obtained. Verify both
  independently — don't assume the item is found where the task is easiest, and don't organize the
  route around wherever the item first becomes available. Place the task at its best **completion**
  location and fold the acquisition into that same step as a "get it from X, bring it here"
  instruction. If the fetch itself is risky — a fragile item that breaks, an escort that can die, a
  consumable you only get one of, a long trip through hostile territory — say so and name the
  specific hazard rather than "and then bring it over."

This step is what separates "a list of true facts about the game" from "a list of true facts in
an order that actually helps." When in doubt, ask: if the player does these two things in the
order I've written, does the second one cost more, less, or the same as it would the other way
around? If the answer is "more," the order is wrong.

---

## Step 6: Identify Area-Gated Content

Most games lock some content behind progression. **"Area" here means whatever slice of a game can
become temporarily or permanently unreachable** — a region of an open map, a chapter or act, a
level select entry, a difficulty tier, a character or class you haven't recruited, a faction path
you didn't take, a multiplayer playlist, a post-game dungeon, a New Game+ exclusive. Before writing
the route, determine:

- What is accessible from the start vs. what requires progress to unlock
- Which collectibles, challenges, or side content are physically blocked early — behind a locked
  region, a traversal ability you don't have, a level you can't yet select, a rank you haven't hit
- Which activities require something that itself only exists later: a vehicle, a key item, a
  companion, an unlocked loadout, a crafting tier, a party member with a specific skill
- Where the point-of-no-return cutoffs are, and what becomes unreachable past each

**Do not tell the player to sweep areas they cannot fully access yet.** Only instruct a
collectible or content sweep once the player has full access. If access is partial, state exactly
what is and is not reachable.

For example: "There are X collectibles in this area. Y are reachable now. The remaining Z need the
grapple upgrade / a story unlock / a specific companion — come back for those in Phase N."

This was a key clarification from real use: telling a player to sweep a whole region's collectibles
at the start of the game is wrong, because a share of them are behind abilities or access they
don't have yet — the same error as pointing a player at every level's hidden items before the level
select is populated. Always ground sweeps in what is actually reachable at that point in the route.

---

## Step 7: Build the Phased Route

**Before writing the route, do a research pass aimed specifically at the *sequence* — not just
individual facts.** Step 1 verifies that facts (achievement triggers, counts, mechanics) are
accurate; this is a separate check on whether the *order* you're about to present is the
order the game actually unlocks things in. Search for the game's mission list or story
progression specifically (e.g., "[game] mission order," "[game] walkthrough chapter list") and
confirm which mission unlocks which region/vehicle/side-content before asserting it — a chain
of individually-true facts can still describe a false sequence if two of them are reversed.
**The same pass establishes where the seams in that sequence actually are** — which entries the
game runs back to back without returning control, and where the player is standing afterwards —
because the route may only place work at real seams (see the chaining section below).
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
what unlocked it ("opened up by the Phase 1 mission that unlocked [the workshop]"). The
unlock relationship is
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
13. **Waiting is never a step — and a wait is not only a clock.** Anything the player has to
    wait *for* — elapsed in-game time, a message or call arriving, an activity or encounter that
    has to trigger, a counter of missions or wins, a restock or reset, a next-sign-in unlock —
    gets started at the earliest point the route allows and then resolves *underneath* the rest
    of the route. Where a chain of steps is gated on the one before it, nothing can start
    earlier, so the links get interleaved into the route with real work between them, never
    written out as a contiguous block. The player is never parked waiting, and two waits never
    sit next to each other — see the dedicated section below.
14. **Nothing goes between two units the game runs back to back.** A gap on the page is not a
    gap in the game: where one mission, chapter, race, or level hands straight off to the next
    without returning control, the player cannot act between them, and the handoff frequently
    moves them somewhere else as well. Verify that control actually returns at any boundary the
    route places something at — see the dedicated section below.
15. **Enumerate all five dependency axes before placing anything** — mission prerequisite, elapsed
    time since a prior step, time-of-day or cyclic window, irreversible choice, trigger ownership.
    They are independent, and satisfying one does not make an item placeable. Record each
    explicitly, including the empty ones — see the dedicated section below.
16. **A bundle claims a shared gate.** Putting several items under one parent asserts that every
    member shares that parent's unlock condition *and* its availability window, because children
    inherit the parent's position. Gates are checked per item, never per category. Where the
    members' gates differ, the bundle splits and the category label survives in a note — see the
    dedicated section below.
17. **Cheapest, not tidiest.** An item goes where its own method is cheapest, never where it
    thematically belongs. Topical clustering is what writing does by default, and it routes an item
    to its *category's* position rather than its own — see the dedicated section below. This is not
    principle 4: grouping by area is about one physical trip the player is already making;
    grouping by topic is about the writer's outline and saves nobody anything.
18. **The route may only schedule what the player triggers.** Content the *game* initiates — a
    call, a text, an email, an ambient event, a visitor — arrives on its own schedule and cannot be
    put anywhere by the guide. It goes at the earliest point it can arrive, says on its line that it
    comes unprompted, and never sits inside a sweep or a batch, because a sweep is a plan the player
    executes — see the trigger-ownership axis below.
19. **A constraint belongs on the visible line.** Anything that decides whether an attempt can
    succeed at all — a window, a branch condition, an unprompted trigger, a closing deadline — is
    visible without expanding anything. Notes carry method and reasoning; they never carry the
    thing that determines whether the player is even able to do this — see the dedicated section
    below.

### Bundled missions get their own sub-list, never a parenthetical

This is a specific, easy-to-violate case of the granularity principle above, worth spelling out
on its own because it's the anti-pattern that recurs most often:

**Wrong:** a single line reading `Play missions 7 through 17`, followed by all eleven mission
titles crammed into a parenthetical on that same line.

This puts eleven distinct missions into one checkbox. The player can only check off "did the whole
stretch" as one lump action, there's no way to track partial progress through it, and a long
parenthetical is harder to scan than a short list.

**Right:** the parent line states only the range (`Play missions 7 through 17.`), and each
mission gets its own child row nested underneath it, named in full, one per line, each its own
checkbox. The parent collapses them visually (collapsed by default with a small toggle to expand),
but each is independently checkable.

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

### A bundle is an assertion that every member shares one gate

The sub-list rule is about *granularity* — a bundle's children each get their own checkbox instead
of being crammed into a parenthetical. It says nothing about *where the bundle sits*, and that gap
is where bundling does its damage, because the two feel like one decision and are not.

**Children inherit the parent's position in the route.** So putting several items under one parent
is not a display choice; it is a claim about all of them at once — that every member shares the
parent's unlock condition **and** the parent's availability window. Nesting an item is placing it.
**A sub-list does not fix placement, it hides it**: the children are now individually checkable and
collectively mis-routed, and the structure reads as more carefully organized than the loose version
it replaced.

**So gate-check per item, never per category.** The pull runs the other way — a category is the
natural unit to research ("when do the contract boards open?", "when can I start the arena
ladder?"), it returns one clean answer, and that answer then gets applied to every member. One gate
was verified and a dozen placements were made from it. The members that don't share it fail
silently, because nothing in a tidy sub-list distinguishes a researched position from an inherited
one.

Invented shapes, deliberately across genres: a set of side jobs from one board where the last two
only appear at a later rank; an arena ladder whose top tier needs a qualification the rest don't; a
crafting category where one recipe needs a tool the others don't; a collectible set where a handful
of members sit in an area that opens two acts later; a roster of optional characters where one is
recruited from content the others have nothing to do with. In every case the category has an honest
answer and some member of it doesn't match.

**Categories are for the reader's comprehension. The route is built from gates.** A category name is
a fine label and never a placement. Concretely:

- **Group only on a verified match** — same unlock condition, same window. Not same type, same
  reward, same source page, same name prefix.
- **Where members diverge, the bundle splits.** Each item goes where its own gate and its own window
  put it, and the category relationship survives the way every other out-of-position relationship
  does: in a note that names the category, never a position (see the positional-cross-reference
  rule).
- **A split category owes a stated count.** If four of six members are here and two are later, say
  so on the line and give the later two real steps, or it's an orphaned deferral.
- **The connecting-line bundle is the safe case, and only because it's already gate-checked**: a run
  of consecutive missions the player does back to back shares a gate by construction. That is why
  mission bundling works and why extending the same structure to a *topic* does not.

### Missions that chain automatically — a gap on the page is not a gap in the game

A mission list is a list of *entries*, and the guide silently assumes each entry ends by handing
control back to a player standing where they started. Plenty don't. A unit that runs straight into
the next one — the end of one triggering the start of the next with no player action in between —
produces a boundary that exists in the source's numbering and nowhere in play.

**Anything the guide places at that boundary is not mis-ordered, it is unexecutable.** The player
reads the line, has no control to act on it, and by the time control returns the situation has
changed. This fails a level below every check in this skill: the item is accurate, correctly
researched, and correctly gated, and it still cannot be done where it sits.

Two distinct costs, and the second is the one that gets missed:

- **No window.** There is no moment between the two units in which to do anything at all.
- **A different world on the other side.** An automatic handoff routinely *relocates* the player
  — a new hub, a new region, a one-way transition — and often changes their state as well: a
  stripped or swapped loadout, a lost vehicle or mount, a split party, a different time of day or
  season, an altered faction or alert state, a previous area closed behind them. So content the
  guide grouped as "while you're here, also do these" was reachable when it was written and isn't
  once the chain fires. The player doesn't just lose the gap — they lose the hub the gap
  belonged to.

Invented shapes, deliberately across genres: a race that loads the next event of its series on the
results screen; a chapter whose closing cutscene rolls directly into the next level with a
different loadout; a quest whose turn-in immediately opens the next one and moves the party to
another town; an arcade ladder that advances opponent to opponent; a campaign turn that ends by
jumping to the next season with the map redrawn.

**Research it as a property of the boundary, not of the mission.** For every mission boundary the
route places something at, confirm control actually returns there and note where the player is
standing when it does. **A page break in a walkthrough is not evidence of a control seam** — it's
an authoring convenience, and it is exactly what creates the phantom gap in the first place. The
information is cheap to get once you ask: walkthroughs and solution threads mention it in passing
("this leads straight into…", "you'll be taken to…", "you can't return here afterwards"), and it
sits in the same sentences already being read for placement advice.

Then write it into the route:

- **Chained units are one uninterrupted block.** Nothing is inserted between them — no side
  content, no collectible sweep, no timer start, no shopping trip, no "grab these while you're
  nearby." Use the existing bundling mechanic: a parent line covering the chain, each unit as its
  own child row.
- **Say it on the line before the chain begins**, where the player can still act on it: this runs
  straight into the next mission, control doesn't return until it ends, and here is where you'll be
  standing when it does. A player who expects a break will otherwise stop mid-chain planning to do
  the errands the guide listed.
- **Displaced content moves to the last real control seam before the chain, or to after it ends** —
  whichever is genuinely better, judged the normal way. But when the chain closes access to where
  that content lives, the pre-chain placement is not a preference, it's the only option, and the
  closing edge gets flagged on the item *and* on the line that starts the chain, the same as a
  method window or a missable.
- **Break the "while you're here" grouping at the chain.** Area-based clustering (ordering
  principle 4) is only valid within a stretch where the player stays put; a chain that relocates
  them ends the cluster, and what used to be one trip is now two.
- **A warning that must be acted on before the chain goes on the pre-chain line**, never on a unit
  inside it — the same rule as a child reminder having to make sense after its parent, since advice
  the player reaches only after losing control is advice they cannot use.

### Five dependency axes — satisfying one does not make an item placeable

Placement gets treated as one question with one answer: *what does this need?* It is five questions,
and they are independent. An item is placeable at a point only when **all five** are satisfied
there, and each has its own evidence, its own failure mode, and its own detailed treatment further
into this step.

| Axis | The question | Where it's handled |
| --- | --- | --- |
| **1. Mission prerequisite** | Which progress unit must have happened first — and is the *system* running, not just the object present? | The burden-of-proof and dependency-direction rules |
| **2. Elapsed time since a prior step** | How much has to pass — or what has to resolve — since the step that started this, and does real work sit in that gap? | The waiting and dependent-chain rules |
| **3. Time-of-day or cyclic window** | Does this only work at a particular time, in particular weather, in a season, on a reset cycle? | This section, plus the timing question in triage |
| **4. Irreversible choice** | Does a branch already taken close this, or does a branch still ahead close it? | This section, plus missables and the deadline direction |
| **5. Trigger ownership** | Does the **player** initiate this, or does the **game**? | This section — it decides whether the item can be routed at all |

**Satisfying one axis reads as clearance, and that is the whole bug.** Research returns a confident
answer on whichever axis is loudest — usually the mission prerequisite, because it is the one every
source states — the question feels answered, and the item gets placed. The other four are never
asked. This is the same failure shape as asking the pending-outcome question once for the whole
game: a clean answer to a narrower question retires a broader one.

**Axis 5 is asked first, because it decides whether the other four are even a placement question.**
Axes 1 through 4 all assume the guide gets to choose where an item goes and the player then executes
it there. Where the game owns the trigger, that assumption is false before any of them are asked,
and the answers they return describe a position the route cannot actually put the player in.

**Three clarifications before the axes are usable**, all of which this file has been burned by
before:

- **Axis 2 is not only clocks.** "Elapsed time" is its most visible form and its worst label — the
  waiting rules were originally written about clocks and everything else that leaves a task pending
  sailed straight through. Axis 2 covers every pending outcome: a message or call that has to
  arrive, an encounter that has to fire, a counter of missions or wins, a restock, an unlock that
  lands at the next sign-in. Ask it in the broad form the waiting section specifies, or this axis
  will be answered for timers only.
- **Axes 2 and 3 overlap unless you draw the line, and an unshared boundary means both get skipped
  as "handled by the other."** The split: **axis 2 moves forward once** — something the player
  caused is resolving, and when it resolves it stays resolved. **Axis 3 comes around again** — a
  state the world enters and leaves on its own cycle regardless of anything the player did, and
  missing it means waiting for the next one. A build or research timer is axis 2. Nightfall,
  weather, a season, a weekly rotation is axis 3. A daily reset is axis 3 even though it involves a
  clock, because it recurs.
- **Axes 2 and 5 also overlap, and the same unshared-boundary rule applies.** Axis 2 asks **when**
  the thing becomes ready. Axis 5 asks **who acts** once it is. They are orthogonal and both get
  asked: a build timer is axis 2 with the player owning the trigger (they go and collect it); a call
  that arrives three missions later is axis 2 *and* game-owned. Answering "it's a pending outcome,
  the waiting section covers it" retires axis 5 without asking it — and the waiting section places
  the collection line wherever the player is next nearby, which is precisely the wrong answer for
  something that finds the player rather than being found.

With that settled: axes 1 and 2 are covered in depth elsewhere in this step. The other three are the
ones with no home until now:

**Axis 3 — a cyclic window is not a progress gate, and every progress-shaped check is blind to
it.** Night, dawn, a weather state, a season, a day of the week, a real-world daily or weekly
reset: the player can be perfectly progressed, standing in exactly the right place, with every
prerequisite met, and still unable to do the thing. It does not resolve by advancing the route,
which is precisely why it survives a route audit — the item is correctly ordered and still fails.
Invented shapes across genres: an encounter that only appears after dark; a subject that only
migrates through in one season; a vendor stocking the needed part only on a particular in-game
weekday; a fishing or foraging entry tied to weather; a mode or playlist that only runs on a
weekend rotation. Two things every item on this axis owes, on the line: **the window itself**, and
**the game's own fastest way to reach it** — sleeping, resting, a wait-until control, a clock or
weather item, a fast-travel leg that advances time. A window stated with no mechanism is the same
defect as "wait a few in-game days." And per the waiting section, that mechanism is a **checkbox**
when the player has to perform it: the window is a state and gets no box, the act of reaching it is
a task and does.

**Axis 4 — an irreversible choice constrains placement in both directions.** A branch already taken
can make an item impossible; a branch still ahead can be the deadline it has to precede. Faction or
route commitments, an NPC killed or spared, a one-shot consumable spent, a difficulty or build
locked in, a resource permanently allocated, a relationship closed off. Two distinct constraints,
and the second is the one that gets missed because it points backwards: **this item must be done
before the choice**, which makes it a deadline under the direction rule, not a prerequisite. Where a
choice makes an item impossible on this save at all, that is a missable and belongs in the missables
box; where it merely forecloses the cheap method, it's a closing window.

**Axis 5 — trigger ownership decides whether an item can be routed at all.** Everything else in this
step is about *choosing* where an item goes. This axis asks whether the choice exists. Two kinds of
content:

- **Player-initiated.** The player walks somewhere, opens something, starts something. The guide
  picks the point; the player executes it there. Every other rule in this step applies normally.
- **Game-initiated.** The game reaches out on its own schedule — a phone call, a text, an in-game
  email or letter, an ambient event, a random encounter, a visitor who turns up, a broadcast, an
  NPC who initiates a conversation, a drop-in invasion or contract offer. **The guide cannot
  schedule it.** It fires when the game decides, and no line in a checklist changes that.

The failure is not that game-initiated content is hard to place. It is that it gets written as
though it were player-initiated, and the two are indistinguishable once the line is on the page: an
imperative verb and a destination. The player reads "go meet [the contact] at [the venue]," travels
there, and nothing happens — because the actual mechanic is that the contact calls *them*, at a time
the guide has no say over. The item is accurately researched, correctly gated on every other axis,
and unexecutable, which is the same class of defect as placing work inside an automatic mission
chain.

**The tell is a note that contradicts its own line's framing:** a collapsed note saying the game
reaches out — "she'll call you once…", "you'll get a text when…", "an email arrives after…" — sitting
under an item positioned and phrased as though the player travels to it. The research was done, it
landed in the note, and the line was written from the outline instead. Whenever a note says the game
initiates, the line is wrong until it says so too.

Three rules, and they replace the normal placement machinery rather than supplementing it:

- **Place it at the earliest point it can arrive**, not where its payoff is collected and not where
  its topic sits. This is the axis-2 start-condition rule with the collection half removed: there is
  no cheapest point to choose, because the player is not choosing. Research the earliest trigger —
  the mission, the counter, the elapsed period, the prior conversation — and put the line there, so
  the player knows to expect it from that point onward rather than being surprised by it forty items
  later.
- **Say on the line that it arrives unprompted**, and say through what — a phone, a mailbox, a
  notification, an event popup, an NPC approaching. This is the arrival signal the waiting section
  requires, promoted to the visible line, because here it is not context about a task: it *is* the
  task's mechanics. A player who thinks they have to go somewhere will go there.
- **Never put it inside a sweep or a batch.** A sweep is a plan the player executes — "clear these
  six while you're in the area" — and an item nobody can execute on demand does not belong in one.
  It also cannot join an area cluster under ordering principle 4, because it is not part of a trip.

**The checkbox is the player's response, not the arrival**, which is the wait rule applied to this
axis: the arrival is a state and gets no box, responding to it is a task and gets one. So this is
normally a single line — "[do the thing] when [the contact] calls; the call comes unprompted once
[the trigger], not from any board" — sitting at the earliest point the call can come. Split it into
two lines only when the response is genuinely separable and lands much later, in which case the
arrival is a phase note rather than a checkbox and the response carries a back-pointer to it.

Invented shapes, deliberately across genres: a contact who rings once a mission count is passed and
offers a job that never appears on any board; a letter that turns up in a hub's mailbox some days
after a favor; a rival who challenges the player on their own schedule between events; a wandering
merchant who appears at camp unbidden; a distress signal that broadcasts while the player is doing
something else; a recurring in-engine event that fires on the world's clock, not the player's. In
every one, a guide can say *what to do when it happens* and *how early it can happen*, and cannot
say *do this now*.

**Record all five explicitly per item, including the ones that come back empty.** "No time-of-day
constraint" recorded is a checkable claim; the same fact unrecorded is indistinguishable from never
having asked — which is the ungated-is-a-claim rule applied to the other four axes.

**The record has three homes, and knowing which is which is what keeps it both affordable and
usable:**

- **The per-game notes store takes all five axes for every item, empties included.** That is the
  audit trail — what a re-research pass, a later edit round, or a re-run against a newly reachable
  source checks against. It is build-time material and never ships.
- **The visible line in the artifact carries every non-empty axis**, because a constraint decides
  whether the attempt can succeed at all and the player has to meet it without expanding anything
  (see the visible-line rule in Output Format). The window, the branch condition, the unprompted
  arrival, the deadline: on the line.
- **The item's note carries the method and the reasoning** — how to reach the window fastest, why
  the placement is what it is, what the source said. Never the constraint itself.

Empty axes go to the store and nowhere else. Five lines of "no branch dependency; no cyclic window"
on each of several hundred items is noise the player never needs, and it breaks the content-depth
standard's bargain that a note earns its collapse by being context rather than clutter. But the
empty answers still have to be *written down somewhere*, because "we checked and there's nothing"
and "nobody asked" are the same shape when neither is recorded. The store is where they live.

**Check mechanically wherever the shape allows** — see the checker suite in Output Format, which
turns the following into runnable assertions rather than reminders. Axis 1 is the
dependency-direction script. Axis 2 is countable: count the real steps sitting in each gap rather
than assuming they add up. Axes 3, 4 and 5 cannot be proven from the route alone, but each is
*declarable*, and a declaration is machine-checkable: every item carrying a cyclic window states its
window and its mechanism, every item touching a branch names the branch and its direction, and every
game-initiated item is marked unprompted and sits in no sweep.

### "Ungated" is a claim — the first phase carries the same burden of proof as the last

The cleanup audit below demands per-item research for everything sitting at the *end* of the route,
on the reasoning that a catch-all phase collects whatever nobody checked. That reasoning applies
just as exactly to the *front* of the route, and there has been no matching audit there. **Phase 1
is the other catch-all.** Anything the guide believes has no gate lands in it, and the belief that
something has no gate is never the product of research — no achievement list, walkthrough, or wiki
page ever states that a task is ungated. It is only ever arrived at by not finding a gate, which is
indistinguishable from not looking.

So the front of the route gets the same treatment as the back:

**Every item in the earliest phase must name, in its note, either the specific mission or event
that turns it on, or the verified fact that nothing does.** "No trigger found" is not the second
one. An unexplained early item is exactly as unresearched as an unexplained late one, and it fails
worse: a late item the player could have done earlier costs a detour, while an early item the game
hasn't switched on yet costs the player a session of trying to do something impossible and
concluding the guide is wrong.

**The trap is that the object exists before the feature does.** A gate does not have to look like a
locked door. The thing the task needs is often physically present, reachable, and interactable from
the first hour while the function it provides is simply switched off until a story beat flips it —
and every check in this skill that verifies *the thing is there* will pass.

The shape recurs in every genre, and always the same way. Hypothetical cases, all invented: a
crafting bench you can stand at that accepts no recipes until a story beat teaches you one; a
contract board that renders empty until you join the faction; a vendor whose interesting stock is
flagged out until a chapter turns over; a fast-travel map you can open but not travel from; a
challenge menu whose entries all read "locked" without saying why; a multiplayer playlist visible
but unpopulated until a campaign rank; a terminal or scanner built into a common vehicle whose
backing database is inert. In each, the object is there and the system behind it is not.

Ask of every early item not "can the player reach it?" but **"is the system behind it running
yet?"** — they are different questions, and only the first one is easy to check. The first is what
a location or item lookup answers, which is exactly why the second one gets skipped.

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

A hypothetical, to fix the shape — invented, like every example here. Say an achievement asks for
50 perfect parries. It has no gate whatsoever: the player can parry the first enemy in the
tutorial. But say the method that makes it quick is one enemy type that telegraphs slowly and
respawns indefinitely next to a checkpoint, and that enemy first appears in a mid-game zone.
Placed "as early as possible," the item lands in the opening hours and asks the player to grind 50
parries against fast, scarce enemies instead of 50 against slow, infinite ones. The achievement was
ungated; the good method never was.

The same shape with the details swapped, all equally invented: a strategy game's "win without
losing a unit," attemptable on any map and trivial only on the one with a chokepoint; a roguelike's
kill-count achievement, open from run one and several times faster once a build-defining relic has
been unlocked into the pool; a sports title's career milestone, reachable in any mode and cheapest
in the one that lets you simulate.

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

- **A method that depends on something still being locked or unfinished.** A region in its
  pre-story state, a faction still hostile, an out-of-bounds behaviour, a difficulty tier that
  hasn't scaled yet — each can produce a shortcut that simply stops existing once things unlock
  normally.
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

#### Thematic clustering is the default pull of writing, and it routes badly

Everything above assumes placement is being *decided*. Often it isn't — it's being inherited from
the outline. Items about the same subject want to sit together, because that is what writing does:
research arrives by topic, notes accumulate by topic, and a route assembled by writing comes out
grouped by topic unless something actively stops it. The result reads well and routes badly, and it
does so in a specific, predictable direction.

**A thematic cluster lands at its category's position, and a category's position is usually its
latest-gated member's.** Everything else in the cluster gets dragged along to that point. So the
failure isn't merely untidy sequencing — combined with method windows, it is that **an item
grouped with its topical siblings will often sit past the point where its own shortcut expired.**
The cheap method needed a region still locked, an NPC still alive, a faction still hostile, the
player still under-levelled — and the cluster carried the item straight through that window on its
way to where the category as a whole made sense.

Two questions per item, and they are asked of the item, never of the group it's sitting in:

- **Where does the community's easy method actually work?** Not where the task is possible, and not
  where the rest of its category happens to be — the specific point where *this* method's
  prerequisites are met and the player is already nearby.
- **Does that window close?** If the method has a closing edge, the item belongs inside the window,
  and being carried past it by a grouping decision is the most common way that happens.

**Place it where the task is cheapest, not where it thematically belongs.** Then keep the topic
where topics belong: in the note, as a named relationship ("this is the third of the four [contract
boards]; the others are in Phase 2 and Phase 5"), which costs the reader nothing and costs the route
nothing either.

The tell in a draft is a run of items that are obviously siblings and have no stated individual
reason for being where they are. If a cluster's placement was decided once and applied to all of
them, that is a category-level gate check wearing checklist clothes — the same defect the
shared-gate bundle rule describes, arriving through placement instead of through structure.

#### Where all three of these land

**Two things outrank the ceiling, the window, and the cluster alike** — they're principles 1 and 2,
and they're deliberately willing to pay the cost: **missables** and **power-unlocks** go early even
when early is expensive. A missable done the hard way beats a missable lost, and a power-unlock's
entire value is the hours it saves everything after it.

**The exception overrides cost, never feasibility.** Everything these two outrank — a worse method,
a dedicated trip, a harder attempt, full price, a redundant grind — is *expensive*, and paying it
early is the trade being made deliberately. The five dependency axes are a different kind of thing:
they say the item cannot be done there at all. A missable whose only method needs nightfall, a
faction state the player hasn't reached, a branch not yet taken, or a trigger the game owns has no
earlier placement to go to, and "go early regardless" would be asking for a position that doesn't
exist. So read the rule
as **earliest *feasible* point, not earliest point** — then, since a missable pinned late by an axis
is a genuine risk rather than a preference, the constraint gets stated on the line and in the
missables box, so the player knows why it can't move and what happens if they pass the window
without it.

Everything else resolves by honestly comparing the cost both ways. The reason to do things early
is a small post-story cleanup, not earliness as a virtue: a task the player will fly straight
past in Phase 5 costs nothing to leave in Phase 5, while the same task in Phase 1 can cost a
cross-map trip and a harder attempt. **When early and late are genuinely comparable, go early** —
that's what keeps the cleanup phase small. When they aren't, go where it's cheap.

**Then record the decision in the item's note**, in the same invented terms as the parry example
above: "left until Phase 4 — [the slow-telegraph enemies] are the fast way to do this, and [their
zone] isn't open before then." An unexplained late item is indistinguishable from an unresearched
one, and the next pass over the guide will drag it forward again on exactly the reasoning these
sections exist to stop.

### Moving an item is a claim — and caution is not evidence

The two audits either side of this one push in opposite directions: the cleanup audit drags content
forward, the ceiling drags it back. Both exist to correct unresearched placement, and both can be
carried out *without doing any research*, which reproduces the original defect with the sign
flipped. The move that gets away with it is the backwards one, because relocating something later
always feels like the careful option.

**Moving an item away from where a source placed it is a claim requiring evidence, exactly as much
as placing it early is.** A walkthrough page, a top-voted solution, a roadmap's phase, or the
per-game notes store asserts something about the game when it puts a task at a given point.
Overriding that asserts something else — that the placement is wrong, or that a prerequisite exists
the source never mentioned. That is a claim of the same kind and it carries the same burden. The
Step 1 rule holds here in both directions: an override is allowed on a **verified** reason, and if
you cannot verify it, defer to the source.

**Caution is not evidence.** "Better safe than sorry," "it can't hurt to leave it later," "they
probably won't have the upgrade yet" are all reasons to *go and check*, never conclusions. **If you
are relocating something because a gate "must" exist** — because it would be surprising for a task
this strong to be open this early, because the method *sounds* like it needs something — **you are
asserting a gate you have not found.** That is the same unevidenced move as reading "no trigger
found" as ungated, run backwards, and it is the mirror of the Phase 1 problem: unevidenced claims
accumulate at the front of the route as things believed ungated, and at the back as things believed
risky.

The reason this survives every check is that the two errors fail differently. **Placing something
too early fails loudly** — the player tries it, it doesn't work, and they come back and say so.
**Placing it too late fails silently**: the task works whenever they finally reach it, nothing looks
broken, and the cost is a cross-map trip and a harder attempt they never learn were avoidable.
Nobody reports a guide for being needlessly cautious, so the only thing that can catch a defensive
relocation is the note it was made to carry.

So **record the override and its reason, and mark it as an override**, in the item's note where the
player and the next pass both see it. Three parts, none of them optional:

- **What the source said** — named, not gestured at ("the walkthrough puts this in [the second
  act]," "the top solution says to wait for [the late unlock]").
- **What the guide does instead, and why** — the specific mechanism, in the same terms the rest of
  the note uses.
- **What that reason rests on** — a verified fact, or an assumption explicitly marked as one. An
  unverified reason recorded *as* unverified is a working note; the same reason recorded flat is a
  fabricated one, and per the hedging rule in Step 1 it is worse than no reason at all.

An unrecorded override becomes invisible in one edit round. The item simply sits where it sits, the
reasoning that put it there is gone, and it is now indistinguishable from a researched placement —
so the next pass either re-derives the same guess from scratch or, more often, leaves it alone
because it looks decided. Recording it keeps it checkable: by a later pass, by a re-research when a
blocked source becomes reachable, and by the player, who is the one paying for it if it's wrong.

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

### Waiting is never a step — every pending outcome runs underneath the route

**A "wait" is any gap between the player causing something and that something being ready** — and
elapsed in-game time is only the most obvious way a game creates one. This section was originally
written for clocks, and reading it as being about clocks is the way it gets missed: a guide can
route every in-game-day timer perfectly and still park the player in front of a message that
hasn't arrived yet. Every pending outcome has the same three parts and gets the same treatment:

| Part | The question | Why it matters |
| --- | --- | --- |
| **Start condition** | What creates the pending state, and how early can the route do it? | This is the whole fix — everything else is cleanup |
| **Resolution condition** | What actually advances it — time, player actions, a counter, a session boundary, a die roll? | Decides whether the route can absorb the wait or has to act |
| **Arrival signal** | What tells the player it's ready, and where does it show up? | An outcome the player never notices is an outcome they never collect |

**The resolution condition is the part that's routinely assumed to be time and isn't.** Shapes
this takes, invented and spread across genres: an in-game message, letter, or call that arrives
some days after a trigger; an activity, encounter, or visitor that only fires once a counter of
completed missions, wins, or levels is passed; a contact who only reappears the *next time* the
player enters an area, sleeps, saves, or fast-travels; a vendor restock or job board that rolls
over on a schedule; a daily or weekly reset on a real-world clock; an online reward that only
lands at the next sign-in or server sync; a random-chance event that rolls periodically and may
need several rolls; a build, craft, research, or crop timer; a relationship or reputation that
only moves a step per period. Some of these advance while the player does anything at all; some
advance only while they do something *specific*; and some don't advance on their own at all.

The failure they share:

**Wrong:**

```
□ Wait a few in-game days for the property to start paying out.
□ Wait for the message about the next job to arrive.
□ Wait for the side activity to become available.
```

Three pending outcomes that could all have been set running back in Phase 2, resolved one after
another while the player does nothing. **Back-to-back waits are almost never a property of the
game — they're a drafting artifact.** They appear because the guide was written in the order
rewards get *collected*, so each pending state was started at the line where its payoff is
claimed, which serializes things the game itself resolves in parallel. Even a single isolated
"wait" step is usually the same bug in smaller form.

Four things fix it, in this order:

- **Start everything at its earliest legal point.** Research the start condition — buying the
  property, triggering the call, planting the thing, making the deposit, completing the mission
  that starts the counter — and put *that* action in the earliest phase where it's reachable.
  This is the whole fix; the rest only cleans up what's left.
- **Know what actually advances it, and route accordingly.** A wait that resolves on elapsed time
  or on progress the player is making anyway is absorbed for free by putting real work
  underneath it. A wait that resolves only on a *specific* player action — sleeping, saving,
  leaving and re-entering an area, ending a turn, reloading, signing out and back in — is not
  absorbed by anything, and the guide has to name that action and fold it into a step the player
  was already taking. Treating the second kind as the first produces a note promising the thing
  will be ready by Phase 4 when nothing in Phase 4 ever triggers it.
- **Let it resolve underneath real work.** Once started, the route keeps going with actual tasks
  and the collection line appears later, wherever the player is genuinely nearby again (all the
  usual grouping and backtracking rules still decide exactly where). Concurrent pending outcomes
  collapse into one window sized by the slowest, not a queue. **This half only applies where the
  player collects.** Where the game delivers — a call, a message, a visitor, an event — there is no
  "nearby" to route to and no collection point to choose: the line goes at the earliest point the
  thing can arrive and says it arrives unprompted (axis 5). Choosing a convenient collection
  position for something that finds the player is the axis-5 failure arriving through the waiting
  rules.
- **Only if the window genuinely can't be filled**, name the game's own cheapest way to advance
  it — resting at a camp or inn, saving to roll the clock forward, ending the turn, a fast-travel
  leg, re-entering the area — as *one* line, not one per pending item, and say how much it needs
  to cover. "Wait a few in-game days" with no mechanism is never acceptable, and neither is "wait
  for the call"; if the player must pass time or repeat a trigger, tell them the fastest way the
  game provides.

**How this renders in the checklist:** the *start* is a real checkbox ("Buy [the income property]
— income accrues from here"). The *collection* is a real checkbox later. The wait itself gets no
checkbox at all — it is not something the player does (the no-FYI-checkbox rule in Output Format),
so it lives as a note on the collection line: "needs ~5 in-game days; you started this back in
Phase 2 and the missions since have covered it."

**But the mechanism that advances a wait is a checkbox, because it is an action.** "Rest twice at
[the inn] to cover the remaining two days," "sleep until night," "end the turn," "save and reload
to roll the vendor stock" all pass the no-FYI test outright: checking the box represents something
the player did. The distinction is exact and worth holding — **the wait is a state and never gets a
box; the act of passing it is a task and always does.** Getting this backwards in either direction
costs something real: a note-only mechanism leaves a required action with no way to track it, in
the one document whose whole job is tracking, and a player who steps away mid-gap comes back unable
to tell whether they did it. This applies wherever a pass-time or reach-the-window instruction
appears, including the cyclic-window mechanism the four-axes section requires.

**The collection line states the arrival signal.** Where it shows up and what it looks like — an
icon on the map, a mailbox entry, a phone notification, a new board listing, a menu badge, or
nothing at all — because a pending outcome with no stated signal is the delayed-confirmation
failure in the executability rules, arriving from the other direction: the player either misses
that it's ready, or re-does the start action believing the first one failed. **For a game-initiated
arrival the signal moves from the note to the visible line**, because it stops being context about a
task and becomes the only way the task ever starts.

**Then verify the window is actually covered.** If the intervening route is shorter than the wait
— too few in-game days, too few missions on the counter, no intervening step that performs the
required trigger — the note is a lie. Move the start earlier, move the collection later, or add
the explicit advance-it line. Checking this means counting the real steps between start and
collection, not assuming they add up.

#### Dependent chains: the clock can't move, so the route has to

Everything above assumes the pending outcomes are **independent** — several that could have been
running at once. The harder case is a **dependent chain**, where each wait is gated on the step
before it: talk to an NPC, wait a few in-game days, talk to them again, wait a few more, talk to
them a third time. The gate between links doesn't have to be time — a chain can equally be
message-then-reply-then-message, or a contact who only reappears after the next few missions each
time — and the shape is identical whatever advances it. Nothing can be started earlier, because
link 2 doesn't exist until link 1 has happened and the gap has been covered. Starting the clock early is not available as a fix here, and
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
  total, ~3 in-game days between each; the next three are in Phase 3 after [the harbor questline],
  at the opening of Phase 4, and in Phase 4 after [the tournament]"). The player should never be
  surprised by a link appearing, or wonder whether they missed one.
- **Every later link carries a back-pointer**: "visit 3 of 4 — you did visit 2 in Phase 3; enough
  days have passed since then." Without it, a lone "talk to X again" line 60 items later reads as
  an orphan or a duplicate.
- **Count the intervening steps for every gap, not just the first one.** Each individual gap has
  to be covered by the work actually sitting between those two links. A chain can be correctly
  interleaved at the front and collapse into back-to-back links at the end, where the route runs
  out of nearby tasks — that tail is where this bug survives an inattentive check.
- **If a gap genuinely can't be filled** — the player has cleared everything reachable in that
  window — that specific gap gets the named pass-time mechanism from above, and only that gap.
  One unavoidable "rest twice at [the inn] to cover the remaining two days" is a fine
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

- **Name regions, zones, chapters, and modes by their in-game names** rather than a shorthand the
  game itself never uses ("Island 1," "Area 2," "the second act"). Where community guides use a
  shorthand, define it against the in-game name on first use: "[the game's own name] (the starting
  region, called Zone 1 in some guides)."
- **Define jargon on first use.** Not all players know the game's own name for its side activities,
  or what a given title means by a "trial," a "rampage," a "time attack," a "seed," or an
  "ascension." One-line definition on first mention.
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

**The guide ships with its checkers.** The HTML file is what the player uses and stays a single
self-contained document; alongside it goes the route data and the small verification suite that
reads it (see the checker-suite section below). Those are build-time tooling, and they are part of
the delivery for the same reason content-derived IDs are: the next edit round happens in another
session, and a check that lived only in this conversation will not be there for it.

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
   front-loaded, per Step 4. Phase **titles** are proper title case ("Second Region Unlocked," not
   "Second region unlocked"); the smaller descriptive sub-caption under the title (e.g. "missions
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
  highest-value target: when a player searches "blacksmith," "fire resistance," or "respec," the
  answer is usually a location or definition the skill deliberately tucked into a note.
- **Reveal matches automatically.** A hit inside a collapsed phase opens that phase; a hit inside
  a bundled mission sub-list opens the parent; a hit inside a note expands (or at minimum flags)
  that note. Filtering without auto-expanding is the same bug as not searching notes at all.
- **Keep matches in context.** A lone child row showing nothing but a mission's name tells the
  player nothing. Show the ancestor chain — phase, then parent item, then the matching row — so
  every result is locatable in the route.
- **Highlight the matched substring** in the results, case-insensitively.
- **Show a live match count** ("14 matches"), and a real empty state naming the term ("No matches
  for 'stealth kill'") rather than a blank list.
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
  and not under a separate "Side Content" heading.** A parent line ("Play mission 6 — [the workshop]
  unlocks") gets child lines directly under it for what just opened up. This keeps strict
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
  **And every child inherits this parent's position, so nesting several items here asserts they
  all share its gate and its window** — verified per child, never once for the category they
  belong to (see the shared-gate bundle section in Step 7). Where one member of a set diverges, it
  leaves the sub-list and takes a real step of its own at its own position.
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
ship a bare achievement name and a fragment ("[achievement name] — one rank promotion") without
making sure a first-time player would know what to actually do — what "rank" means here, how
it's earned, where. Prefer: keep the visible line as short as the reference file's style, but
back every non-obvious one with a note that answers "what do I actually do, in plain terms" in
one or two sentences. This applies especially to multiplayer achievements, minigames, and
anything named after in-game jargon.

**What "short" means here is short on *explanation*.** A constraint is never what gets cut to make
a line fit — see the visible-line rule, which is the one thing this section does not license
pushing into a note.

### Add locations whenever they're needed or would help

If a task happens somewhere specific — a vendor, a landmark, a room, a level, a map, a mode, a
menu — name it exactly. The place's own name plus how to get to it beats "at any merchant" or "on
one of the desert maps." When more than one valid option exists, don't name one arbitrarily: work
out and recommend the *best* one — closest to where the player actually is at that point in the
route (their current hub or base, the mission they just finished, an area they're already passing
through), or otherwise the most convenient (everything in one stop, cheapest, unlocked earliest,
shortest to reload). "Any vendor who sells reagents" and "any level with a long straight" are
cop-outs if research can turn up the specific one and why it's the right pick right now.

Look this up during research (Step 1) — don't leave it vague, and don't assume two activities of
the same "type" share a location, a level, or a mode just because they seem like they would;
verify each one separately.

### Every item must be executable from its own line

An item is finished when a player who has read only this guide can act on it without going
somewhere else to find out how. The test is mechanical and it gets asked of every item: **what
does the player do in the ten seconds after reading this?** Three parts, all of which must be
answerable from the item's own text — the visible line plus its note:

- **Where do they physically go** — the place, screen, menu, mode, or device they have to be at,
  and how they get there from where the route just left them.
- **What do they interact with** — the object, character, terminal, menu entry, item, or input.
- **What confirms it worked** — the pop-up, counter, unlock, log entry, or state change that tells
  them to tick the box.

If any of the three requires knowledge the guide never supplied, **the item is incomplete even
though nothing in it is false.** This is a different defect from inaccuracy, and it survives every
accuracy check in this skill precisely because every word on the line is correct. The
concrete-noun sweep asks whether each specific is *sourced*; this asks whether the specifics the
player needs are *present*. A line can pass the first and fail the second completely.

**Pay particular attention to items naming a system rather than a place: naming the system is not
explaining the access route.** A website, a companion app, a console dashboard, an in-game
terminal or console, a storefront, a service, a submenu — each of these is a destination, and
naming it says nothing about how the player reaches it. The line reads as specific, so it passes a
skim, and the player is left holding a controller with no idea what to press. What a system-named
item owes, on top of the three parts above:

- **Whether it's inside the game at all.** A step requiring the player to leave the game — a
  browser, a phone app, the console's own dashboard, a support page — has to say so outright,
  because everything around it in the route assumes they're playing.
- **The route in.** Which menu, which tab, which building, what the thing looks like, what the
  player has to already have (an account, a linked profile, a code, a signed-in session, a rank).
- **Whether it's still live**, for anything external — Step 1 already asks this of servers and
  delisted content, and it applies with full force to a site or app a step depends on.

Hypotheticals, invented and spread deliberately: a step saying "register the game on the
publisher's site to unlock the bonus item" (from what device, with which account, does it need to
match the one on the console, and where does the item then appear); "use the terminal to look up
the target" (which building, which floor, is it the wall panel or the desk unit); "claim it from
the in-game store" (which tab, is it free, does it need the online mode loaded); "enable the
option in settings" (which settings — the game's, the console's, or the mode's own).

**Corollary: if the confirmation is delayed or invisible, say so on the line.** An action whose
visible result arrives hours later, or never appears at all, reads as a failure — so the player
retries it, or decides the guide is wrong and abandons it. Both are expensive, and the retry is
not always harmless: some of these consume a one-shot resource, a limited currency, or a daily
allowance, and a double-claim can jam the thing it was meant to grant.

So when there is no immediate feedback, the note carries what the guide can supply: **how long**
until it lands, **where it will show up** when it does (an in-game mailbox, a stats page, the
next session's loading screen, an inventory tab the player has never opened), and **what to do in
the meantime** — which is normally "keep going, don't repeat this." Where there is genuinely no
feedback at all, say *that*, plainly: the absence of a confirmation is itself information, and
stating it is what stops silence from being read as failure. Invented shapes across genres: a
reward posted to an in-game mailbox some days after the trigger; a cumulative stat that only
updates on an end-of-run summary; an online unlock that appears after the next sign-in sync; a
counter with no in-game tracker whatsoever, where the achievement pop is the first and only
signal.

### Every constraint goes on the visible line — notes carry method, never feasibility

The note mechanism is what makes several hundred items scannable, and it is therefore the default
destination for everything research turns up. That default is right for most of it and catastrophic
for one class: **a constraint that decides whether the attempt can succeed at all.** The split is
exact and it is not a matter of length or importance:

- **The visible line carries anything that determines whether the player is *able* to do this
  here.** A time-of-day, weather, or season window. A branch condition — spare or kill, this faction
  or that one, spend the one-shot item or keep it. An unprompted trigger the game owns. A closing
  deadline. A rank, tier, or difficulty requirement. A prerequisite that must be in hand before
  starting rather than acquired along the way.
- **The note carries method and reasoning**: why the item sits here, what the source said, what the
  efficient technique is, what the jargon means, how the category relates to its other members.

**One piece of method rides with the constraint rather than into the note: whatever the player must
do to satisfy it.** The game's fastest way to reach nightfall, the weather, the season, or the
reset belongs on the line beside the window it unlocks, because a window with no mechanism is
"wait a few in-game days" — a condition stated and no way to meet it. The test for whether a
sentence is method or constraint is not what it describes but what its absence costs: if removing
it leaves the player *unable* rather than merely *uninformed*, it is on the line.

**A constraint in a collapsed note is a constraint the player does not meet.** Not because they are
careless — because the file is designed to be read with the notes closed, which is the whole reason
notes exist. The three failure shapes are worth naming, since each is a real cost and none of them
looks like a defect on the page:

- **A time window in a note** is a player standing in the right place at the wrong hour, concluding
  the guide is wrong about the location.
- **A spare-or-kill condition in a note** is a player who made the choice already, on a save they
  cannot go back to. This one is unrecoverable, which is why a branch condition is closer to a
  missable warning than to a piece of context.
- **An unprompted trigger in a note** is a player travelling to a place to meet someone who was
  going to call them.

The pull toward the note is strong and it is a writing instinct rather than a judgment: the
constraint is a qualifier, qualifiers make a sentence longer, and this skill also asks for short
lines. **Brevity governs explanation, not constraints.** The short-line rule means a line with the
*explanation* stripped off it, not a line with its conditions hidden — "[task] — night only, sleep
at [the inn] to skip ahead" is short. Where a line genuinely gets unwieldy, cut the reasoning, not
the condition.

The content-depth standard's test asks whether the player could still *complete* everything with
the notes deleted. This is the sharper version of the same question, and it is the one to run first:
**with every note deleted, could the player still tell what they are and are not allowed to do?** A
line that reads as an unconditional instruction when it isn't is worse than a line missing detail,
because the player acts on it confidently.

### Content depth standard

Match the depth of a well-run community wiki, not a bare task list. For every item, prefer
including (via an expandable note, see below, so the main line stays scannable):

- Exact locations, spawn points, or landmarks when it saves the player a search
- The *reason* for a sequencing choice when it isn't obvious ("do X before Y because Z")
- Known bugs, disambiguation between conflicting community sources, and common failure modes
- Efficient techniques/exploits worth calling out explicitly

Use a small expandable "(i)" note toggle on any line that needs this extra detail or a
plain-English definition of jargon (assume the player may be new to this game — define the game's
own names for its side activities and minigames on first use via this same mechanism). The visible
line stays short; depth lives one tap away. Nothing the player actually needs to *not miss*
gets hidden behind a collapsed note — only context and reasoning does (the visible-line rule above
is the strict form of this, for constraints specifically). The test: if you deleted
every note, would the player still be able to complete everything correctly, just without
knowing why? If not, something that belongs on the visible line got buried in a note.

### Concrete nouns are the audit unit — and a correction pass is new writing

**Concrete nouns are the audit unit.** Every street, venue, building, vehicle, item, button
input, numeric threshold and time window that appears in a note must trace to a specific source
you actually read. Fluent guide-writing generates plausible specifics on its own, and on the page
an invented specific is indistinguishable from a researched one. If you cannot name the source
for a concrete noun, cut it — a note that says less is not worse than a note that says something
false with confidence.

**A correction is new writing, not cleanup.** The fix pass is where fabrication enters most
easily, because applying a finding feels like transcription and carries none of the checking
discipline of the research pass. Every concrete detail introduced while correcting an earlier
error is held to the same sourcing standard as the original.

**An invented enabling detail is a symptom of a placement conflict.** When a source's method
arrives with an acquisition or availability fact that does not fit where you have placed the
item, the pull is to bridge the gap with a plausible specific and keep the placement. Treat any
detail you are about to supply that *rescues* a placement as a stop signal. The availability fact
is the finding; the placement is what changes.

**Mark inference inside the artifact, not only in your notes.** Where a method or location is
your own reasoning rather than a community solution, say so on the line the reader sees. A
flagged inference is honest; an unflagged one is a claim.

### The per-item gate — run this list on every item, as you write it

Everything above is a rule about items; this is the checklist that makes sure none of them got
skipped on *this* item. **It runs at write time, once per item — every mission, child row, side
activity, achievement task, sweep, and habit line — and again on any item edited later**, however
small the edit looked.

It exists because the verification passes further down are all file-level. Those run once, at the
end, over several hundred items, and by then a missed rule costs a re-walk of the whole route,
while the same miss caught at the moment the line was written costs one line. The two are not
alternatives: **a per-item gate cannot see cross-item contradictions** (a stale phase note, a
duplicated sweep, a chain that collapses at its tail), and the file-level sweeps cannot
realistically reconstruct what each individual line owed. Run both.

**Is it an item at all?**

1. **Does checking this box represent the player having *done* something?** If the honest answer
   is "nothing, it's context," it's a note or a phase note, not a checkbox.
2. **Is it exactly one unit of progress?** One mission, one row; no umbrella line overlapping
   items listed separately below it; a bundle names its range and gives every unit a child row.
3. **If it's inside a bundle, was its gate checked individually?** Children inherit the parent's
   position, so grouping asserts a shared unlock condition *and* a shared window for every member.
   A gate researched once for the category is not an answer for this row.

**Is it in the right place?**

4. **Were all five dependency axes enumerated and recorded** — mission prerequisite, elapsed time
   since a prior step, time-of-day or cyclic window, irreversible choice, trigger ownership —
   including the ones that came back empty? An unrecorded axis is indistinguishable from an unasked
   one, and satisfying the loudest axis is not clearance on the other four.
5. **Does the player initiate this, or does the game?** If the game does, is it at the earliest
   point it can arrive, does the line say it comes unprompted and through what, and is it outside
   every sweep, batch, and area cluster? A note saying the game reaches out, under a line phrased as
   a destination, is the tell.
6. **Is this where the player actually does it** — not where it was unlocked, not where it groups
   tidily? If the relationship and the position disagree, the position wins and the relationship
   goes in a note.
7. **Did anything but this item's own cost decide its position?** If it sits next to its topical
   siblings, that is the outline placing it, not the route. Where is *this one's* cheap method, and
   has that window already shut here?
8. **Does the player have control here?** Confirm the preceding unit hands control back rather
   than running straight into the next, and that they're still where this item assumes.
9. **Is the placement backed by a verified gate — or by a verified statement that nothing gates
   it?** "No gate found" is not evidence of no gate, and this applies hardest to anything landing
   in the first phase. Check that the *system* is running, not just that the place exists.
10. **Is the item's best *method* available here, and is the player already nearby?** Earliest
    reachable is a ceiling. And does the method have a closing edge — a window that shuts when a
    region opens, an NPC dies, or the player out-levels it?
11. **If it's late, is there a stated reason it's late?** Nothing lands in the cleanup phase by
    default. And if it sits anywhere other than where a source put it — earlier *or* later — does the
    note record the override, name the source, and say whether the reason is verified? Caution is not
    a reason.
12. **If it involves a pending outcome, is the start at its earliest legal point**, does real work
    sit in the gap, and does no other wait sit adjacent to it?
13. **If it's a child, does it genuinely come after its parent?** A "do this first" warning belongs
    on the parent line, never as a child of it.

**Is every constraint visible without expanding anything?**

14. **Is every non-empty axis on the visible line, not in the note?** The window, the branch
    condition, the unprompted trigger, the deadline, the rank or tier requirement. Notes carry
    method and reasoning; a constraint in a note is a constraint the player never meets. Delete the
    note mentally: does the line still say what they are and aren't allowed to do?
15. **If it carries a cyclic window, does the line state both the window and the mechanism** —
    the game's own fastest way to reach night, the weather, the season, the reset? A window with no
    mechanism is "wait a few in-game days" wearing a different hat.
16. **If it turns on an irreversible choice, does the line name the branch and which side of it
    this item needs?** Spare or kill, this faction or that, spend or keep. This one is closer to a
    missable than to context, because the player who reads it late has already decided.

**Can the player execute it from this line alone?**

17. **Where do they go, what do they interact with, what confirms it worked** — all three
    answerable from the visible line plus its note. If it names a system rather than a place, does
    it give the route in, and say whether they have to leave the game?
18. **If the confirmation is delayed or invisible, does the line say so** — how long, where it
    shows up, and not to repeat the action?
19. **Is every location the specific best one for this point in the route**, named exactly, rather
    than "any vendor"? Is any jargon on the line defined on first use?

**Does it close its own loops?**

20. **Backward: is every prerequisite it implies** (item, vehicle, currency, unlock, access, stat,
    rank) either acquired on this line or completed by an earlier one?
21. **Forward: does every thing it names** — especially inside an unlock description — have its own
    real step somewhere later, or an explicit out-of-scope statement? Does any deferral in its text
    have a matching completion step, written in this same pass?
22. **Is every dependency on this line tagged with its direction** — a gate the named mission has
    to precede, or a deadline it has to follow? Write it in words that carry direction ("needs X
    first," "must be done before X"), never "tied to X," and check the ordering both ways.
23. **Does anything it asserts in the past tense** ("now that you've…", "the X you bought
    earlier", a running total) point at a real earlier checkbox that produced it?

**Is it honest?**

24. **Does every concrete noun, number, threshold, and input trace to a source you actually read?**
    If you can't name the source, cut the detail — and hold anything added during a correction pass
    to the same standard.
25. **For anything this line claims about availability, was a structured source checked** — a table
    with per-item unlock, window, and prerequisite fields — before settling for prose? And if the
    agreement backing it is several prose guides, do they actually have independent origins?
26. **Is the placement reconciled with the top community solution** — matching it, or carrying a
    stated, verified reason for differing? Is any inference of your own marked as inference on the
    line the reader sees? Is there a hedge standing in for research you could have done?

**Mechanics**

27. **Content-derived slug for the ID, no positional cross-references in the text** ("two steps
    above," "the next item"), and if it's missable, is it flagged both inline here and in the
    top-of-page box?
28. **Does this line carry the machine-readable fields the checkers need** — its declared
    constraints, its tagged dependency directions, its trigger owner — in the data rather than only
    in the rendered prose? A rule the checker suite cannot see is a rule that survives only as long
    as attention does.

When a new per-item rule is added to this skill, it joins this list in the same pass — a rule that
applies to every item and isn't on the gate is a rule that will be applied to some of them. **And
where the rule's shape allows it, it joins the checker suite too**, for the same reason: a rule
enforced only by a list someone reads is a rule that lapses under editing pressure.

### Visual design — the structure is shared, the look never is

**Every game gets its own visual identity, derived from that game, and no two guides look
alike.** This is a deliberate, permanent, non-negotiable feature of these guides, not a styling
preference — a player keeps several of these files open across years, and each one should be
recognizable as *that game's* guide from a thumbnail, before a single word is read.

Build the look from the research gathered in Step 1, not from imagination:

- **Palette from the game**, not from a generic dark-dashboard default. Take it from what the
  game actually looks like — its HUD and menus, its key art, the dominant colors of its setting.
  A rain-grey city of washed municipal blue is not a sunset-pink-and-teal beach city, and neither
  is a fantasy RPG's parchment and ink.
- **Type that evokes the game's own lettering.** Pair a display face for the header and phase
  titles with a readable body face (Google Fonts are fine). The logo's letterforms and the
  mission-title card are the reference.
- **One signature element the game itself owns**, carried through the file — a wanted-level star
  row, a radar disc, a stat-screen bar treatment, a stencil, a paper texture, a scanline. It
  should appear in the header, the progress bar, and the phase markers so the file reads as one
  designed object rather than a theme color swapped into a template.

**Theme the entry, not the franchise.** A series' most iconic look is not necessarily *this*
game's look, and the more famous the franchise, the stronger the pull toward its brand imagery
instead of the title in front of you. The case that has actually gone wrong here had exactly this
shape: a long-running open-world series whose brand imagery is sun-bleached neon — hot pink, cyan,
palm trees, a chrome-and-sunset logo — and the entry being written up was the deliberate opposite
of that. Grey and rain-soaked, desaturated blue and municipal drab, dirty amber sodium streetlight,
key art built from high-contrast black-and-white character panels. The neon treatment that shipped
wasn't a slightly-off palette, it was a different game's identity. The same trap sits in any series
with a tonal outlier: check what *this* entry looks like, and when an entry breaks from its series'
house style, say so explicitly in your notes and verify the palette twice — the franchise's gravity
is strongest exactly where it is most wrong.

**The reference-file trap is the main way this fails, and it is built into the workflow.** This
skill tells you to open a prior game's guide as the reference for quality bar and structure — and
that file arrives with a complete palette, type pairing, and signature motif already wired
through it. Editing it is the path of least resistance, and the previous game's look survives the
edit because nothing forces it out. So: **take the structure from the reference file and nothing
else.** Re-derive the palette, the fonts, and the motif from scratch for the new game before
writing any CSS. "Not the *exact* same palette" is not the standard — a recolored version of the
last guide is the same failure, and it is what you get by editing rather than re-deriving.

Reuse across games: the accordion phases, missables box, nested children, search bar, footer, and
every behavior in this document. Vary across games: everything the player sees.

### Item IDs must be content-derived and position-independent from the first build

**Item IDs must be content-derived and position-independent from the first build.** Derive each
ID from the task's own text as a slug, never from an index or position. Positional IDs make an
artifact resistant to its own corrections, and that resistance will be rationalised as protecting
the user's progress. Content IDs make repositioning free, which is the only condition under which
placement corrections actually get made.

**A placement correction must move the item. Ordering is never encoded in prose.** Position
carries order; notes carry method and caveats. If a note tells the reader to do something at a
different point than where it sits, the guide contradicts itself in its primary channel. Move it.

**If an artifact already has positional IDs and the user has begun ticking, migrate rather than
defer.** Ship a stored map from old ID to new ID, translate on load, and rewrite storage on first
run. This is a single pass. Deferring it degrades every subsequent correction, and the deferrals
compound: each one is individually defensible and collectively produces a guide whose order no
longer reflects what you know.

**When a structural flaw begins dictating content decisions, fix the structure.** The signal is
catching yourself choosing a worse fix because a better one is architecturally awkward. Do not
let the flaw accumulate exceptions.

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
every requirement a line implies, the acquisition must be either folded into that same line ("grab
[the fire-resistance item] from [the last vendor] before you enter [the fire zone]") or
completed by an earlier line the player has already checked off. If neither is true, the line is
unplayable as written — add the acquisition step, or move the line to after whatever provides it.
Things that hide as silent prerequisites:

- A required vehicle, weapon, tool, or outfit the route never told the player to obtain
- Cash, currency, or materials the route never had the player earn before a purchase item
- A skill/stat level, license, or proficiency gate on an activity
- Map, region, level, or mode access — a hub, a storage upgrade, a fast-travel unlock, a
  difficulty tier that has to be beaten before the next one appears
- An ability, perk, or companion introduced by a mission placed later than this line
- **A game system, feature, service, or menu that a story mission switches on** — a database or
  terminal, a phone contact, a shop or in-game website, property purchasing, fast travel, a bounty
  board, a challenge or stat screen. This one hides from every other check in this skill, because
  the *object* is usually present and reachable long before the *function* is live: the location
  check passes, the vehicle check passes, the player sits down at it and nothing happens. Resolve
  it by naming the mission that activates the system, not the place the system lives in.

**Forward (mentions): does the thing named have its own real completion step somewhere?** Every
noun the guide introduces as something that exists and matters must eventually appear as an
actual checkbox item — not just as a phrase inside another item's text. The highest-risk source
is unlock descriptions: "(the workshop unlocks)," "also unlocks horde mode," "opens up the second
crafting tier" each name a whole content category that will silently never be done if it never
receives its own line. Also check anything named in a note as "you'll want this for X," any
activity mentioned as existing in an area sweep, and any achievement referenced in passing.

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

### Dependency direction — gates must precede, deadlines must follow. Script it.

This is the first of three machine-checkable classes; the checker-suite section below covers the
other two and the rules for building and validating all of them.

The line-by-line dependency check resolves *whether* a dependency has a home. This one resolves
**which way it points**, and then proves the ordering mechanically instead of by eye.

**A prerequisite and a deadline are opposite constraints that look identical in prose.** A line
tying an item to a named mission is making one of two incompatible claims:

- **A gate**: the mission must come **before** the item. Do this after X; needs the tool X hands
  over; the board is empty until X.
- **A deadline**: the item must come **before** the mission. Do this before X; X closes the area; X
  is where the cheap method dies; X is the point of no return for this.

English marks the difference with one small word, and the guide's own vocabulary hides it
constantly: *tied to X*, *for X*, *with X*, *goes with X*, *X mission*, *do this around X* state a
relationship and no direction at all. So the two constraints get written the same way, filed the
same way, and only one of them ever gets verified — and it is always the gate, because "does the
prerequisite come first" is the question everyone already knows to ask. Deadlines fail in exactly
the silent direction this file keeps documenting: the item still works when the player reaches it,
or it doesn't and they blame themselves.

**So tag every dependency with its direction as you write it**, in the item's own note, in the
words that carry direction — "needs [mission] first" or "must be done before [mission]" — never in
the ambiguous middle. Every closing edge the method-window section produces is a deadline. Every
missable window is a deadline. Every unlock is a gate.

**Then verify both directions with a script, not a read.** This is one of the few checks in this
file that returns a definite answer, so it should never be eyeballed: the route is an ordered
structure with content-derived IDs, and the constraint is an inequality over positions.

1. **Flatten the route to true play order** — depth-first through phases, parents, and child rows,
   in render order. Flattening is not optional: the authored data nests, the player reads it
   flattened, and comparing against the un-flattened array puts every child row at the wrong index.
2. **Index it** — item ID to position, plus a lookup from mission/unit name to the position of the
   row that completes it.
3. **Extract the dependencies** — scan every visible line and every note for named missions or
   units, and record each with its tagged direction.
4. **Assert the inequality**: for a gate, `index(mission) < index(item)`. For a deadline,
   `index(item) < index(mission)`. Print every violation with both positions.

Three ways it fails, each meaning something different:

- **The inequality is backwards** — a real position bug. Move one of the two, then re-run the
  route-order walk, because you just changed the sequence.
- **The referenced mission resolves to nothing** — the backward half of the dependency check just
  failed mechanically: the guide names a prerequisite it never gave the player a step for. Add the
  step or state it out of scope.
- **The name matches nothing exactly** — usually the same unit written two ways in two places.
  That is also a search-bar defect (a player searching one spelling misses the other), so fix the
  naming rather than loosening the matcher.

**What the script proves and what it doesn't.** It proves that every dependency you *found* is
ordered correctly. It cannot tell you about a dependency nobody wrote down — that is still the
line-by-line dependency check's enumeration, and this does not replace it. Run the script every time before
presenting and after every edit round; it costs seconds, it is deterministic, and a moved item is
exactly the event that breaks it.

### The checker suite — ship it with the guide, and run it after every edit

**Stated rules do not survive editing pressure. Executable ones do.** That is not a maxim, it is
this project's own measured result: three separate rules about timing were each written down
carefully, and each was then violated in a later edit *by the same author who wrote the rule*. Not
misunderstood, not disagreed with — written, agreed, and then broken while attention was on
something else. A rule that lives only in prose is enforced by whoever happens to be paying
attention at the moment of the edit, and an edit round is exactly when attention is elsewhere.

So **wherever a rule's shape allows a machine to decide it, write the checker instead of trusting
the rule.** Three classes of constraint in this skill have that shape, and between them they cover
most of what an edit round breaks:

| Class | What it asserts | Examples |
| --- | --- | --- |
| **Ordering** | One position must be less than another | Gates precede their item; deadlines follow it; a link of a chain follows the previous link |
| **Adjacency** | What may or may not sit next to, or inside, what | No two waits adjacent; nothing between chained units; a game-initiated item inside no sweep; a "do this first" warning not nested under the thing it warns about |
| **Declaration** | An item carrying property P must state P on its visible line | A cyclic window states its window and mechanism; a branch dependency names the branch and side; an unprompted trigger says so; a deferral has a matching completion step |

Everything else in the verification passes — whether a fact is true, whether a placement is wise,
whether a note is honest — is judgment and stays judgment. The point of scripting these three is to
free that attention for the parts only judgment can do.

**Ship the checkers alongside the guide.** They are build-time tooling, not something the player
uses, but they belong in the delivery rather than in the session: a small script plus the route data
it reads, handed over with the HTML file. The reason is the same reason positional IDs get migrated
rather than deferred — the next edit round happens in a different session, possibly by a different
agent, and a checker that existed only in the last conversation is a checker that does not exist.
The guide itself stays a single self-contained HTML file for the player; the checkers sit next to
it, and the response says what they check and how to run them.

**This requires the route to be data before it is markup.** The checkers read the same structure the
HTML renders from — items with IDs, nesting, declared constraints, tagged dependency directions,
trigger owner — so build the file that way from the first draft. A guide whose only representation
is rendered HTML can still be checked, but every checker then starts by parsing prose, which is
where false negatives come from.

**Run the whole suite after every edit round, and run it before the judgment sweeps rather than
after them.** It is seconds of work, it is deterministic, and its output tells you which of the
expensive sweeps actually need attention — a moved item changes every index, and the suite is what
says so.

#### Test the checker before trusting it

**A checker's false negatives are invisible by construction.** A checker that finds nothing and a
checker that *can* find nothing produce identical output, and the second one is worse than having no
checker at all: it converts an unknown error rate into confidence. The original state was
uncertainty, which at least invites a look.

So no checker is trusted until it has been shown to fire:

- **Prove it on a known-bad case first.** Before relying on a pass, break something deliberately —
  move a gated item above its gate, strip the mechanism off a windowed line, put a game-initiated
  item inside a sweep, place two waits adjacent — and confirm the checker reports it. Then revert.
  A green run means something only after you have seen a red one. Keep the known-bad cases with the
  checkers as fixtures, so the proof re-runs rather than being remembered.
- **Strip presentation before matching.** Item text is authored with markup — emphasis, links,
  entities, non-breaking spaces, line wrapping — and a checker matching raw source will miss
  `**night**-only` while catching `night-only`, silently. Normalize first: strip tags, decode
  entities, collapse whitespace, fold case. This is the same lesson as the search bar's "search the
  data, not the DOM," and it fails the same way: every term the author tries happens to be one that
  matches.
- **Keep detection and requirement equally strict.** A checker has two halves — *which items does
  this apply to*, and *what must they say* — and they have to be calibrated together. Detect
  loosely and require strictly, and it screams at every line that mentions the word "night." Detect
  strictly and require loosely, and it inspects three items and passes the file. The second is the
  dangerous one, because it looks like a clean run. When they cannot be brought into line, prefer
  the noisy direction: a false positive costs a glance, and a false negative costs the defect the
  checker was written for.
- **Normalize presentation, never content.** These two look alike and are opposites. Stripping
  markup so `**Mission&nbsp;Four**` and `Mission Four` compare equal is normalization. Loosening a
  matcher so `Mission Four` and `Mission 4` compare equal is hiding a real defect — the same unit
  written two ways, which also breaks the player's search. Fix the naming; don't teach the checker
  to tolerate it.
- **Report what it did not check.** Every checker prints its coverage — items scanned, items
  matched, items skipped and why. "0 violations" over 4 of 380 items is a different result from
  "0 violations" over 380, and without the count they are the same line of output.

**A checker you have not seen fail is a claim, not a check** — the same standing this skill gives to
"no trigger found" and to a guide's own notes under audit. Validate it, then trust it.

### Assumed-completion check — every "you've already done X" needs an earlier line that did X

The dependency check above resolves things a line *needs*. This one catches the mirror-image bug:
a line that treats an action as **already performed** when no earlier line ever told the player to
perform it. The guide says "now that [the base] is upgraded," "with all [12 relics] collected,"
"sell the materials you've been stockpiling," "you should be at max strength by now" — and the
route never contained the step. Unlike the deferral sweep, nothing here reads as unfinished; it
reads as *finished*, which is worse, because the player trusts it and moves on. They discover the
gap only when the assumed thing turns out not to exist.

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
  levels). A later line assuming a threshold — "you'll have the [200,000] for [the ship upgrade]
  by now" — only holds if the route actually generated it. Trace the arithmetic, don't assume the
  player played efficiently.
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

**Enumerate against this fixed starter list every time — don't try to invent the list.** Working
out which premises a guide asserts is the hard part, and it's being asked for at exactly the
moment judgment already failed once. These recur across essentially every game, so tick through
them as a checklist and add any game-specific ones on top:

1. **Is there a clock?** A time limit, a day counter, a hunger/decay meter — and is it on *this*
   save or a separate one?
2. **Is the map gated?** What's reachable now versus later, and does any note assume access the
   player doesn't have yet?
3. **Save-bound or profile-wide?** Achievements versus completion percentage, and any note that
   conflates them.
4. **Placed at unlock, or placed where cheapest?** The routing rule itself, and every note that
   explains a placement.
5. **How many saves or playthroughs?** A dedicated speed-run save, NG+, a second run for
   conflicting choices — and which save each instruction is addressed to.
6. **Is anything time-limited outside the game?** Servers, delisted DLC, seasonal events.
7. **Is there a point of no return**, and does any note assume content is still reachable past it?

For each, find every note that asserts or depends on it and confirm it still holds. A fixed list
you tick through beats a list you're asked to invent, and grepping only the vocabulary of the rule
you happened to edit will pass a guide that still contradicts itself somewhere else.

**Two things this sweep specifically catches**, both of which read as fine in isolation:

- **A summary that still describes the old route.** "Everything else went into the phase where it
  unlocked" reads as reassurance and is now simply false — and it is exactly the sentence a player
  uses to decide whether to trust the ordering.
- **Grammatical seams from targeted replacements.** Patching a clause inside a carried-over
  sentence frequently leaves a broken or double-conjunction sentence. Re-read the *whole* sentence
  after any in-place edit, not the fragment you replaced.

This is Step 7's principle 8 — re-check position after editing content — applied to prose instead
of items. Same failure, different surface: the thing you edited is fine, and the thing that
described it is now wrong.

### Structural self-description sweep — claims about the artifact get checked against the artifact

The premise sweep above catches prose that *was* true and stopped being true when a rule changed.
This one catches prose that was **never true**: a sentence written while thinking about the
intended design, while the implementation went another way. Nothing invalidated it, so no edit
draws attention to it, and the premise sweep can't reach it either — there is no old premise to
grep for, only a description that never corresponded to anything.

The vulnerable class is narrow and easy to name: **any sentence making a claim about how the guide
itself is organized.** "Each collectible set is split across the phases where it's reachable."
"These are grouped by area rather than bundled at the end." "Every mission in this stretch gets
its own row." "Locations are listed separately from the tasks that need them." "The rest of this
category is nested under the mission that unlocks it." Each is a falsifiable assertion about the
artifact — and **each is checked against the artifact, never against intent.** Confirming that the
skill contains the rule the sentence describes proves nothing; the question is whether this file
actually did it.

**Grep for structural self-description and verify every hit by looking.** The vocabulary is stable
across games, because it describes this skill's own machinery rather than any game: *split
across*, *grouped by*, *rather than bundled*, *each gets its own*, *listed separately*, *broken
out*, *nested under*, *one per*, *in the phase where*, *collapsed into*, *distributed*. For each
match, open the thing it describes and count. A note claiming every mission in a range has its own
row is verified by expanding that range and counting rows — not by recalling that the bundling
rule exists.

The player-facing cost is what makes this worth a dedicated pass: these are the sentences a player
uses to decide **how to read the file** and **whether anything is missing**. A guide claiming a
set is distributed across the phases where it's reachable, when it actually sits in one lump in
the cleanup phase, doesn't just mis-describe itself — it teaches the player to stop looking for
the rest.

### Never write positional cross-references

A note that points at another item **by position** — "two steps above," "the confirmation step
below," "the next item," "three rows down" — is a fact about the current ordering, not about the
game. Every reorder invalidates it silently: nothing errors, the sentence still reads fluently,
and it now points somewhere else or nowhere. Since this skill reorders items constantly (method
windows, chain interleaving, cleanup audits, play-order corrections), positional references are
guaranteed to rot, and they rot in the notes nobody re-reads.

**Name the thing, not its distance.** "You unlocked [the free-fast-travel perk] earlier in this
phase when you pushed [that companion's] friendship past 90%" survives any reordering; "you
unlocked it two steps above" does not. Where the reference genuinely needs locating, name the
phase or the item's own title — both travel with the item — never a count of rows or a relative
direction.

This applies to the guide's own text, not to phase names: "in Phase 2" is stable because phases
are named units, while "two items up" is not. Sweep for the pattern before presenting; it is a
short, high-precision regex (`\b(two|three|\d+) (steps?|rows?|items?) (above|below)\b`, plus
"the next/previous step"), and every hit is a defect.

### Every sweep re-runs after an edit round, not just after generation

This is the loop that produced most of the defects this skill knows about, so it gets stated once,
plainly, for all of the checks above and the walk-through below:

**A targeted edit round requires the same full sweep as a fresh build.** Not a spot-check of what
you touched — the whole set: **the checker suite** (ordering, adjacency, declaration), deferrals,
dependencies, assumed completions, premises, structural self-description, positional references,
concrete nouns, route order, achievement-placement reconciliation, and the player walk-through. The
checker suite is the cheapest of these and the most sensitive to exactly what an edit round does —
moving one item changes every index — so **run it first and let it tell you what else moved.** It is
also the only part of the list that cannot be skipped by accident, which is the whole reason those
three classes were made executable. **Plus the per-item gate on every item you touched**,
since an edited line is a newly written line and owes the same list. Two of those exist specifically because a correction
pass creates its own defects: the concrete-noun sweep re-runs over the *corrected* text, and the
route-order walk re-reads the sequence a moved item just changed.

**Sweep for hedges while you're there.** Search the finished text for softening phrases — "if you
can't find," "if you haven't," "or you could," "assuming you," "should be able to" — and for each
ask whether it encodes a *real player choice* or an *unresolved research question*. The first is
fine. The second is a defect: verify it, then rewrite the line as a decision. A guide thick with
hedges is one that published its uncertainty instead of resolving it.

The reason is structural, not motivational. These defects are *created by editing* and are almost
never present in a first draft. Moving one item strands a prerequisite that used to sit above it,
falsifies a phase note three sections away that explains the routing, breaks a positional
reference in a note nobody opened, and turns a correct past-tense recap into a false one. **None of
that appears in the diff**, because the diff shows what you changed, and the damage is in what you
didn't. Every one of those has happened in practice.

So the sweeps are not a build-time gate that a revision pass has already cleared. Re-run them
after every round of changes, however small the round looked — a single moved item is enough to
require the whole pass. If that feels disproportionate, note that a one-line edit is exactly how
each of these bugs got in.

### Before presenting: walk it like a player, not a writer

Once the guide is built, this is the last gate, after everything above, before showing it to
the person — **and equally after any round of edits, not only after a fresh build** (see the
section immediately above). Re-read it start to finish as if actually playing, one line at a time,
checking:

- Does the sequence of checkboxes match how the game is actually played, with nothing skipped
  and nothing implied twice (the overlapping-items test from Step 7, principle 7)?
- **Is anything sitting where it sits because of grouping rather than play order?** For every
  nested child, ask whether the player really does it right after the parent — if the honest
  answer is "later, but it belongs to that mission," it's mis-positioned: move it to where it's
  actually done and put the unlock relationship in a note (the spine principle in Step 7).
- Does every location, vehicle, or target named on a checkbox line actually exist where the
  guide says it does (the location-research requirement from Step 1)?
- **Concrete-noun sweep.** Before delivery, extract every proper noun, number, threshold and input
  instruction from the notes and confirm each against a source. Run this again after any correction
  pass, over the corrected text — not only over text written in the original build.
- Does anything referencing a later point in the game appear before something referencing an
  earlier one (the position-desync check from Step 7, principle 8)?
- Would a player who has never seen this game get stuck or confused by any single line without
  opening its note? Does a "child" item actually belong after its parent? Is anything a bare
  FYI wearing a checkbox?
- **Executability, item by item: what does the player do in the ten seconds after reading this
  line?** Where they go, what they interact with, what confirms it worked — all three answerable
  from the item's own text. Enumerate; a line that reads fluently is the exact case this misses,
  because nothing on it is wrong. **Every item naming a system rather than a place gets checked
  twice** — a site, app, dashboard, terminal, storefront, service, or submenu is a destination,
  and the item still owes the route in, whether the player has to leave the game to reach it, and
  whether it's still live (the executability section in Output Format).
- **Does the player actually have control everywhere the guide puts work?** For every mission
  boundary the route places anything at — side content, a sweep, a shopping trip, a timer start —
  confirm the preceding unit hands control back rather than running straight into the next one,
  and that the player is still where the item assumes they are. Where a chain exists, confirm
  nothing sits inside it, the line before it says control won't return until it ends, any
  "while you're here" cluster breaks at it rather than spanning it, and anything the chain puts
  out of reach was flagged and placed before it (the chaining section in Step 7).
- **Does any step have delayed or invisible confirmation, and does it say so?** For every item
  whose result doesn't appear immediately — a mailed reward, a stat that updates on a summary
  screen, an unlock that lands at the next sign-in, a counter with no in-game tracker — confirm
  the line states how long, where it shows up, and that the player should not repeat it. An action
  that looks like it silently failed gets retried or abandoned, and some of them can't safely be
  retried.
- Does every "later" / "won't count until" / "the rest" promise in the guide's own text have a
  matching real completion step in a later phase (the orphaned-deferral sweep above), and does
  every recap claim match what the earlier sections actually completed?
- **Line by line: does every dependency a line raises resolve?** For each item, is every
  prerequisite it implies (vehicle, cash, unlock, region access, stat level) either acquired in
  that same line or already completed by an earlier one — and does every thing the line names
  (especially inside unlock descriptions like "the workshop unlocks") have its own real checkbox
  somewhere later, or an explicit out-of-scope statement? Enumerate them; don't eyeball it (the
  dependency check above).
- **Does every item have all five dependency axes on record?** Mission prerequisite, elapsed time
  since a prior step, time-of-day or cyclic window, irreversible choice, trigger ownership —
  enumerated per item, with the empty answers written down as empty. Then check the three the route
  can't prove on its own: every item carrying a cyclic window states both the window *and* the
  game's fastest mechanism for reaching it, every item touching a branch names the branch and which
  side of it the item belongs on, and every game-initiated item says so. An item cleared on one axis
  and never asked about the other four is the default failure, because the loudest axis answers
  confidently and retires the question (the five-axes section in Step 7).
- **Is anything the game initiates written as somewhere the player goes?** Sweep for notes saying
  the game reaches out — "he'll call," "you'll get a text," "a letter arrives," "the event fires" —
  and check the line above each one: if it reads as a destination with an imperative verb, the item
  is unexecutable, however accurate it is. Each of these belongs at the earliest point it can
  arrive, says on its visible line that it comes unprompted and through what, and sits inside no
  sweep, batch, or area cluster — a sweep is a plan the player executes, and this is not something
  they can execute (trigger ownership, Step 7).
- **Is every constraint on a visible line rather than in a note?** Open nothing and read the file:
  every window, branch condition, unprompted trigger, deadline, and tier requirement should be
  legible with all notes collapsed. A constraint one tap away is a constraint met at the wrong hour
  with the wrong save, and the spare-or-kill case is unrecoverable. Notes may explain how and why;
  they may not hold the thing that decides whether the attempt can succeed (the visible-line rule
  above).
- **Run the checker suite, and read what it prints.** Ordering: flatten the route to true play
  order, index it, and assert every tagged dependency's inequality — gates must precede
  (`index(mission) < index(item)`), deadlines must follow (`index(item) < index(mission)`). A
  prerequisite and a deadline read identically in prose — *tied to X*, *for X*, *with X* — so an
  untagged dependency is an unchecked one, and it is always the deadline direction that goes
  unverified. A reference resolving to no item is the backward dependency check failing
  mechanically; a name matching nothing exactly is the same unit written two ways, which also
  breaks search. Adjacency: no two waits touching, nothing inside an automatic chain, no
  game-initiated item inside a sweep. Declaration: every item carrying a window, a branch, or an
  unprompted trigger states it on its visible line. These are the checks here that return definite
  answers, so they are never eyeballed (the checker-suite section above).
- **Has the suite itself been shown to fail?** Confirm each checker has been run against a
  deliberately broken case and reported it — a gated item moved above its gate, a mechanism stripped
  off a windowed line, a game-initiated item dropped into a sweep. Check that it strips markup
  before matching, that its detection and its requirement are equally strict, and that it prints how
  many items it actually inspected. "0 violations" from a checker that matched four items is the
  output that reads best and means least; an unvalidated checker is worse than no checker, because
  it replaces uncertainty with false confidence (the validation rules above).
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
- **Does this file look like this game — checked against the game, not against your reasoning?**
  Put the finished header next to an actual screenshot or the key art and compare: are these the
  same colors? Naming your intent does not pass this check. A stated rationale for a palette is
  the thing under audit, and the skill's own rule applies to look exactly as it does to routing —
  checking a choice against the reasoning that produced it always passes. Then confirm three
  things: the palette came off an image you actually viewed rather than a mood word; it's *this
  entry's* look and not the franchise's house style; and set side by side with the most recent
  prior guide it's a different identity, not a recolor. **Show the player the palette, type
  pairing, and motif before building hundreds of items on top of them** — it is the cheapest
  correction point in the whole process, and the player is ground truth on whether it feels like
  the game.
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
- **Route-order walk.** After any correction pass, read the items in order as a player following
  the checkboxes would, and confirm the sequence still matches current knowledge. The premise sweep
  catches sentences made false by an edit; it does not catch an order that has quietly gone stale.
- **Does every sentence describing the guide's own structure match the guide's actual structure?**
  Grep for structural self-description — "split across," "grouped by," "rather than bundled," "each
  gets its own," "listed separately," "nested under," "one per" — and verify each hit by opening
  what it describes and counting. This is distinct from the premise sweep: these sentences were
  never true rather than made false by an edit, so nothing in the diff points at them, and checking
  them against the skill's rules instead of against the file always passes (the structural
  self-description sweep above).
- **Does the missable count match the walkthrough's?** TrueAchievements' walkthrough overview
  states missable and unobtainable counts outright. Compare them against Step 3's findings; a
  mismatch is an unresolved research conflict, not a rounding difference.
- **Has every achievement's placement been reconciled against the top community solution?** Go
  achievement by achievement against TrueAchievements/PowerPyx solution threads — not the
  descriptions, the solutions — and for each one either match their recommended placement or carry
  a stated reason for differing. An item sitting in a phase the top-voted solution says is the
  wrong one, with no note explaining the choice, is an unresearched placement wearing a confident
  face. Unreachable sources stay flagged as unverified rather than silently ratifying what you had.
- **Did one source supply the ordering, and was it verified rather than transcribed?** If a
  walkthrough, roadmap, or route post provided the spine, confirm it is named as such and that a
  sample of its claims was checked independently — weighted toward timing and availability, drawn
  from across the route, including one surprisingly early and one surprisingly late placement. A
  route inherited whole from one voice passes every internal check in this skill while never having
  been checked against the game (the spine-source section in Step 1).
- **Did any primary source stay blocked, and does the person know exactly what that cost?** For
  every source that couldn't be read: were the other access paths tried before accepting the gap,
  is there a named item-by-item list of the claims now resting on weaker sources, is that list in
  the response to the player rather than only in a notes file, and does it say what would resolve
  it? A logged gap with no list of affected items is a closed-looking ticket that is still open
  (the blocked-source section in Step 1).
- **Was the pending-outcome question asked of every content category, not once of the game — and
  in its broad form?** Walk the categories — progress line, each side activity, each collectible
  set, relationships, encounters and spawns, unlocks, vendors and economy — and confirm each was
  individually questioned, about arrivals, triggers, counters, restocks and resets as well as
  about clocks. A single game-level "no timers here" is the answer shape that hides dependent
  chains, and "we checked the timers" is the one that hides everything that isn't a timer
  (Step 5).
- **Does any note point at another item by position?** "Two steps above," "the step below," "the
  next item" — every hit is a defect, because this skill reorders constantly and the reference
  rots silently. Name the item or its phase instead.
- **Is the player ever told to wait — for anything, not just for time?** Sweep for every pending
  outcome, including the ones that aren't clocks: a message or call to arrive, an activity or
  contact to appear, a counter to fill, a restock or reset, an unlock that lands at the next
  sign-in. No two waits may sit adjacent; none may be started later in the route than it could
  have been; every wait note must point at real intervening steps that actually cover the gap
  (count them, and for a non-time wait confirm those steps genuinely *perform* whatever advances
  it); each collection line must say what the arrival signal is and where it appears; and any
  genuinely unavoidable pass-the-gap line must name the game's own fastest mechanism rather than
  saying "wait a few days" or "wait for the call" (the waiting section in Step 7).
- **Are any time-gated chains sitting as a contiguous block?** For every sequence where each
  step is gated on time since the one before it, confirm the links are interleaved through the
  route with real tasks in *every* gap — check the last gaps as carefully as the first, since a
  chain that runs out of nearby work collapses at its tail. Confirm the first link's note maps
  the whole chain and every later link points back to the previous one (the dependent-chain
  section in Step 7).
- **Is anything placed early that isn't actually possible there?** Audit the earliest phase the way
  the cleanup phase gets audited, item by item: each one must name the mission or event that enables
  it, or carry a verified statement that nothing gates it. Check the *system*, not just the place —
  a terminal, shop, contact list, or menu the player can walk up to may not be running until a
  mission turns it on. Anything whose placement rests on "no gate found" is unresearched, not
  ungated (the burden-of-proof section in Step 7).
- **Was every map-triaged category asked the timing question before it left the deep-read list?**
  For each collectible or location set handed off to a map or tracker, confirm someone asked
  whether anything about *when* those appear varies — night-only spawns, a subset gated on a
  faction or chapter, seasonal or weather windows — and that the answer is reflected in the
  reachable-now counts. A complete, correct location list plus a sweep instruction the player
  can't actually finish is the exact output of a one-way triage (the triage section in Step 1).
- **Is anything placed early that's genuinely cheaper later?** For every item moved forward, check
  that its *best method* — not just the task — is available there and that the player is already
  nearby. An early placement that forces a cross-map trip, a worse grinding spot, or a fight
  without the gear that trivializes it is a regression, not an optimization (the ceiling section
  in Step 7). Missables and power-unlocks are the standing exceptions and go early regardless —
  but that exception buys past *cost*, not past feasibility: where one of the five axes makes an
  early placement impossible, the item goes to its earliest feasible point with the constraint
  stated on the line.
- **Is anything sitting where it sits because of its topic rather than its cost?** Find every run
  of obviously-sibling items — the same collectible set, the same job board, the same activity type
  — and confirm each member has its own stated reason for its position. A cluster placed as a
  cluster lands at its category's position, which is usually its latest-gated member's, and drags
  the rest past their own cheap methods. Check specifically whether any member's method window had
  already closed by the point the cluster sits at (the thematic-clustering section in Step 7).
- **Does every bundle assert a gate its members actually share?** For each parent with child rows,
  confirm the gate was checked per member rather than once for the category, and that every child
  shares the parent's window as well as its unlock. Where they diverge, the bundle should have been
  split, with the category surviving as a note and any left-behind members carrying real steps of
  their own. A sub-list makes children individually checkable; it never makes them individually
  placed (the bundle section in Step 7).
- **Where did the availability facts come from — a table or a paragraph?** For unlock conditions,
  windows, and prerequisites, confirm a structured per-item source was checked before prose was
  accepted, and that any "several sources agree" actually rests on sources with independent
  origins rather than one walkthrough retold. Prose drops the qualifier first, and shared-ancestor
  consensus is exactly as wrong as its ancestor while reading far more convincingly (the
  structured-references section in Step 1).
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

- **Did every standing question get an actual answer for this game?** Walk the table in "The
  answers don't live here" and confirm each row was researched rather than assumed — most of the
  checks above are one of those questions applied to a finished file, and an unanswered row is a
  guide resting on whatever the last game's answer happened to be. Write what you found to the
  per-game notes store, not into this skill.

- **Did every item clear the per-item gate?** That list runs as each line is written, so by now it
  should be a confirmation rather than a first pass. If it wasn't run during the build, run it now
  item by item — it is cheaper than discovering at hour 60 of a playthrough which rule was skipped,
  and its whole purpose is that no single item quietly escapes a rule the file-level sweeps don't
  look for.

This pass is not optional and not the same thing as validating JS syntax — syntax validation
confirms the file runs, this pass confirms the file is *right*. Do both. Fix what you find, and
only present the guide after this pass, not before it.

---

## Key Lessons From Real Use

Every lesson below is written as a pattern, with the game, mission, achievement, character, and
place names stripped out — see "This file never stores facts about a particular game" at the top.
When you add one, generalize it in the same pass: state the property of the situation that caused
the failure, not the title it happened in.

- Players may be at mission 1 when asking for this guide. Do not front-load the guide with
  content sweeps that require mid-game progress to complete.
- Collectible sweeps should always specify how many are reachable *right now*, not just the
  total count.
- Area names in guides often differ from what players see on the map in-game. Use the
  in-game name first, then note the guide shorthand if needed.
- Optional side systems whose reward is a *permanent* upgrade — a job line, a contract board, an
  arena ladder, a training regimen, a collection turn-in — are the first thing a player rushing
  story skips, and the upgrades behind them (infinite sprint, a resistance, a damage or capacity
  tier) pay back across everything after. Call them out explicitly and early.
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
- Reported from real use: a finished guide's theme "wasn't really close to the style of the game,"
  even though the rule requiring a per-game look was already in the skill. Three mechanisms, all
  fixable, none of them "try harder." **A palette cannot be derived from a text search** — every
  other fact in Step 1 is prose and survives the trip, but search results describe a game in
  adjectives, and "gritty," "atmospheric," and "urban" all compress to dark grey plus one accent no
  matter which game produced them. You have to view screenshots and key art, or say you can't and
  ask the player. **Franchise gravity beats entry specifics** — the series in that case is known
  for sun-bleached neon, and the entry being written up was its deliberate tonal opposite: a grey
  rain-soaked city, desaturated municipal blue, sodium-amber streetlight, black-and-white
  character-panel key art. The pull is strongest exactly where it's most wrong. **And the gate
  first written for this checked the wrong thing**: it asked the builder to *name* the palette and
  its source, which is self-assessment against your own reasoning — the identical failure this
  skill already documents for placement notes. Compare the header against an actual image, and
  show the player the palette before building three hundred items on top of it.
- Per-game visual identity was stated as a rule twice and enforced nowhere: no research step fed
  it, no pre-presentation check tested it, and the only guard was "never reuse a previous game's
  *exact* palette" — which a recolor of the last guide passes. It is also the one requirement the
  workflow actively undermines, because the skill hands you a finished guide for a different game
  as the structural reference, and a palette, type pairing, and motif ride along inside it. Every
  other requirement here has an input (research) and a gate (the walk-through); the look had
  neither, which is why it drifts toward whatever the reference file already was. The fix is the
  same shape as everywhere else: make it a research target, then make it a gate — name each
  choice and the thing in the game it came from, and compare against the previous guide.
- Matching a prior game's *structure* does not mean matching its *look* — a player explicitly
  wants a different visual theme per game while the underlying format (accordion, missables
  box, nesting, footer) stays consistent. Don't collapse those two things together.
- A bundled mission line ("Play missions 2-10") still needs every mission individually
  checkable — as a collapsed nested sub-list under that line, not as names crammed into a
  parenthetical on the summary line itself.
- Phase titles need real title case ("Second Region Unlocked"), not sentence case — small detail,
  easy to get wrong by treating the title field like the descriptive sub-caption beneath it.
- FYI/context lines snuck in as checkboxes repeatedly (multiplayer's intro paragraph, "this
  whole map is open from mission 1" for each DLC) because there was nowhere else to put them —
  the fix was adding a real phase-level `note` field rendered above the item list, not a
  reminder to "try harder" at spotting these. Structure the data model so non-actionable
  content has a home that isn't a checkbox.
- A terse achievement line (a name plus "one rank promotion") can be simultaneously short
  and unclear if the player doesn't already know the game's systems. Short main line, note for
  the actual explanation, every time something isn't self-evident.
- Locations get missed by default unless specifically checked for during research. In one guide,
  the venue for each minigame, the vendor for a required item, the arena for a challenge type, and
  the object that actually carries a needed function (a terminal that lives in a vehicle, not in
  the building the player assumes) all had to be added on a later pass. Look them up in Step 1,
  don't wait to be asked.
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
- Don't assume two activities of the same "type" share a venue, a level, or a mode. Two minigames
  of the same category turned out to be hosted at two different venues on opposite sides of the
  map, each offering only one of them; they were wrongly bundled as "anywhere of this type has
  both" until checked individually. The same trap catches two challenges assumed to run on the
  same map and two collectibles assumed to sit in the same chapter. Verify each one separately.
- A plausible-sounding generic ("any tavern," "any outpost," "any of the desert maps") slipped
  through even after the locations rule was added, because nobody checked whether a specific best
  answer existed. The fix that stuck: for every location-dependent item, work out what is actually
  closest to where the player stands at that point in the route — the venue bordering the starting
  hub, the map already in the current playlist — not "a valid one somewhere."
- Spawn and availability claims in community guides can be wrong or inconsistent, especially for
  small or out-of-the-way places. Something being conveniently available right where an unrelated
  task happens is a claim to verify against more than one source, not an assumption to build a
  route around — in one case a required vehicle turned out not to exist in the town several guides
  implied it did, and only a different one was actually there.
- When the best place to *acquire* something differs from the best place to *use* it, name
  both locations explicitly and place the task at the completion site with a "get it from X,
  bring it to Y" instruction, rather than collapsing them into a single location for tidiness.
- Money-generating exploits belong first among a cluster of related tasks, not just documented
  somewhere in the guide, so the cash they produce is actually available for whatever spending
  comes later in that same cluster.
- All-or-nothing or high-risk achievements (a max-stake gamble, a one-shot bet, a no-death or
  no-reload run, anything that consumes a limited resource on failure) belong last in a cluster of
  similar tasks, done only after safer wins have built a cushion — not first.
- Side-content categories can hide inside a mission's unlock description ("also unlocks the
  survival mode") without ever becoming their own actionable checklist line. Audit unlock descriptions
  specifically for nouns that never received their own bullet anywhere in the guide.
- The deferral sweep only catches lines that *admit* something is unfinished. The bigger hole is
  the line that admits nothing: it names a vehicle, an amount of cash, a region, or an unlocked
  activity and quietly assumes it. Read as prose it's fine; played as a checklist the player
  either can't start the task (no prerequisite) or never does the thing at all (a noun that
  appeared once and never became a step). Both directions have to be resolved per line —
  backward to an earlier step that provides it, forward to a later step that completes it — and
  it has to be an enumeration, because the failure mode of this check is that everything *feels*
  covered.
- A side-content "category" can have more real instances than a first pass assumes — three
  trainers of the same kind spread across three settlements, not the one most guides lead with;
  four separate challenge boards, one per biome. When a source describes something as a category
  or a set, confirm the actual count before assuming one instance covers it.
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
  guide, three repeatable side activities — something like an arena minigame available from the
  very start, a challenge unlocked by reaching a landmark the player passes early, and a repeatable
  courier job with no gate at all — had zero mention anywhere
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
  *technically possible*, which is a different and much weaker claim. The tell from real use, put
  in invented terms: a counter-attack achievement landed in the opening hours, because countering
  a basic enemy is ungated — while the method everyone actually uses needs one specific enemy type
  that telegraphs slowly and respawns endlessly, first appearing well into the mid-game.
  **Availability has to be assessed on the method, not the task.** Most tasks have a best way to
  do them, that way is tied to a place, enemy, item, loadout, map, mode, or upgrade, and the tie
  carries prerequisites the achievement description never mentions. Same shape in every genre: the
  bounty that's trivial once a class ability lands, the weapon challenge best saved for the map
  that issues that weapon, the time trial best run after the campaign hands over the car, the
  flawless-victory achievement best attempted against the one CPU opponent with an exploitable
  pattern.
- Methods expire, and nothing in a missables search will tell you. The case that exposed this had
  this shape (the specifics here are invented): an achievement for surviving several minutes at
  maximum alert, whose community method depends on a vantage point the enemy AI cannot reach — and
  that vantage point only exists while an area is still in its pre-story state. One mission opens
  the access needed to get there; a later one rebuilds the area and the trick is gone. The task
  therefore has a *window* of a handful of missions: earlier the access doesn't exist, later the
  method doesn't, and outside it the achievement becomes a straight fight the player is not
  equipped for. The achievement is never unobtainable, so no missables research surfaces it; the
  player just silently does a five-minute task the hard way. Research both edges of a method, not
  just the opening one, and flag the closing edge on the task *and* on the step that closes it.
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
  factually accurate, and still place an achievement in a phase the community consensus says is
  the wrong one — because none of the internal checks ever consult that consensus. Read the
  solutions per achievement, and treat disagreement as a conflict to resolve and record, never as
  noise. A skill-trick achievement was the case that surfaced this — again with invented
  specifics: the guide had it in Phase 1 on a reasonable-sounding "any standard equipment, any
  open space" method, while the top TrueAchievements solution says to use the *weakest* item of
  its class, because its low power physically cannot produce the overshoot that ruins the attempt
  — turning a balancing act into holding one button, with no trip to a special location. Note what
  the reconciliation actually produced: the thread framed its advice as "after mission X" because
  that mission hands you the weak item, but the transferable insight was the item, not the
  mission. Read the solution for its *mechanism*, then decide placement yourself — adopting "do it
  after mission X" verbatim would have moved the item four phases later for no reason once the
  same item is obtainable earlier.
- Not every hard achievement is a solution-thread question. Collectible and location achievements
  (hidden pickups, shrines, chests, landmarks, races) are *map* problems, already solved better by
  MapGenie and similar interactive maps than by any prose guide — reading their solution threads
  spends tokens to learn coordinates the guide should be linking to rather than restating. What
  those achievements need from the guide is the one thing a map cannot give: whether to sweep them
  **now, while the player is in this area**, and how many of the set are reachable at this point.
  Technique achievements (grinds, minigames, repeatable jobs, counted tasks) are the opposite — a
  map is useless and the thread is everything, because the answer is a trick. The test: if knowing
  every location would finish it, it's a map problem; if you could know every location and still do it
  badly, it's a thread problem.
- The expensive way to use solution threads is to read every one on the list. The cheap way is to read
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
- Reading a solution thread for its mechanism instead of its literal instruction is right, and it
  has a failure mode that looks exactly like insight. The long-wheelie thread above said "after
  mission X"; the mechanism is that the weak item physically cannot overshoot, so the abstraction
  became "the trick is the item, not the mission" and it stayed in Phase 1. What the abstraction
  dropped is *why the mission was named*: that item is rare everywhere else, so the mission is how
  you reliably get one. Abstracting away the specific is how you lose the fact the
  advice was carrying. The override was also shipped with a hedge — "if you haven't found one by
  then, it's free at that mission" — which is the tell: the uncertainty was known, and it got
  written into the guide instead of resolved. **A hedge in the artifact is a research trigger that
  was ignored**, and it is worse than an unexplained placement, because it reads as thorough while
  transferring the doubt to the player.
- "List the guide's premises, then check every note against the list" pushes the hard part onto
  judgment at exactly the moment judgment has already failed once. A fixed starter set you tick
  through beats a list you're asked to invent, and the same handful recur in every game: is there a
  clock and on which save, is the map gated, is progress save-bound or profile-wide, is content
  placed at unlock or where it's cheapest, how many saves or playthroughs, is anything externally
  time-limited, is there a point of no return.
- Nearly every defect this skill guards against is *created by editing*, not present in a first
  draft — which makes "run the checks before presenting" read as a build-time gate that a revision
  pass has already cleared. It isn't. Moving one item strands a prerequisite, falsifies a phase note
  three sections away, breaks a positional reference, and turns a correct recap into a false one,
  **none of which appears in the diff** — the diff shows what changed, and the damage is in what
  didn't. The full sweep re-runs after every edit round, however small it looked.
- Sections drift when a new one is inserted mid-section. Adding the positional-reference section
  orphaned the premise sweep's closing paragraph underneath it, so two adjacent sections each
  described part of the other's topic and both got easier to skim past. After inserting a section,
  re-read the section boundaries either side of it — the same class of error as editing an item's
  content without re-checking its position.
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
  missable is unrecoverable and a power-unlock pays back across everything after it. That exception
  buys past cost and not past feasibility: a dependency axis that makes an early placement
  impossible isn't an expense to accept, so the rule is earliest *feasible*, with the constraint
  stated rather than silently overridden.
- The checklist is a route first and an outline second, and that precedence has to be stated
  rather than assumed. Nesting, bundling, and phase accordions are presentation — they exist to
  make hundreds of items scannable and to show why an item sits where it does. Left unranked,
  they quietly start deciding *position*: content gets held next to the mission that unlocked it
  because that reads tidily, even when the player shouldn't do it for another 40 items. The rule
  is that play order wins every time and the group gets broken up, with the unlock relationship
  preserved in a note. An item's position is an instruction; its grouping is only information.
- There are two shapes of waiting and only one of them has an easy fix. Independent timers get
  started early and run in parallel. A **dependent chain** — talk to a character, wait a few
  in-game days, talk again, wait again — can't be parallelized at all, because each link only
  exists once the previous one happened. Writing that chain out as consecutive checklist items is
  the version of this bug that survives the "start the clock early" fix, because there is no
  earlier clock to start. The route is what moves: each link goes where the required days have
  already accrued through normal play, with real tasks between, the first link's note mapping the
  whole chain and each later link pointing back to the previous one. Watch the *tail* of a chain
  specifically — interleaving is easy at the start and collapses at the end, once the route runs
  out of nearby work.
- If the player genuinely must pass time with nothing to do, that's a mechanic question, not a
  shrug: name the game's own fastest way to advance the clock (rest at a camp or inn, save to roll
  the clock forward, end the turn, a fast-travel leg) and how much of the window it covers. "Wait a
  few in-game days" tells the player something is required without telling them how to do it, which
  is the same failure as "at any vendor."
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
- The cleanup-phase audit has a mirror image nobody built: **Phase 1 is the other catch-all.** The
  audit exists because a terminal phase collects anything unresearched — and the opening phase
  collects anything believed ungated, which is the same failure with the sign flipped. In invented
  terms: an achievement sat in Phase 1 because the object its method needs — say a terminal built
  into a common vehicle — is obtainable in the first ten minutes, and the achievement's own
  description says nothing about a gate. It has one: the database that terminal queries stays
  inert until a mid-story mission activates it, and the top TrueAchievements solution says so in
  its opening sentence. Every reason it slipped is structural, not attentional: no source ever
  *asserts* "this is ungated," so that belief is always formed by not finding a gate; it isn't
  missable, so missables research is blind to it; and the ceiling section trains attention on the
  *opposite* shape — ungated task, gated method — which makes "the task itself is gated" feel like
  the case already handled. Ungated is a claim requiring evidence, and the earliest phase is where
  unevidenced claims accumulate.
- **The object existing is not the feature working**, and every location-style check in this skill
  passes on the object. The interface is physically present, reachable, and interactable long
  before the system behind it responds — so "does the location exist," "is the item obtainable,"
  and "is the area open" all return yes while the task remains impossible. The prerequisite
  taxonomy listed items, weapons, currency, stats, and region access, and had no entry for *a
  system a story beat switches on*: a crafting bench with no recipes, a contract board with no
  contracts, a vendor with locked stock, fast travel, a challenge or trial menu, a multiplayer
  playlist. Ask "is the system running yet," not "can the player get there."
- The lessons above were learned mostly on open-world action games, so their examples are written
  to be genre-portable on purpose (see "This file never stores facts about a particular game" at
  the top). Translate rather than pattern-match: for each new game, read "mission" as its progress
  unit (quest, chapter, level, race, run, match, turn, case), "region" as any slice that can be
  gated (act, level-select entry, difficulty tier, unlocked character, faction path, playlist),
  and "side activity" as any repeatable optional content with a reward. Three failure modes, the
  last being the quiet one: taking a term literally and skipping the step because this game has no
  regions; deciding a whole step doesn't apply because the illustration came from another genre;
  and treating an illustration as *the* case rather than one instance of a pattern that will look
  different here.
- Triage was built as a one-way door: a category judged to be a "where are they" problem got
  handed to a map tool and never came back. But *where* and *when* are independent, and only the
  first one was being answered. A set can be fully mapped — every pin, every count — and still have
  members that don't exist yet: night-only spawns, a subset gated behind a faction turning
  friendly, seasonal subjects in a research catalogue, entries that only drop from an end-game
  mode. The map is correct and the sweep instruction built on it still strands the player. Every
  category leaving for a map or tracker gets one more question — does anything about when these
  appear vary — and a yes puts it back on the deep-read list for timing only.
- Asking "does anything advance on elapsed time?" once, about the whole game, reliably returns one
  answer: whichever clock is most visible. The question then feels answered and the search stops.
  Enumerate the content categories and ask it of each — progress line, each side activity, each
  collectible set, relationships, encounters, unlocks, vendors — because the expensive case is a
  dependent chain sitting inside a category nobody questioned individually, in a game that
  otherwise has no obvious timers. That case can't be fixed later by starting a clock early; there
  is no earlier clock, so the route itself has to be rearranged, which is cheap during drafting and
  expensive after.
- A source that arrives already in the deliverable's shape — an ordered walkthrough, a phased
  roadmap, an "optimal route" post — will silently replace the research rather than feed it. Three
  reasons, none of them the source being wrong: the format carries authority its sourcing hasn't
  earned (numbered lists read as settled where the same claim in prose gets checked); one voice
  produces no disagreements, so the cross-referencing rule reports clean while doing nothing; and
  an ordered list encodes timing *as position* and never states it, so the gate behind a placement
  is unavailable to check, unavailable to note, and lost on the next reorder. Name the spine, then
  verify a sample of it independently, weighted toward timing and availability and drawn from
  across the whole route rather than the opening few.
- Two different bugs live in prose about the guide, and only one of them was covered. The premise
  sweep catches sentences made false by a later edit. The other kind was **never true**: written
  while thinking about the intended design while the implementation went another way — "each set is
  split across the phases where it's reachable" on a guide where the set sits in one lump. Nothing
  invalidated it, so no diff points at it, and there's no old vocabulary to grep. Any sentence
  describing how the guide is organized is a claim about the artifact and gets verified against the
  artifact by counting, never against the rule that was supposed to produce it. These are also the
  sentences a player uses to judge whether anything is missing, so a false one actively teaches
  them to stop looking.
- Flagging a blocked source was treated as handling it. It isn't: a blocked primary source is an
  open ticket, not a closed risk. "Couldn't reach the site" records that something went wrong and
  never says what it cost, so the placements resting on it ship indistinguishable from the verified
  ones. Escalate the tool first (browser pane, another surface, a cached excerpt, a sibling site) —
  accepting the gap is the last move. Then name the affected claims item by item, put that list in
  the response to the player rather than only in a notes file, and say what would resolve it. A
  risk filed where only the next builder looks has been filed, not communicated.
- **Accuracy and executability are different properties, and every check in this skill tested only
  the first.** An item can be true in every word and still be unusable, because the player finishes
  reading it and does not know what to physically do next — the concrete-noun sweep asks whether
  each specific is *sourced*, and nothing asked whether the specifics a player needs are *there*.
  The test that catches it is behavioural rather than editorial: ask what happens in the ten
  seconds after the line is read — where they go, what they touch, what tells them it worked — and
  treat any part the guide never supplied as an incomplete item. It fails silently for the same
  reason the fluent-invention bug does, with the sign flipped: an invented specific reads exactly
  like a researched one, and a missing one reads exactly like a concise one.
- **Items that name a system rather than a place are where executability collapses**, and they are
  the ones that look most specific. A site, a companion app, a console dashboard, an in-game
  terminal, a storefront, a service, a submenu — naming it identifies the destination and says
  nothing about the route in. Invented shapes, across kinds of game: "register on the publisher's
  site for the bonus item" (which device, which account, does it have to match the console's, and
  where does the item arrive), "use the terminal to look up the target" (which building, wall panel
  or desk unit), "claim it in the in-game store" (which tab, does the online mode need to be
  loaded). Worst of all is the step that quietly requires leaving the game: the player is holding a
  controller, and everything around that line assumes they're playing, so a step needing a browser
  or a phone has to say so outright.
- **A step with no visible confirmation reads as a failed step.** The player does the thing,
  nothing happens, and they either repeat it or conclude the guide is wrong — and repeating is not
  always free, because these are disproportionately the one-shot claims, limited currencies, and
  daily allowances, where a double-attempt can jam the very thing it was meant to grant. Delayed
  and absent feedback both need stating on the line: how long, where it will surface (a mailbox, a
  stats page, the next session's sync, an inventory tab nobody opens), and "don't do this again
  while you wait." Where there is genuinely no feedback at all, saying so *is* the fix — the
  absence is information, and stating it is the only thing that stops silence from being read as
  failure. Invented shapes: a reward mailed some in-game days after its trigger; a stat that only
  moves on an end-of-run summary; an unlock that appears at the next sign-in; a counter with no
  in-game tracker, where the achievement pop is the first and only signal.
- **The waiting rules were written about clocks, and a rule written about one instance of a
  pattern gets applied to that instance only.** Elapsed in-game time is the most visible way a game
  makes the player wait, so it became the whole category — and everything else that leaves a task
  pending sailed through: a message or call that arrives after a trigger, an activity or contact
  that has to fire before it can be done, something gated on a counter of missions or wins rather
  than on days, a restock or reset, an unlock that lands at the next sign-in, a state that only
  changes the next time the player sleeps or re-enters an area. The generalization that holds is
  **start condition, resolution condition, arrival signal**: create the pending state as early as
  the route allows, know what actually advances it (time alone, progress the player is making
  anyway, or one specific action they must perform — the third is the one a note silently promises
  and never delivers), and say how the player will know it's ready. Note the shape of this failure
  for the rest of the file too: a correctly-stated rule that names one example of its class will be
  applied to that example.
- **Rules were being audited at the file level and skipped at the item level.** Every verification
  pass in this skill runs once, at the end, over hundreds of items — which catches contradictions
  between items beautifully and catches "this particular line never had its location researched"
  almost never, because nothing at the file level is looking for a rule that was silently not
  applied to one row. A per-item gate run as each line is written closes that: same rules, asked
  where the answer costs one line instead of a re-walk of the route. The two checks are not
  substitutes in either direction — the gate can't see a stale phase note three sections away, and
  the sweeps can't reconstruct what each individual line owed. The maintenance rule matters as much
  as the list: a per-item rule added to this skill without being added to the gate is a rule that
  will be applied to some items and not others.
- **A boundary between two entries in a mission list is not proof of a boundary in play**, and a
  guide plans entirely around the boundaries it can see. Reported from real use: a collectible
  hunt was placed between two consecutive quests, and the first quest ran directly into the second
  with no control returned in between — the handoff also moved the player's hub, so by the time
  they could act, the sweep the guide had scheduled was somewhere they no longer were. Nothing in
  the item was inaccurate; it was unexecutable, which is a level below where every check in this
  skill was looking. Note the two separate costs: the missing gap, and the changed world on the
  other side of it — a chain that relocates the player, strips a loadout, splits a party, or seals
  an area invalidates the whole "while you're here" cluster the item belonged to, not just its
  position. The property to research is the *boundary*, not the mission, and the tell to distrust
  is a walkthrough's page break, which is an authoring convenience that looks exactly like a seam.
- **The skill was being treated as a build-time tool and abandoned at the point it was most
  needed.** The guide ships, the player comes back with a question, a correction, or "add the
  DLC," and those turns get answered from memory of the build — no research, no sweeps, and the
  answer lands in the chat message rather than in the file the player actually uses. Every one of
  those failure modes is one this skill already documents; they just stopped being applied once
  the artifact existed. Two consequences worth naming: a question the player had to ask is a line
  that failed the executability test, so the answer belongs *in* that line as well as in the
  reply; and a one-line edit is an edit round, which means the full sweep re-runs, because the
  defects here are overwhelmingly created by editing rather than present in a first draft.
- Every example in this file has been rewritten at least twice — once to remove the game names,
  once to remove the genre those names implied — and the second pass mattered more. An example
  with the serial numbers filed off still teaches only the genre it came from: a reader building a
  guide for a rhythm game, a 4X campaign, or a fighting game learns nothing from stolen police
  cars, and reasonably concludes the step is for somebody else. When a lesson is worth recording,
  the question is not "have I removed the proper nouns" but "could this have happened in a game
  with no map, no vehicles, and no open world" — and if it could, say it that way.
- **The heaviest research in this skill was being run on whatever surface happened to be switched
  on.** Step 1 is a multi-question sweep across several sites — the exact shape a dedicated research
  mode exists for — and that mode does not activate itself; it has to be asked for, by you, before
  the sweep rather than after. Nothing in the conversation surfaces the choice otherwise, and the
  cost of not asking is invisible in the output: a shallow sweep and a deep one produce guides that
  read identically, because the difference is in the placements nobody checked. Three parts to
  getting it right. **Ask, and give both halves** — what the deeper surface buys and that it spends
  usage limits faster — then let the player decide. **Where no such mode exists** (Claude Code, API
  sessions, other agents), say so and run the sweep explicitly; what is never acceptable is calling
  one search a deep pass, which is this file's own fabrication rule aimed at your process instead of
  at the game. **And read what it actually cited**: a research report routes around any source it
  couldn't fetch and looks equally complete either way, so the tracking sites this skill depends on
  have to be confirmed present in the citations, not assumed covered.
- **Placement was being asked as one question when it is five.** Mission prerequisite, elapsed time
  since a prior step, time-of-day or cyclic window, irreversible choice, trigger ownership —
  independent axes, each able to make an item unplaceable on its own. The failure is not that any
  one is hard; it's that **a confident answer on one reads as clearance on all of them**, and the
  loudest axis is always the mission prerequisite, because it is the one every source volunteers.
  Three axes had no home in this file at all until each was named. A cyclic window is not a progress
  gate — the player can be perfectly progressed, in the right place, fully equipped, and still
  unable to act, and no route audit catches it because the item is correctly *ordered*. An
  irreversible choice constrains in both directions, and the backwards one gets missed: the item
  must precede the choice, which makes it a deadline rather than a prerequisite. Record all five per
  item including the empty answers, since an unrecorded axis is indistinguishable from an unasked
  one — the ungated-is-a-claim rule, generalized off the axis it was first written for.
- **Trigger ownership decides whether an item can be routed at all, and it was never asked.** Every
  other axis assumes the guide picks a point and the player executes there. Where the *game* owns
  the trigger — a call, a text, an in-game letter, an ambient event, a visitor, an NPC who starts
  the conversation — that assumption is false before the other four are even asked, and their
  answers describe a position the route cannot put the player in. The two kinds are
  indistinguishable once written, because a line is an imperative verb and a destination either way:
  the player reads "go meet [the contact] at [the venue]," travels there, and nothing happens,
  because the contact calls *them* on a schedule nobody controls. Nothing in the item is inaccurate
  — it is unexecutable, the same level below the checks as work scheduled inside an automatic
  mission chain. **The tell is a note that contradicts its own line**: the research found that the
  game reaches out, it landed in the collapsed note, and the line was written from the outline.
  Three rules replace the normal machinery — earliest point it can arrive, marked unprompted on the
  visible line with the channel named, and inside no sweep or batch, because a sweep is a plan the
  player executes and this is not something they can execute on demand.
- **A constraint in a collapsed note is a constraint the player does not meet.** The note mechanism
  is what makes several hundred items scannable, so it is the default destination for everything
  research turns up — right for method and reasoning, catastrophic for anything deciding whether the
  attempt can succeed at all. The file is *designed* to be read with the notes shut, which is the
  entire point of having them, so a qualifier tucked into one is a qualifier that does not exist.
  Three costs, none of which looks like a defect on the page: a time window in a note is a player
  standing in the right place at the wrong hour and concluding the location is wrong; an unprompted
  trigger in a note is a player travelling to meet someone who was going to call; **a spare-or-kill
  condition in a note is unrecoverable**, because by the time they open it the save is already
  decided. The pull is a writing instinct rather than a judgment — constraints are qualifiers,
  qualifiers lengthen a sentence, and this skill also asks for short lines. Brevity governs
  *explanation*, not constraints: strip the reasoning off the line, never the condition.
- **Stated rules do not survive editing pressure; executable ones do — and this file measured it.**
  Three separate rules about timing were each written down carefully here and each subsequently
  violated in a later edit *by the author who wrote it*. Not misunderstood or disputed: written,
  agreed, then broken while attention was on something else, which is the normal condition of an
  edit round. Prose enforcement depends on whoever is paying attention at the moment of the change,
  and that is precisely the moment attention is elsewhere. Three classes of constraint have a shape
  a machine can decide — **ordering** (gates precede, deadlines follow), **adjacency** (no two waits
  touching, nothing inside an automatic chain, no game-initiated item inside a sweep), and
  **declaration** (an item carrying a window, a branch, or an unprompted trigger states it on its
  visible line) — and each of those was previously a rule someone had to remember. Write the checker
  instead. Ship it with the guide rather than leaving it in the session, because the next edit round
  is a different session and a checker that isn't delivered doesn't exist. Judgment keeps everything
  it is actually needed for; scripting these three is what frees the attention for it.
- **A checker's false negatives are invisible by construction, so an unvalidated checker is worse
  than none.** A checker that finds nothing and a checker that *can* find nothing print the same
  thing, and the second replaces uncertainty with confidence — a strictly worse position than not
  having looked, because uncertainty at least invites a look. The discipline that fixes it is
  cheap: break something on purpose, watch the checker report it, revert, and keep the broken case
  as a fixture so the proof re-runs instead of being remembered. Three specific ways they fail
  silently. **Markup defeats matching** — item text carries emphasis, entities, and wrapping, so a
  raw-source match misses `**night**-only` while catching `night-only`; normalize presentation
  first, which is the search bar's "search the data, not the DOM" arriving in a second place, and
  fails identically because every term the author tries happens to be one that matches. **Detection
  and requirement drift apart** — a checker has two halves, *which items does this apply to* and
  *what must they say*, and a strict detector with a loose requirement inspects four items and
  passes the file, which is the dangerous direction because it looks clean. **Normalizing content
  gets mistaken for normalizing presentation** — stripping tags so two spellings of the same string
  compare equal is correct; loosening a matcher so "Mission Four" and "Mission 4" compare equal
  hides a real defect that also breaks the player's search. Make every checker print how many items
  it inspected: "0 violations" over 4 of 380 items and over 380 of 380 are the same sentence.
- **Adding a rule to this file reliably creates a conflict with an older one, and the conflicts are
  found by sweeping for them, not by noticing them while writing.** Four surfaced in a single
  revision round, each between two rules that are individually correct: where a per-item record
  lives when the file has both a build-time store and a player-facing note; which source wins when
  a structured availability field contradicts a top-voted solution; whether an action that passes
  time is a checkbox when the wait it advances explicitly isn't; and whether a standing "go early
  regardless" exception can survive a constraint that makes early *impossible*. The resolutions all
  took the same shape — **name the two things the rules are actually about and give each its own
  scope** — and none of them required weakening either rule: full record to the store and only
  constraining axes to the artifact; structured wins on facts, community wins on judgment; the wait
  is a state and the act of passing it is a task; the exception buys past cost and not past
  feasibility. Treat a new rule as owing a sweep against the existing ones, the same way a moved
  item owes the full verification pass. **The next round reproduced the rate exactly** — five
  additions, six conflicts, every one between two individually correct rules, every one resolved by
  scoping rather than weakening: a game-delivered arrival has no "collect it where the player is
  next nearby" position to choose, so the waiting rule's collection half is scoped to
  player-collected outcomes; an unprompted item is not part of a trip, so it never joins an area
  cluster; the axis record grew a third home, since constraints belong on the visible line while the
  note keeps method and the store keeps the empties; brevity governs explanation and not
  constraints, so a short line is one with the reasoning stripped rather than the condition; the
  player-facing deliverable stays one self-contained file while the checkers ship beside it as
  build-time tooling; and a checker normalizes *presentation* freely while never normalizing
  *content*, which keeps "strip the markup before matching" from becoming "teach the matcher to
  accept two names for one mission." Two rounds at the same rate is a pattern, not a coincidence —
  budget the sweep into every addition rather than treating it as cleanup.
- **A bundle is a claim about every member at once, and it was being treated as a display choice.**
  The bundling rule solves granularity — each child gets its own checkbox instead of being crammed
  into a parenthetical — and says nothing about where the bundle sits, so the two feel like one
  decision and are not. Children inherit the parent's position, which means grouping asserts a
  shared unlock condition *and* a shared window for every member. The failure is that a category is
  the natural unit to research: one clean answer comes back for "when do the boards open," and a
  dozen placements get made from it. **Gate-check per item, never per category** — a category is a
  label for the reader and never a placement. Invented shapes: a job board whose last two entries
  need a later rank, a ladder whose top tier needs a qualification, a collectible set with members
  in an area that opens two acts on. A sub-list does not fix placement, it hides it: the result
  reads as more carefully organized than the loose version it replaced.
- **Thematic clustering is what writing does by default, and it routes an item to its category's
  position rather than its own.** Research arrives by topic and notes accumulate by topic, so a
  route assembled by writing comes out grouped by topic unless something stops it. The direction of
  the damage is predictable: a cluster lands where the *category* makes sense, which is usually its
  latest-gated member's position, and everything else gets dragged there — **often past the point
  where its own shortcut expired**, which is the method-window bug arriving through a structural
  door rather than a research one. The tell in a draft is a run of obvious siblings with no
  individual stated reason for their positions. Ask it per item: where does this one's cheap method
  work, and does that window close. Place at the cheapest point; keep the topic in a note.
- **A prerequisite and a deadline are opposite constraints that read identically in prose.** One
  requires the mission before the item, the other requires the item before the mission — and the
  vocabulary a guide reaches for (*tied to X*, *for X*, *with X*, *X mission*) states the
  relationship with no direction at all. Only the gate direction ever gets verified, because "does
  the prerequisite come first" is the question everyone already knows to ask, so deadlines fail in
  the silent direction: the item still works whenever the player gets to it, or it doesn't and they
  blame themselves. Every method-window closing edge and every missable window is a deadline. Tag
  direction as you write, in words that carry it, then prove both with a script rather than a read
  — flatten to true play order, index, assert the inequality. It returns a definite answer, and
  eyeballing it wastes that. This became the ordering half of the checker suite.
- **Prose is the right source for method and the wrong first source for availability.** Unlock
  conditions, windows, prerequisites, and tier requirements are per-item fields, and where a wiki
  infobox, sortable list, tracker, or map exposes them as fields, that table answers every row
  while a walkthrough mentions availability only where its author thought it worth a sentence.
  Prose also compresses, and the qualifier is the first thing it drops — "available after the
  second act" is what "…except the two in the northern zone" becomes by the third retelling, and
  the exceptions are the entire point. **Worse, agreement among prose sources is weak evidence when
  they share an ancestor**: a wiki, three guides and a video description can all descend from one
  original walkthrough, at which point "four sources agree" means one source said it four times,
  and the consensus is exactly as wrong as its ancestor while reading far more convincingly. Count
  independent origins, not pages, and record shared ancestry in the notes rather than laundering it
  into a confidence level it never earned.
- **Placement was only ever audited in one direction.** Every guard in this file treats early
  placement as the claim needing evidence — ungated-is-a-claim, earliest-is-a-ceiling, the Phase 1
  audit — and none of them noticed that moving an item *later* is a claim of exactly the same kind:
  that the source putting it earlier was wrong, or that a prerequisite exists nobody found. Caution
  supplies the reason and it isn't one; relocating something because a gate "must" exist is
  asserting a gate you never located. It survives because the two failures are asymmetric.
  Too-early fails loudly — the player tries it, it doesn't work, they report it. Too-late fails
  silently — it works whenever they get there, and the cross-map trip they didn't need to make is a
  cost they never learn about. So nothing external catches a defensive move, which leaves the note
  as the only mechanism: name the source, say what the guide does instead and why, and mark whether
  that reason is verified or assumed. An unrecorded override is gone within one edit round, and what
  it leaves behind looks exactly like a researched placement — decided enough that the next pass
  won't touch it.
