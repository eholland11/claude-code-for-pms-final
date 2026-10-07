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

Source: one file, `00-rook/company/notes/handoff-from-priya.docx` (Priya, outgoing PM,
written 21 Aug 2026; no overlap with the user). Everything below is from that note
unless marked _inferred_. Priya's views are opinions, not verified facts.

### The user
New PM for **Rook Dispatch** at Rook Industries. Inherits a product Priya ran alone for
14 months and says she "made calls faster than I checked them", so decisions in the
less-examined parts of the product deserve a fresh look. She advises using the
no-attachment advantage in the first month.

### Product
- **Dispatch** is the flagship and the product responders stick with. Flow: incident
  comes in, available responders are ranked, the callout is offered to the top of the
  list, the responder accepts or doesn't (the "ping").
- Surfaces: **console** (stable) and **mobile** (stable since 4.1). **Routing** (the
  ranking and ping logic) is where the interesting work and the risk are.
- Headline metric: **acceptance rate**. The user needs to be able to explain it early.
- Routing code is in `00-rook/code/dispatch-routing/` (not covered by the handoff;
  read it before claiming how ranking works).
- Only Dispatch is described. No other Rook products are mentioned in the source.

### People (roles only; the note gives no names)
- **Engineering manager**: runs Dispatch engineering. Candid. First stop when unsure.
  Can usually pull numbers.
- **Staff engineer** (she): built the who-gets-pinged logic. The only real source on how a
  responder is ranked; there is no document.
- **Support lead**: hears handler complaints first. Priya suggests a standing 15 min.
- **Director of Product** (she): the user's director. Good, gives room.

### Vocabulary
- **Responder**: the person offered a callout. **Handler**: the people writing in to
  complain about 4.2 (_inferred_: console-side users; the note never defines it).
- **Ping / offer**: the callout sent to a responder. **Ping timeout**: how long they
  have to respond.
- **Acceptance rate**: share of pings taken. Exact definition not given.
- **Recent acceptance history**: a ranking input, weighted against **proximity**.

### Where things stand
- **4.2 shipped 12 Aug 2026.** Proximity now weighs more than recent acceptance
  history (a long-requested change, delayed three quarters, from responders working
  wide geographies). The ping timeout was also cut in the same release.
- **Problem:** since 4.2, fewer pings are accepted and more handlers are complaining.
- **Confounds:** August is seasonally soft every year, and two changes shipped together
  (ranking and timeout). Priya's read is "mostly seasonal, back in September", which is
  untested. Today is 6 Oct 2026, so September data should now exist and can test it.
- **Priya's steer:** check seasonality first; don't let this become a revert-4.2
  debate, since the change was requested and reverting trades one angry group for
  another. Treat that as her view, not a decision.
- **Open with the Director of Product:** some items were cut from 4.2 and it's unsettled
  which are still Q3 commitments. That conversation hasn't happened. Q3 ended 30 Sep, so
  it is now overdue.
- **Noise:** the 4.2 console filter-persistence change will generate cosmetic tickets.
  Don't let it consume the first month.
- **Gap:** nobody has written down how ranking works. Priya asks the user to write it
  (work with the staff engineer plus the code).

### Not known yet
Names, team size, the acceptance-rate definition, actual before/after numbers, which
items were cut from 4.2, and what Q4 commitments exist.

### Module 2 findings (interviews and tickets)
- Sources: rook-wiki "Customer interviews" (4 handlers, 2-5 Sep: Dot, Ambrose, Halloran, Kip) and rook-database `support_tickets` (147 tickets, 29 Jun-7 Sep, 12 handlers). `00-rook/feedback/tickets/` is empty. 15 handlers seen in total (only Ambrose is in both); the real team size is still unknown.
- Timing: no vanished-callout or quiet-responder tickets before 12 Aug. Vanished callouts start 12 Aug (15 tickets, 11 of 12 handlers). Quiet responders start 17 Aug (30 tickets, only 4 responders): The Undertow and Farlight had 7-9 days with no ping (about 12 a week down to 1-2), Halfmoon and Corporal Ashgrove are down about 30%. All 40 pre-release tickets are closed; 83 of 107 since are open.
- Skew: two handlers (Okafor, Pruitt) wrote two-thirds of the quiet-responder tickets, and none of the four worst-affected handlers was interviewed. The "flooded responder" side comes only from Dot and Kip. The interviews were console-redesign research, held after the ticket peak (week of 24 Aug).
- 4.2 is a strong candidate cause, not proven: the timeout and ranking changes shipped together, filter resets "after update" suggest later deploys, Ambrose says it was not the first time this year, and the 12 Aug deploy time is unknown. Priya's "mostly seasonal" read is still untested.
- Outside Dispatch, route to Supply: cracked vest plates stuck on slow requisitions, a grapple line retracting slowly in the cold, and failure reports nobody answers.
- Next: read the routing code and CHANGELOG (not yet read), ask the staff engineer about the quiet responders, get ping data (including Sep and Aug 2025), call Okafor and Pruitt, answer the open tickets, and hold the overdue Director of Product conversation.

### Module 3 findings (ping and callout data)
- Sources: `00-rook/data/callout-history.csv` (weekly per responder, weeks from 29 Jun to 31 Aug) and rook-database `pings` and `callouts` (daily, to 6 Sep) agree exactly. `00-rook/feedback/tickets/` now holds the same 147 tickets as `support_tickets`. Acceptance is computed as taken ÷ sent; Rook's own definition is still unconfirmed.
- Main result: four responders (Farlight, Meteor Mite, The Undertow, Vesper) went from about 12 pings a week each (49 combined) to 3 combined by the week of 31 Aug (-69% over 12 Aug-6 Sep, -94% in the latest week), with acceptance 76% to 23%. Callouts in their areas fell only 11-18%. The other 12 dipped about 9 points and recovered to about 74%. Overall acceptance 76.8% to 64.0% (-12.8 points); the four account for about 3.7 of that.
- Callouts fell about 15% (140 to 118 a week), a step in release week. "Pings taken" equals callouts filled, so it mixes demand with routing; use filled % (94.9% to 88.9%, back to 94.5% latest week) and pings per callout (1.24 to 1.39). No Aug 2025 data, so Priya's seasonal read is unsupported but untested.
- Code (read, not yet confirmed with the staff engineer): 4.2 moved proximity weight 0.45 to 0.60, acceptance 0.40 to 0.25, and timeout 90s to 60s. A missed offer counts as a decline (-0.12 vs +0.08 for a yes) and the score never decays (2019 TODO), so a quiet responder may never earn offers back. Missed offers jumped from 0-1 a day to 7-12 a day on 12-16 Aug. Need the four's scores and travel times.
- Farlight (Uptown): last accepted ping 14 Aug, last ping 28 Aug, none through 6 Sep. Uptown callouts held at about 10 a week and now go to Falkirk, Cindermark and Bulwark. Vanished-callout tickets start 12 Aug, quiet-responder tickets 17 Aug (about 2 days behind the data). Kip, Aunt Dot and Halloran filed zero tickets all period, so no tickets about Meteor Mite or Vesper is not evidence they're fine.
- Open: why callouts stepped down in release week, ranking vs timeout (shipped together), and which metrics to give leadership (leading with pings to the four and filled %).
- Module 4 (read all of `00-rook/code/dispatch-routing/`; `00-rook/4.2-investigation-summary.md` holds the earlier write-up): the folder starts once a callout exists, so where an incident becomes a callout is not in it. Ranking = 0.60 proximity + 0.25 recent acceptance + 0.15 capability; nobody is removed, only ordered. Offers go one at a time down the list, 60s each; a yes ends it.
- The "recent acceptance" score is a running tally, not a rate: starts 0.5, +0.08 per yes, -0.12 per decline or miss, clamped 0 to 1, never decays. `record_accepted` is the only thing that adds points, so a responder ranked low and rarely offered has no way back in the code. Break-even is a 60% yes rate; from 0 it takes 7 straight yeses to reach 0.5.
- Scores sit in an in-memory dict keyed by responder name, with no saving code in the folder (a restart may reset them, unconfirmed). Weights are global constants, so the 4.2 change applied to everyone, including past decliners; no flag or staged rollout is visible here. The four starved responders weren't heavy decliners before 4.2 (15-29% declined).
- People now named in the team directory: Marcus Oyelaran (Engineering Manager), Wen Li (Staff Engineer, away 14-24 Aug, never answered Marcus's 14 Aug question on whether the ranking change should cover past decliners), Helen Achebe (Director of Product), Nadia Hoffmann (Support Lead), Ravi Menon (Data Analyst, weekly acceptance series). Open for Wen Li: the four's current scores, whether misses should count like declines, where scores are stored, and whether a restart resets them.
