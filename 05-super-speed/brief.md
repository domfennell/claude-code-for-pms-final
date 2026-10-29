# Fixing the quiet-responder trap

*For Helen — before any code changes.*

## 1. Overview

If someone misses a call, we score it the same as them saying "no." There's no way back. We want to fix that for good, not just patch it. This also gives Dot a quiet heads-up when a ping goes out — something she asked for directly.

## 2. The problem, and why now

A missed call isn't a "no" — but we score it like one, and it never gets better on its own. People are stuck right now, today.

## 3. Decisions we need from Helen

| Decision | Our answer |
|---|---|
| OK this plan before engineering starts | Please OK it |
| Fix stuck people (like Vesper) right away, not just going forward | Yes — same fix, applied once |
| Who owns the lost-pay question | Engineering Manager + Support Lead |

## 4. What other teams still need to do

| Item | Who |
|---|---|
| Check the new rule makes sense | Staff Engineer |
| Check it answers Wen's old question properly | Staff Engineer + Wen |
| Build the real screens, once approved | Design / Engineering |

## 5. What we'd build

A missed call should count less than a real "no," and should fade away over time instead of staying forever. No one should get stuck with no way out. People already stuck get fixed right away.

**Aunt Dot (Vesper's handler), today:** Vesper looks unreliable. She doesn't know why, so she stops picking her.
**Aunt Dot, after:** she sees a small "Recovering" tag and just offers Vesper the call like normal.

**Vesper, today:** her calls stopped weeks ago, with no reason given.
**Vesper, after:** her calls come back fast, with one message: *"Your calls are back to normal — a routing issue affected you, and it's fixed."*

Dot also gets a quiet notice the moment a ping goes out for Vesper — not just her phone buzzing through the ceiling. That's something Dot asked for directly, not something we added on top.

This is two separate things happening together: a one-time catch-up that fixes Vesper's score right now, and an ongoing change so future misses fade instead of sticking. Both show up in the click-through, labeled separately.

**How we'll know it worked:** no responder's score sits near zero for more than 2 weeks without a visible way back.

*(Click-through: `prototype.html`)*

## 6. The numbers

| | Before | After |
|---|---|---|
| Calls per week | 12–14 | ~5 |
| Wins in her own area | 97% | 13% |
| Of the calls she gets, % taken | — | 29% |
| Odds she climbs out alone | — | 1 in 60,000 |

These are Vesper's exact numbers from the full 4.2 write-up, cited here rather than recalculated. The click-through also shows The Undertow and Farlight — two more real, independently-verified cases, computed live since no published figures exist for them yet.

## 7. Open questions

| Question | Who answers |
|---|---|
| Tell everyone affected, or just show the message? | Support Lead |
| Should this become our first written rulebook for ranking? | Staff Engineer |
| Is "Recovering" the right word for the tag? Not yet tested with Dot — needs a real check before build | Product Designer |
