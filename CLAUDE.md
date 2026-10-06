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
