---
authors: ["Gniewomir Świechowski"]
title: "You can un-slop code but not documentation"
date: "2026-05-09"
tags: ["AI", "LLM", "Software Engineering", "Documentation", "Opinion"]
categories: ["AI", "Software Engineering"]
draft: false
ShowToc: false
---

There is a huge problem I have not seen discussed in the context of AI. Documentation—just like code—can rot when subjected to unrestricted AI use, and this is not something that can be easily, if at all, fixed.

Missing, misleading or outdated documentation forces rushed explorations focused on how, not why—which tightens competition for resources between research, design, and implementation. Good documentation warns about dead ends and explains constraints, allowing teams to reach better decisions faster. Yet, having a good knowledge base was hard before AI, and I'm convinced that it will get even harder with it. 

The pre-AI baseline was already bad:

1. Any documentation that cannot be verified automatically will, at some point, subtly drift from reality or become completely outdated and misleading.

2. Updating existing documentation is a time-consuming and thankless job, often skipped in estimations.

3. While incredibly useful for the org and peers in the long run, it competes with delivering what you are actually accountable for in the short term.

At first glance, AI should improve our outcomes:

1. You can explore the codebase with AI, which lowers the friction of creating accurate documentation.

2. You can quickly turn a draft into a professional-looking document - skipping writer’s block and jumping straight to iterating on it.

3. You can put smart guardrails in place, cross-referencing existing documents with new ones.

But the related risks can dominate the benefits:

1. Hallucinations are an unresolved problem, so your documentation will contain a growing number of subtly wrong claims. This seems unavoidable: we have not solved the same problem in much more formal programming languages, even with linters, static analysis, type systems, and tests.

2. Existing documentation becomes context for new documentation, exacerbating the previous issue and creating an organizational version of model collapse. Garbage in, garbage out.

3. It is much easier to create volume instead of substance, so people will do it, and readers overwhelmed by the volume will often rubber-stamp it. As friction for document creation goes down, document volume grows—just like with PRs.

4. When documents look finished before they have been verified, you lose the visual signal of how much actual effort was put into the document, and it gets harder to assess if the document is performative documentation or created to provide actual value.

Decay is not an unavoidable outcome, but using AI to improve documentation quality instead of degrading it requires one thing our industry is notoriously bad at: daily hygiene. Boring, unsexy, tedious, and underappreciated good habits.

Maybe, just maybe, it can be mitigated by throwing A LOT of compute at AI-powered review pipelines and quality gates. But you need them now, not next year, and it will put a hefty price tag on the smallest edits—which may open a different can of worms.

As with everything else, if your org was unable to maintain a healthy knowledge base before, then AI will make everything much worse at warp speed, robbing you of the one tool coding agents desperately need to be truly useful. AI errors tend to compound very fast in code and design, and one of the main ways to limit them is by providing unambiguous context, explaining vocabulary, processes, limitations, and accepted workarounds.

Knowledge bases are a great way of doing it—but they are very fragile. Like automated tests, they are useful only as long as they can be trusted.

While even the worst code can be refactored, tested, un-slopped, and effectively un-f***ed while keeping the lights on, a poisoned knowledge base is hard to fix without starting from scratch. This is both because of the effort required to examine literally all claims—after inherited outdated ones mix with hallucinated ones—and the complete loss of users' trust.
