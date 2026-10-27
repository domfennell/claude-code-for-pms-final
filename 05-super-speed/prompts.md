# 05 · Super Speed — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. You've spent three sessions finding out what went
wrong: the two piles of feedback that didn't agree, the numbers that
hid four people inside an average, and the code that settled it —
the shorter timeout is what did it.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

read 05-super-speed/director-request.txt and explain to me what my director wants to see

### 2.

what is she saying line by line. tell me what she means at each point in a table form.

### 3.

The note says this shouldn't just be a setting we quietly flip. Read the responder I picked from CLAUDE.md and use that name. Do not ask me which one. Walk me through what's still missing from the brief before this could actually get built.

### 4.

let's organise the brief as follows.

1. executive overview
2. decisions we need from helen
3. open items, decisions we need from other teams
4. problem we're solving for and why now
5. ideal state and plan to get there
6. supporting data
7. open questions with assigned owners

### 5.

this brief is hard to read. Let's simplify to where there's 1-2 sentences per section; we're bringing in the key data, tables are fine, and it's writing for a 9th year old.

### 6.

pretend you are helen. give this brief a read and provide feedback. to make sure i have a better confidence, as you are playing helen, i want you to do so using multiple models. don't come back to me until the different helens are aligned and you have clear guidance on what changes we need to make to this brief.

### 7.

rebuild the brief with these six fixes. not further. be sure to save it.

### 8.

let's re-organise the brief again as follows.

1. executive overview
2. decisions we need from helen
3. open items, decisions we need from other teams
4. problem we're solving for and why now
5. ideal state and plan to get there
6. supporting data
7. open questions with assigned owners

### 9.

great. cut it down in under one page. reading age 9.

### 10.

this brief is going to serve as the input for our working prototype with the fixes. before we build anything, read the brief and ask me clarifying questions on what we need to build until you are 95% confident.

### 11.

this is better. put yourself in helen's shows and consider:

1. Is this a solid prototype?

2. If Helen put this side-by-side with the brief doc, is it a fair representation?

### 12.

what would we change next in order to close the gap and move it towards being "solid"?

### 13.

agreed. discuss what we should do next.

### 14.

i can't see the note for the ping that just went out for vesper.

make vesper's phone look like a phone, i.e. portrait mode.

### 15.

this is better. put yourself in helen's shows and consider:

1. Is this a solid prototype?

2. If Helen put this side-by-side with the brief doc, is it a fair representation

?
3. is the lack of clickability within the dot dashboard holding anything back? it doesn't need to be—i just want to stress test that without it being a fucntional-vanity-metric.

### 16.

what does stress testing one non-obvious case look like? is this the thing that makes this 95% solid for helen?

### 17.

hmm. there should be continuity across the docs. why has this strayed?

### 18.

shiould we have used more "stubbed" data?

### 19.

previously you asked me about sliders when interviewing. what was that in relation to?

### 20.

so should they go in the prototype?

### 21.

what do you think helen would say if they were there?

### 22.

is it possible to rename them? answer before chaning anything.

### 23.

push and commited?

### 24.

Make a skill called review-checklist. When I point it at a brief, it checks that the brief: names who owns it, says how we'll know it worked, keeps the same scope start to finish, and explains the problem before the fix.

### 25.

how do you mean?

### 26.

just to check, is the skill we've created brief agnostic at present? i.e. could i point future briefs at it and it produces the relevant outputs? as opposed to being anchored to the existing brief.md?

### 27.

great. what can we do to improve the skill?

### 28.

let's stress-test it against against a quick and dirty made-up brief.

### 29.

based on the work we've done thus far, what other skills do you think we could create to improve efficiencies? just create anything; just spit ball.
