# 04 · X-Ray Vision — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. Last session the numbers showed you what happened: a
ping used to wait ninety seconds and now it waits sixty, people
missed pings they used to catch, and missing one counts the same as
turning one down — so four responders stopped hearing from us
altogether.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

i should have wrapped that up when the previous session finished on thursday 8th october. please update to clarify this.

### 2.

save to github now so it's all done. then i'll wrap up again later on when this session finishes.

### 3.

Open 00-rook/data/callout-history.csv. Every row is one responder in one week: how many times we pinged them, and how many of those they took.

### 4.

within the repo or notion notebook, is there any data around the callout history that has ping information?

### 5.

is there a way we can visualise this in some sort of map/visualisation that shows the plans of pings pre-4.2 and post-4.2, along with who the ping was originally sent to, but who ended up taking it instead, and the respective home-bases/area as well to see which responder accepted pings in locations outside their own area?

### 6.

what's the "so what"?

### 7.

is there anything i'm missing/are there any other areas i should be examining? bear in mind that the desired output is a single number i'd submit to the product director, so this needs to be trustworthy. sanity-check your confidence as you go.

### 8.

yes, check both

### 9.

pull the time-to-accept numbers too. show them in a graph along with the other numbers we're discussing.

### 10.

now we have a general understanding of the share of the data and what might be happening, let's take a step back and compare the ping data with the transcripts and support requests that we examined previously. set it out in a tabular form so that easy to understand. in a column in the table, highlight any things you think could be false positves/negatives, i.e. that should be approached with caution.

### 11.

Taking a bigger step back...

<pasted_content id="89c2">
BEFORE ANYTHING ELSE: interview me. Ask ONE question at a time until you are 95%
confident you understand exactly what I'm asking for. After each answer, tell me
your confidence as a percentage and what is still unclear. Do not share findings
or start any analysis until you reach 95%. Then play back a one-table brief
(goal, audience, my hunch, scope, format, what is out of scope) and wait for me
to confirm. Cover: the decision this serves, who will read the result, what I
already believe, what format I want, what is in and out of scope, and any other
sources I know of.

CONTEXT: I'm the new PM for Rook Dispatch. Release [4.2] shipped on [12 August].
I need to understand what happened, to whom, and how big the impact is.

SOURCES: Use only the rook-wiki (Research interviews), the rook-database (pings,
callouts, responders, handlers, support_tickets), and the files in this folder.

STEP 1: Interviews. Read all of them. Group what the handlers are unhappy about.
For each theme give how many of the interviews raised it, one short quote,
and whether people volunteered it or were asked. Rank by count and by intensity.
Put anything outside Dispatch in a short "parked" list.

STEP 2: Tickets. Read every ticket body, not just the subjects. Group into themes
and count them before and after the release date, by week, by responder, and by
open or closed. Note repeated wording and which complaints nobody filed.

STEP 3: Pings. Compare before and after the release: pings by outcome (taken,
turned down, missed), per responder, the gap between pings, callouts nobody took,
and how often a responder is pinged in their own area. Also test what it is NOT
(time of day, position in the cascade, geography).

STEP 4: Bring it together. Make one table with a row per release change, written as
"I am a ___, trying to ___, but I cannot because ___, which makes me feel ___",
with columns for interviews, tickets, pings, and a verdict. Then make a second,
companion table of findings that did not fit the first.

STEP 5: Write the story at a 5th-grade reading level, then give me a confidence
score from 0 to 95 for each group of numbers, what would firm it up, and the data
we don't have and who to ask for it.

RULES: Name the source of every number. Label what is observed versus inferred.
Flag a small sample once, not repeatedly. Never try to identify the real people
behind cover identities (Security Policy 4.1). Don't save anything outside this
folder, and ask before sending or publishing anything.
</pasted_content id="89c2">

### 12.

deciding what to tell the Director of Product in a scheduled update

### 13.

stop this. i\ll pick it up again in a bit.

### 14.

based on what you know from our work thus far in this session, if the Director of Product asked tomorrow what Release 4.2 actually did to responders, what's the one number you'd put in front of her?

### 15.

if you HAD to put a percentage in front of her in terms of what happened to the impacted responders, and what sentence would you use to sum it up?

### 16.

Great. Continuing with the investigation, i want to add additional information to that which was included in the last session—tickets and pings illustrated in the table. I want to know more about whether or not they agree, and if/when the numbers actually move (perhaps a column for each).

### 17.

so if we were to compare the support tickets against the pings, with what confidence can we say that they agree with each other? When did people start writing in, and when do the numbers actually move?

### 18.

what would pulling the company-wide acceptance rate before and after tell us?

### 19.

before we step back into the interview, let's return to that output for the director of product and head of engineering. what would we put in it now based on what we know now from this session?

### 20.

when i come to wrap up this session, be sure to include this in github as a documented output—formatted in whatever way makes sense.

### 21.

pick one responder from the database who went quiet. I want to deep dive into their whole month, week by week, in plain english. set it out in in a way that would allow me to present it back myself to this responder.

### 22.

great. now give me the relevant data in a table to include the relevant numbers, e.g. job, pings, area of jobs, taken, turned down, missed, etc. and any other info you see fit.

### 23.

great. now do the same for a responder who did not go quiet. i want to underatdn how the direction changes for a responder who might be doing a bit better. Again a deep dive, week by week, in plain english. set it out in in a way that would allow me to present it back myself to this responder.

in additon, beyond the plain english reivew, give me the table format.

### 24.

is it worthwhile looking at the two datasets side-by-side?

### 25.

add this table to the write-up doc

### 26.

what about a schematic map with areas as nodes?

### 27.

is it possible to illustrate based on all areas, irrespective of whether they were affected or not, so we can see if there are any other things worth noting in the data? so all responders across all areas? im aware that this might become an overwhelmingly involved illustration, but at it's core, this prompt is to drill down into the data to sanity check that we're not isolating a ping blast map to only a few "affected" areas when there are others to be aware of.

### 28.

what does this tell us?

### 29.

one more thing. i want to understand, if I'd only asked for the number, not the rows, what would I have missed?
