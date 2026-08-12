---
authors: ["Gniewomir Świechowski"]
title: "Waterfall-in-disguise's return is just around the corner"
date: "2026-08-12"
tags: ["AI", "LLM", "Software Engineering", "Opinion", "Spec-driven development", "Waterfall"]
categories: ["AI", "Software Engineering"]
weight: -1
ShowToc: false
draft: false
---

Waterfall-in-disguise's return is just around the corner. If we allow it, we will be even more miserable than we already are with "scrum" cargo-cult.

For the second time in the last year I will be writing minimal OAuth2 auth server (why that is material for another note). Creating & refining initial spec took a full day of work so far - before even one LOC was created.

The model's ability to spot underspecified requirements or contradictions with chosen RFC baseline is a godsend when working with a sensitive domain like security. Makes good spec cheap, not resurrecting waterfall by itself. Still, three serious problems follow:

1/ To make informed choices you need to be a domain expert or to have really good breadth (to spot when you do not fully understand tradeoff) and discipline to follow up - regardless of another 50+ decisions waiting in the queue.

2/ Leaning too much on the model during design is a siren song, leading towards rocks of heavy over-engineering. Easier to accept, than to push back against. "Acceptable risk" still contains no-no word "risk".

3/ Sweating when building spec is useful to reconcile initial idea with constraints discovered during design, instead of discovering these contradictions during implementation (cheaper). But it is still a draft, not locked artifact - there were no spikes, no implementation, no non-functional requirements frictions revealed themselves yet.

First problem is supposedly addressed by industry newly discovered love for Full Stack Developers, who nomen omen should provide exactly that. But it rarely goes beyond "does this guy/gal know our frontend, backend framework and our cloud provider UI". Specialization still fits recruitment landscape better than breadth - much harder to assess.

Second is dice throw depending on culture. Matrix of org leaning towards YOLO, pragmatism or spaceship style programming on one axis, and delivery pressure on the other prevents me from making any general observations.

Third is the scariest, a mortal threat of waterfall raising its ugly head once again - in a "spec-driven development" disguise. Too detailed, early design artifacts leaking outside repository, gain a second life on its own, becoming a separate Source of Truth for which devs will be accountable before any reality-checks. Even without "spec-driven" framing.

A detailed spec you can iterate on with your team without added friction is an efficiency booster, but the moment when it gets shared upstream it becomes commitment. Commitment implies overhead of justifying when assumptions change, timelines based on not fully validated assumptions, aligning what was shared with what was discovered, translating to human language reasons why parts of the design tree need to be relitigated.

Startup-like culture can deal with that - nothing there is set in stone by default. In a more rigid setting it might result in sub-optimal choices and over engineering becoming sticky - just to avoid communication overhead.
