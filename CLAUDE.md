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
