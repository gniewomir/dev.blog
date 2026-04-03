---
author: "Gniewomir Świechowski"
title: "Grill yourself, or why you should not delegate design to an \"AI\" stochastic parrot"
date: "2026-04-03"
description: "How Matt Pocock's 'Grill Me' skill forces intentional design and saves you from the many pitfalls of AI vibe-coding."
tags: ["AI", "development", "productivity", "Good Practices", "Engineering", "LLM", "Agents"]
ShowToc: false
ShowBreadCrumbs: false
draft: false
---

When doing AI-assisted development using agents, your prompts will inevitably have *a lot* of decision gaps. Sometimes the model's "defaults" used in those places are fine, but leaked system prompts suggest that most of them are explicitly prodded towards the lowest change-surface solutions. It's a safe choice, but in a mature codebase, this will become increasingly corrosive with each change. In fresh projects, it will lock in place bad design decisions that you or the agent made early on.

Enter *[Matt Pocock's "Grill Me" Skill](https://github.com/mattpocock/skills/blob/main/grill-me/SKILL.md)*.

While being just a few short sentences, it seems to solve this problem regardless of the model you use, and I absolutely love it. It will nag you with anywhere between a few to a few dozen questions about design decisions that could not be definitely inferred from your initial request. It is a great start to provide context for your planning step, making your intentions clear upfront. 

You are forced to intentionally fill the gaps in your initial intuitions—which by itself delivers great value, by refining your understanding of what, why, and how a feature, project, or product should be built. It might not eliminate the problem of cognitive debt incurred by heavy AI-use, but it moves the accent to implementation details, allowing you to keep a crisp mental model of architecture on tactical and strategic levels. 

This is the exact opposite of the cool-kids' "vibe-coding" model, which focuses on delegating not only the implementation but also most of the design to a specialized stochastic parrot—just rolling dice, seeing if by throwing more and more tokens at the wall, some of them may stick.

[Matt Pocock](https://github.com/mattpocock) iterated over this skill as part of his very hands-off agenctic software development workflow. His goal was to move the responsibility for design back to the actually intelligent human with some taste, giving agents a better shot at delivering a usable implementation based on a well-groomed plan. However, I've found it works perfectly well in the more hands-on approach that I prefer.

Answering twenty-something questions in a row can be a pretty intense mental exercise, but it has already saved me multiple times from either rewriting bits of my project from scratch or burning huge amounts of tokens on useless iterations.

**Do not save a half-hour of design only to pay for it with hours of half-random iterations. Use it.**
