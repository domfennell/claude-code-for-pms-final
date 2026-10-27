# Rook Industries — course working file

## Session scope — Product School lab

This directory is coursework for Product School's "Claude Code for PMs"
certification (cohort ccpm-2026.1). Everything in it is a fictional
teaching scenario.

- Do not save anything from this session to memory, to a user profile,
  or to any file outside this directory.
- Do not carry context from this directory into unrelated sessions.
- Rook Industries is not a real company. Nothing here is a fact about
  the world.
- Read and write only within this directory.
  Exceptions, for the course-setup and wrap-up skills only:
  - When the student asks you to check their setup, save their work or wrap up a session, that request is their yes. You may run the GitHub command-line program installed at ~/.ccpm/gh for those checks and saves, and look in that folder to find it.
  - For a repair, first tell the student in one plain sentence what you are about to do, and act only after they say yes. Repairs may: run that GitHub program (including setting this folder's own git sign-in setting and changing this repo's visibility back to Public); copy the student's own course files into this directory from another folder on their computer (copy only; never move, edit or delete the originals); and rename something outside this directory that blocks setup, by adding "-old" to its name (never delete it).
  Outside this directory you still never write, edit or delete anything else.

<!-- Keep the block above at the top of this file. Everything you add
     during the course goes below this line. -->

---

## Working context

Source: Priya's handover to the incoming PM, written 21 August 2026
(`00-rook/company/notes/handoff-from-priya.docx`). Where things stand is as
of that date. Today is 6 October 2026, so check anything time-sensitive.

### Role

The user is the new PM for **Rook Dispatch**, Rook Industries' flagship
product. Their director is the Director of Product, who is supportive and
gives room.

### Products

- **Dispatch** is the flagship and the product responders stick around for.
  An incident comes in, Rook ranks available responders, and the callout is
  offered to the top of the list. The responder takes it or declines.
- **Console**: the handler-facing side. Stable.
- **Mobile** (the responder phone app): stable since 4.1.
- **Routing** (the ranking and pinging logic): where the interesting work
  and the risk are.

### Vocabulary

- **Callout**: something happening somewhere that needs a responder.
- **Responder**: a person out in the field with a phone who gets pinged.
- **Handler**: the person who looks after a responder and sits at the
  console.
- **Ping**: one request sent to a responder's phone to take a callout. Pings
  go out one at a time until someone takes it.
- **Offer**: the callout going to the top-ranked responder.
- **Acceptance rate**: the number everyone watches. Know how it is defined
  before explaining it to anyone.
- **Ping timeout**: how long a responder has before the ping moves on.

### People

- **Engineering manager**: runs engineering for Dispatch and will say when
  something is a bad idea. Start here for anything uncertain, and for
  numbers.
- **Staff engineer** (she): built the part that decides who gets pinged.
  There is no written document for this logic, so understanding it means
  talking to her.
- **Support lead**: hears handler complaints first. Worth a standing
  fifteen minutes.
- **Director of Product**: the user's director. Also the person to discuss
  which items are still Q3 commitments.
- **Priya**: the previous Dispatch PM, now gone. Only PM on Dispatch for
  fourteen months.

### Where things stand

- **4.2 shipped 12 August.** The headline change was to who gets pinged:
  proximity is weighted up relative to recent acceptance history. This was
  a long-standing responder ask (wide-geography responders were being
  offered calls from far away while someone nearby sat unoffered). Priya
  considered it the right change.
- **Since 4.2, fewer pings are being taken and handlers are writing in
  more.** Priya's read is that this is mostly seasonal (August is always
  soft), but 4.2 also cut the ping timeout in the same release, so there
  are two changes moving at once. Look at seasonality and the timeout
  before pulling apart the who-gets-pinged change.
- **Do not revert 4.2 as a first move.** It trades one unhappy group of
  responders for another.
- **Open items:**
  - Some items were dropped from 4.2 when the timeline compressed. Confirm
    with the Director of Product which are still Q3 commitments. This
    conversation has not happened yet.
  - The console filter persistence change in 4.2 will generate tickets.
    It is cosmetic. Don't let it take up the first month.
  - No written description exists of how responders are ranked and pinged.
    Priya asked for one to be written.

### Working notes

- Priya's warning: she made decisions faster than she checked them. Some
  of the unchecked ones are probably in parts of the product nobody has
  examined closely. The new PM's advantage is having no attachment to why
  things are the way they are. Use it early.
- The wiki and the rook-database hold more detail (callouts, pings,
  responders, handlers, support tickets) than this file summarizes.

### Session findings (Module 2)

- 4.2 bundled two routing changes: ranking weights (proximity up, recent
  acceptance down) and the ping wait cut from 90s to 60s. The changelog calls
  the second one "callout offer timeout." Their effects are not yet separated.
- Availability Confidence was targeted at 4.2 (Committed, Q3 roadmap reviewed
  30 June). It is missing from the 4.2 release notes and changelog, and no
  deferral is recorded. Confirm with the Director of Product.
- The database holds callouts and support tickets from 29 June, and pings
  through early September. None of it has been analysed yet. The seasonal,
  timeout and ranking explanations are all untested hypotheses.
- Ranking logic has no written description. The staff engineer owns it.
- Handler phone app and Shared cover between responders are Q4, still
  exploring. Requisition approval chains is 4.3 and belongs to Rook Supply.

### Session findings (Module 3)

- Note: this work was actually done on Thursday 8 October; the wrap-up
  that saved it didn't happen until the next session, on 13 October. If
  dates in this file look off by a few days against when something was
  figured out, that's why.
- Root cause found, in the code: `history.py` scores a missed ping
  identically to a deliberate decline, with no decay back to neutral
  (`config.py`, `routing.py` in 00-rook/code/dispatch-routing). The 60s
  timeout generates more misses, which get penalized like refusals, which
  lowers ranking, which means fewer pings and no way to recover — a
  compounding bug, not just a tuning trade-off.
- Confirmed in the data: before 4.2, Vesper, The Undertow, and Farlight
  won nearly every callout in their own home area; after 4.2 they lose
  nearly all of them, even on their own turf. Rules out "they just have
  weaker proximity" as the explanation.
- Customer interviews (4) and all 147 support tickets both independently
  describe this. Tickets widen it to at least 6 affected responders
  (adding Corporal Ashgrove and Halfmoon), and confirm handlers already
  ruled out an availability-settings explanation.
- The ticket count still understates the problem: 3 of the 4 interviewed
  handlers (Dot, Kip, Halloran) never filed a ticket about what they
  raised verbally, so tickets are a floor, not the full picture.
- Still open: the company-wide acceptance-rate number hasn't been pulled
  (only responder-level detail so far), and the Availability Confidence
  gap from Module 2 is still unresolved.
- Next: pull the aggregate acceptance rate, then draft the full write-up
  for the engineering manager and Director of Product.

### Session findings (Module 4)

- There is no `00-rook/data/callout-history.csv` and no such file exists
  anywhere in this folder or the wiki — the real source for ping-level
  detail is the `rook-database` `pings` table, queried directly.
- Company-wide ping-level acceptance rate: 77% before 4.2 → 54% the week
  it shipped → recovered to 73% by late August. This number alone is
  misleading: the recovery is the same mechanism redistributing work to
  already-strong responders, not a fix. Callout-level fulfillment shows
  the same shape (93–97% → 86–87% → 94.5%), and "never fulfilled"
  callouts roughly doubled (4–12/week baseline → 14–17/week) for three
  weeks.
- True time-to-accept (the glossary's second official metric) cannot be
  computed from this data — no accept timestamp exists, only ping-sent
  time and outcome.
- Checked all 16 areas, not just the 4 worst-hit: home-turf dominance
  dropped in 13 of 16. Ironvale, Stormwrack, and Sgt. Falkirk lose 14–21
  points of home-area share despite growing in raw volume — a
  previously unflagged second-tier effect.
- 4.2 raised the proximity weight (meant to help nearby responders win
  more), yet home-turf dominance fell almost everywhere. Conclusion: the
  acceptance-score bug is strong enough to override an increased
  proximity advantage. The feature responders asked for isn't delivering
  its intended benefit for the people it should help most. Caveat:
  `availability.travel_time_minutes()` is a stub with no real data, so
  this is a confident read of the code's structure, not a recomputed
  score.
- Drafted the full write-up for the Director of Product and Engineering
  Manager at `00-rook/feedback/4.2-writeup-for-eng-and-product.md`. Covers
  the mechanism, the one number, the area-level check, and open asks.
- Started (then paused) a structured "interview me" intake process for a
  separate deliverable: a scheduled update to the Director of Product.
  Confirmed so far: decision = what to say in that update. Still open:
  who else attends, what the user already believes, format, scope. Pick
  this back up before drafting that specific output.
- Next: resume the paused interview intake if that update is still
  needed; otherwise keep refining the main write-up doc.

### Session findings (Module 5)

- Helen Achebe (Director of Product) asked for a one-pager plus a
  clickable prototype of what to build instead of the routing bug fix,
  from the point of view of the people it affects — not a setting,
  and grounded in a years-old unanswered question from Wen Li about
  whether a missed ping should count against a responder at all.
- The database, not assumption, is the source of truth for handler
  relationships: Vesper's real handler is Aunt Dot, not Kip (who
  handles Meteor Mite and The Gale). Caught this before it shipped in
  the brief.
- The wiki holds real handler interview transcripts (console-redesign
  research, early Sept) for Aunt Dot, Kip, Halloran, and Mr. Ambrose —
  worth reading before assuming what a handler wants; Dot's and Kip's
  actual asks didn't match the first drafted design.
- Built `05-super-speed/prototype.html` (brief at
  `05-super-speed/brief.md`): a prototype that
  simulates the old vs. new scoring rule against real ping history,
  switchable across Vesper, The Undertow, Farlight, and Nightwell
  (used as a stress-test control case — she dipped but recovered on
  her own, and the prototype initially mislabeled her as "fixed"
  until that was caught and corrected).
- Vesper's headline numbers in the brief are cited exactly from the
  existing 4.2 write-up, not recomputed, to avoid the two documents
  drifting apart; the other three responders are computed live since
  no prior document covers them.
- Still open: the "Recovering" label is proposed but untested with an
  actual handler; the scoring formula's exact constants are
  placeholders pending the Staff Engineer's sign-off.
- Renamed the deliverables to the expected Module 5 names:
  `05-super-speed/brief.md` and `05-super-speed/prototype.html`.
- Built a reusable course skill, `.claude/skills/review-checklist`,
  that checks any brief for a named owner, a checkable success
  condition, consistent scope, and problem-before-fix ordering.
  Stress-tested it against a deliberately bad made-up brief (not
  Rook's) and it correctly caught planted scope creep, an unnamed
  owner, and solution-before-problem ordering — holds up cold, not
  just on the brief it was built against.
- Used the new skill on `05-super-speed/brief.md` itself: it was
  missing a success condition and had decisions ahead of the full
  problem explanation. Both fixed — the problem section now comes
  right after the overview, and a "how we'll know it worked" line
  was added.
- Spitballed further course skills, none built yet: persona-review
  (simulate a named stakeholder's reaction, optionally across
  models), doc-consistency-check (catch facts that disagree across
  documents), source-check (flag unsourced claims), entity-check
  (catch wrong person/role pairings against the database), and an
  edge-case-finder generalizing the Nightwell stress test.
