---
authors: ["Gniewomir Świechowski"]
title: "Well-used AI: the useful bits of atypical wiring — without the productivity tax"
date: "2026-08-13"
tags: ["AI", "LLM", "Software Engineering", "Opinion", "Go"]
categories: ["AI", "Software Engineering"]
weight: -1
ShowToc: false
draft: false
---

I've read a lot of observations from people signaling a similar epiphany I've been having for a while - that well-used AI allows you to profit from useful bits of atypical brain wiring while lowering friction of problematic ones. Yet, the common approach focusing mostly on "what" at the cost of "why" and "how" did not sit well with me. Founder-mindset and clockmaker-mindset are different. Now I feel that I've built a flow giving me similar benefits, while keeping me honest to what I value.

Inspiration for this note is learning a language (Go) from (almost) scratch while doing an actual project (minimalistic OAuth2 auth server for my other project). With a bit of judgment and tooling, AI enabled focused exploration when needed (more advanced bits of syntax/lang design, tooling, quirks, good & bad practices, filling domain knowledge gaps, diving into RFCs, etc.) to be non-blocking, helping the process to progress - instead of interrupting or derailing it.

A brain demanding clarity and running on high-octane curiosity taxes productivity for unresolved ambiguities. But now a few minutes of waiting for a focused research document replace hours of manual blind digging, days spent on sifting through documentation mostly unrelated to current roadblock, risk or knowledge gap. The tedious process of fishing for relevant bits in noise and slowly assembling understanding got replaced by exercising judgment on what is relevant now and how to formulate correct questions.

Having a very similar project in TypeScript on my personal projects pile-of-shame - known to all developers - gave me a good apples-to-apples comparison of how much this reduced friction speeds things up and helps to keep eyes on the ball.

It forces me to reevaluate why coding became my thing in the first place and what burned me out a few times over the years, when depending on heuristics instead of grounded understanding was a requirement because of time constraints - forcing either an ungodly amount of hidden overtime or lowering the bar below my comfort level.

The other factor is challenge or lack thereof. As I see it, there are three potentially interesting problems that might coexist in every software project: architecture reflected in structure, non-functional requirements and domain discovery/complexity. Very often (not always) one is the bottleneck and solving it is the fun, challenging part - making the other two trivial details. Perfect target for automation - given solid guardrails, which lowers risk of burnout and gives back space for actual growth.

My stance on AI is evolving the more experience I gain on how to employ it correctly (very far from "embracing the vibes" or completely unattended automation) because I feel like it allows you to focus on what actually matters. There was always a place for enforcing a contract and hiding perceived or existing ugliness behind it, sticking to "good enough, will fix later(TM)", going with industry "defaults" without consideration, but also for lovingly hand crafting every LOC to avoid unnecessary memory allocations - where it matters, agonizing over tradeoffs before pouring concrete, handling edge cases before feedback from production and improving DX & testability. AI did not change that in any way, but made exercising judgment leading towards the latter much cheaper.

I will never be that guy who scores points by going in half-blind and consequences beyond current ticket's scope be damned. Nor the one who feels comfortable delegating that half-assed approach to an agentic loop before doing proper homework. But I feel like the tax imposed by above-average curiosity and need for clarity is getting much more manageable with AI - without self-imposed crunch. Something that would have surprised me when I was looking at AI mostly through the lens of unstructured AI use around me - exacerbating known problems instead of solving them.
