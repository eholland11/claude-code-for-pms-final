# Quiet responders: get them offered work again, and tell their handler why

One-pager · Product, Dispatch · 9 October 2026 · For Helen Achebe · Draft

## Problem
Since 4.2, a handful of responders have almost stopped receiving pings, even though they are still available and callouts in their areas haven't dried up. Four have been hit hardest, and their pings have fallen by more than 90%. The way Dispatch ranks responders penalizes a responder who misses pings and gives them no way back: the less they are offered, the less chance they have to recover.

Responders lose work and wonder if they've been forgotten, while other responders in the same area are overloaded. Handlers can see the imbalance but not the reason, so they have nothing to tell the people they support, and support is seeing more tickets about it.

## Who it's for
Any responder and any handler. A few responders are the most affected so far, but the problem isn't specific to them. Missed pings rose across the board after 4.2, so any responder could slide the same way.

## What changes for them
A missed ping stops counting as a refusal, and a long-quiet responder's score eases back toward neutral, so they are offered nearby callouts again within weeks without anyone intervening. Ranking still starts from proximity, so nobody is offered work far from home.

Each console coverage card shows a plain-language "quiet" flag when a responder's pings drop well below their own recent norm, with the reason in one line. A handler can tell their responder what is happening instead of "hang in there," and when two cards tell different stories, the screen explains why.

## What it deliberately doesn't do
It doesn't revert 4.2 or change the proximity weighting, which was a long-requested change. It doesn't change how long a ping stays on a responder's phone, which caused its own rise in missed pings and is a separate decision. It doesn't remove or force-rank anyone, and it isn't a setting.

It doesn't touch handler notifications (see the Handler Phone App brief) or anything in Supply.

## Owner and dependencies
Product owns the brief. Wen Li confirms the ranking design and whether the 4.2 change was meant to apply to everyone, which Marcus Oyelaran asked on 14 Aug and is still unanswered. Sofia Marino designs the quiet flag, and Nadia Hoffmann checks the wording against what handlers are writing in.

## Success measure
Proposed, to be agreed with Ravi Menon: within 4 weeks of shipping, no responder is below half their own 8-week pings-per-week norm for 2 weeks running, and "phone never goes off" tickets fall to the pre-4.2 level (none). We'll track filled % and pings per callout alongside acceptance rate, so a fix for the affected responders isn't hidden or inflated by the average.

## Risks and open questions
Giving quiet responders a way back also re-offers work to people who really have stopped taking it. They return only to a neutral standing, never above it, and a declined offer lowers them again.

Still open: whether the quiet flag should also appear on the responder's phone (this brief covers the handler's console only), how badly the affected responders are stuck today, and whether September data shows them recovering on their own. Engineering hasn't confirmed the last two.
