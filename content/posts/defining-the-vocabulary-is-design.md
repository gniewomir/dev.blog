---
authors: ["Gniewomir Świechowski"]
title: "Defining the vocabulary is design"
date: "2026-07-28"
tags: ["AI", "LLM", "Software Engineering", "Opinion"]
categories: ["AI", "Software Engineering"]
weight: -1
ShowToc: false
draft: false
---

I’m starting to think about “grilling” (in the context of [Matt Pocock’s skill framework](https://github.com/mattpocock/skills/blob/main/grill-me/SKILL.md)) not only as design/decision-recording sessions, because the core benefit is how they expose how domain language clashes with your intent—requiring adaptation of one or the other.

The definition of terms is your core pre-code-generation guardrail. The “world model” of LLMs is language itself, so it makes them pretty good at spotting language-, vocabulary-, and definition-level contradictions. Often better than we do, if you are not blessed with a tiny bit of autistic traits.

When you cannot push a square block (term definition) into a round opening (different term definition/requirement), the design process turns into updating the vocabulary until terms, definitions, and their relations do not contradict one another.

When you are done, your intent is unambiguous to the implementing agent because your ask lives in your new vocabulary more than in your sloppy prompts.

You did not discover some prompt-engineering voodoo. You designed a vocabulary in which your intent can be expressed precisely. That shared vocabulary also happens to make you an unusually effective context engineer. Congratulations.