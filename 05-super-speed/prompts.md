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

I need to create a product brief/requirements document to description the issue that has been identified and what the potential solution is. While creating this brief consider these items

* 05-super-speed/director-request.txt Helen's actual request. Your brief needs to answer exactly what she's asking for.
* rook-wiki Glossary, Team directory, and the 4.2 release comments (people are named by role; the Team directory maps roles to names). Also read the Word doc 00-rook/company/notes/handoff-from-priya.docx. You already read these once on Day 1. Go back for the exact terms and names your brief needs.
* Three things the brief needs who the solution is for, what changes for them once it exists, and what it deliberately doesn't do. This is the fix for the problem you've been investigating all along, made real for the responder you picked in Module 3. You already know them, which makes the brief easier to write, but you can pick someone else if you'd rather.


I want the brief to be concise, no more than one page.

### 2.

no clickable prototypes yet - can you show me the text of the brief you built

### 3.

why did we narrow the scope down to a single responder/handler? was that a request from helen?

### 4.

the who's it for should be any handler or responder, just because that group was the one most impacted, in theory, any responder/handler could encounter this problem

### 5.

can you make the problem statement more high level for a leadership person? remove any specific data points found in the code. explain the problem and it's impact, but there's not need to go into nitty gritty details

### 6.

send me the current version we have right now

### 7.

let's remove the example from "who it's for"

### 8.

yes, and let's also do this that you suggested Leadership-level wording. The “Who it’s for” paragraph, the “doesn’t change the ping wait” bullet, “Owner and dependencies” and “Risks” still carry the numbers and code detail you asked me to remove from the Problem section.

### 9.

yes paste the text

### 10.

let's remove the "what it doesn't do"

### 11.

oops, go ahead and put it back

### 12.

leave score, update to affected responders and how long a ping stays on a responders phone

### 13.

this is a backend change that improves the experience for the responders/handlers. what if we were rebuilding from the start - how would you recommend we'd build this feature if we were starting over

### 14.

okay let's focus on the brief we've already built

### 15.

let's be consistent with format, make everything in paragraph format and be concise. No more than two paragraphs.

### 16.

can you make the each bar of the chart clickable? so when a bar is selected you can see the week dates and number of calls? also let's make the content when the alert is expanded a one sentence concise alert message

### 17.

let's not consider 4.2 timeline when building this prototype. let's default showing 6 weeks at a time. the bars should be one color in their default state and another when they are selected. so maybe dark blue in default, when selected, remains dark blue and all others are light blue. let's offer a date range selector so we show 6 weeks and then they can pick other 6 week date ranges if needed.

### 18.

clicking away from any bar should reset the the select to it's default state.

also what is a way we can offer showing a breakdown by taken, missed, or declined pings?

### 19.

let's try the first option first

### 20.

can we remove the usual about 11 from the segmented bar section

also I don't think it makes sense to reference a different responder on each other's cards. let's just leave the description on the gale focused to him. can we make that section more of an "information" section so i'm thinking a little info icon and something like "busier than usual"

### 21.

remove - Click a bar to see the week.

### 22.

let's update the meteor mite text to - After some missed pings, Dispatch has been offering you fewer callouts. It is being corrected and you should see offers pick up over the next few weeks.

### 23.

review the prototype - do you notice any gaps from what our proposed solution was that the prototype doesn't account for?
