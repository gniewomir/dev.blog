---
authors: ["Gniewomir Świechowski"]
title: "Ubiquitous language is the answer to so many pains of agentic coding"
date: "2026-08-02"
tags: ["AI", "LLM", "Software Engineering", "Opinion"]
categories: ["AI", "Software Engineering"]
weight: -1
ShowToc: false
draft: false
---

I'm prone to being overly enthusiastic when something seems to fit perfectly puzzles I try to solve. Right now I'm in that state exactly. Ubiquitous language is the answer to so many pains of agentic coding. Part of my current experiment vocabulary started as "Workflow", then it gave birth to sibling "Component", then "Fabric" was extracted from "Component" when its meaning got refined, and then "Fabric" revealed "Substrate" underneath. Each of the evolving terms guiding both me and the agents in the correct direction, constraining what conceptually makes sense within the bigger picture defined by vocabulary.

Sharpening vocabulary drives design and implementation, ensuring that human, agent assisting design, and implementing agent share the same understanding. Models understand what fits a "Fabric" or "Substrate" definition — therefore where a particular bit belongs — without you telling them so in each prompt or artifact driving this layer mutation.

I love the analogy of two experts having a conversation — they do not have to define the loaded terms they are using, as you can expect that your counterpart understands all of the nuances implied. Now, imagine what happens when an expert is having a conversation with a layman — before using the term "Idempotency" he needs to define it and confirm shared understanding, before even attempting to explain how it fits the bigger picture.

Experts' conversations are so much more efficient and precise.

But where the ubiquitous language approach gets truly great in the age of agentic coding is when you realize that Vocabulary+ADRs are the soul of your project. All of the code is just an implementation detail (except non-functional requirements, which when known become part of the domain).

When Vocabulary+ADR match the definition of MVP, then you can dive in and carefully inspect where the bits are that need to be carefully reviewed and/or hand-crafted. Everything is a prototype until you get the initial shape right. "Move fast and break things" as long as possible, then reevaluate — but with a solid foundation of documented shared understanding and acceptance tests, so you can iterate with a tighter stability and backwards-compatibility posture.

There are a lot of questions I do not have a good answer for yet about how to employ this approach at scale (when your vocabulary and ADR record do not fit a single agent session, when one codebase has many bounded contexts, when a whole system is distributed but tightly coupled — you know what kind of systems I'm talking about), but conceptually I feel that it is a good direction. We have RAG after all. Hell, do you really even need RAG if your vocabulary is enforced by workflow, therefore consistently greppable?

The fun part is that, like almost everything, it is an adaptation and repackaging of already established ideas that were under-appreciated (since 2003) because they require discipline. Now with models doing most of the heavy lifting — there are no excuses.
