---
authors: ["Gniewomir Świechowski"]
title: "A shared language earns you the right not to read the code"
date: "2026-07-27"
tags: ["AI", "LLM", "Software Engineering", "Opinion", "DDD", "Ubiquitous language", "Domain Driven Design", "Agentic coding"]
categories: ["AI", "Software Engineering"]
weight: -1
ShowToc: true
TocOpen: true
draft: false
---

Adopting ubiquitous language (where agents are heavily responsible for keeping you, the codebase, and the vocabulary in alignment—otherwise, drift will kill you) greatly improves alignment between what you want and what agents deliver.

There is still tactical cognitive debt. You have no idea about the details of delegated implementation, but that's OK. You decided to be a Lieutenant General, not a Lieutenant, so you move divisions, not platoons.

You note that a particular operation introduces side effects that break everything that follows. You can change the implementation to mitigate them; you can ask an agent to do it—it might be enough to move forward. Until a minute, hour, day, or month later, when you or an agent breaks the silent, tribal contract you made by fixing the implementation to be pure and idempotent. It won't fly at scale. Shit, it won't fly even in domain discovery mode for a non-trivial personal project.

Or you can name and define this operation in the project vocabulary (a mandatory part of your context) as idempotent. Then you can delegate aligning the codebase with this shared understanding of what should be true. At the same time, every future developer or agent analyzing, reviewing, or changing the codebase knows that this is a contract the whole project depends on.

One might argue that this is what tests are for—to document invariants. Fair. But they will also be written, updated, and run by an agent, based on whatever understanding of which invariants need to hold is in the context.

One might argue that this is what documentation is for—to document invariants. Fair. But it will also be written mostly by agents. If it does not use a common vocabulary, you won't be able to effectively search for applicable documents. If there is no single source of truth for what this vocabulary is, there might be multiple competing definitions drifting independently.

You can fix the implementation and move on, or you can make the decision part of the language of the project—something every future human and agent has to reckon with before changing it. You still solve today’s problem, but you also give yourself a fighting chance of keeping it solved. And when your understanding changes, the vocabulary changes with it, followed by the code.
