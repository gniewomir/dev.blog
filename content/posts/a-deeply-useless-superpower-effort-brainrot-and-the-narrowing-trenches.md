---
authors: ["Gniewomir Świechowski"]
title: "A deeply useless superpower: effort, brainrot, and the narrowing trenches"
date: "2026-11-02"
tags: ["AI", "LLM", "Databases", "Software Engineering", "Opinion", "Career"]
categories: ["AI", "Software Engineering"]
weight: -1
ShowToc: false
draft: false
---

I'm in the middle of a really deep dive on transactions: isolation and ACID, distributed transactions, where DDD fights the most obvious ACID-transaction shapes, how different engines achieve ACID properties, how to preserve sanity where replicas are in play. The goal is a comprehensive guide connecting theory and practice - not as an end in itself, but as a means to systematize my knowledge and experience, fill in the gaps, and gain some confidence when arguing for sane solutions. (I will put the result online at some point regardless.)

It's at the same time fun - I'm learning; scary - the learning is basically uncovering swaths of ignorance I was blissfully unaware of; and very time-consuming, even with significant help from AI models.

The irritating part: it also feels a bit pointless. Don't get me wrong - deep understanding of how all of those fit together and where tradeoffs have to be made feels like a superpower. Just a deeply useless one.

The market demands we up our game, but in my experience most engineering-team discussions - even before AI - were barely scratching the surface. I remember all too many superfluous discussions about basics, where I had to argue why database-generated IDs are a bad idea in most modern applications and how they hurt testability on top of that. With AI in the picture, this might get much worse - not better. 

Without careful examination and contextualization, the overly verbose gems of wisdom spewed by models are useless. Effort is what makes understanding sticky - the kind of understanding that can be translated into informed decisions about silicon- and protein-generated code. Effort is what converts technical mumbo-jumbo sprinkled with abbreviations - stuff that can be memorized and recited - into an actually useful mental map of fundamental limitations, concepts, constraints, quirks, and tradeoffs.

AI cuts both ways. On the one hand, it made it pretty easy to explore where the potential foot guns are, what the mitigations are, what they buy and cost - if you're inclined to leave no stone unturned. On the other - brainrot is real. You cannot realistically expect that effort if the aproximation of "how" is readily available without first painstakingly going through the "why" ladder. There are just not enough incentives to be thorough, but all too many to be fast.

Where it really bites is when I realize that the niche between half-blind rubber stamping (common even before AI), narrow specialization (for which I had no inclination), and technical leadership (that I assumed only as a last resort) - what I like to think of as the actual trenches of our industry - is getting frighteningly narrow. Not enough to switch to carpentry - but enough to entertain the idea.
