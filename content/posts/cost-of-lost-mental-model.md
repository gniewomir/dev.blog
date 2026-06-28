---
authors: ["Gniewomir Świechowski"]
title: "Cost of lost mental model"
date: "2026-03-10"
tags: []
categories: []
weight: -1
ShowToc: true
TocOpen: true
draft: true
---

I recently wrote a Chrome extension to fit my specific needs, and coding models were a great help—to a point. When thinking about the process, it hit me that it was a good ilustration 

# Core technical problem

The extension in question is [Flotsam](https://chromewebstore.google.com/detail/flotsam-auto-close-tabs-a/fjncigamjmbnpgbhhikmddiijpjiodjp)—at first glance, nothing overly complicated. It should close browser tabs after some time with some exceptions (focused, manually anchored, excluded by domain, pinned, grouped, playing sound, etc.). 

Sounds simple, until you take into account that the Chrome browser is multi-process and multi-threaded, so multiple things can happen almost at the same time and will be communicated via events to your service worker. While service worker JavaScript execution is single-threaded, it offers simulated concurrency by releasing control to the event loop until asynchronous operations are completed—like querying the Chrome state. On top of it, your service worker can be killed at any time. 

You end up with the core problem of modern web development and distributed systems: how to deal with unavoidable shared, global, mutable state. Your configuration (what domains are whitelisted?), transient state (what tabs are anchored?), and the state of entities you are tracking (is the tab audible? is the current URL whitelisted?) can change independently at any point in time, and a lot of those changes have to be queried asynchronously. You get multiple parts moving simultaneously, which leads to race conditions of the time-of-check to time-of-use flavor.

# Busy work vs systemic solution

Here comes the AI coding model—which is perfectly capable of creating a working POC, but depending on your understanding of the Chrome API, the solved problem, and the [effort put into design](/posts/grill-yourself-or-why-you-should-not-delegate-design-to-an-ai-stochastic-parrot/) upfront, it will be heavily skewed towards the simplest possible solution. Which, in this case, will typically mean stitching your logic directly with event handlers. This is perfectly okay if you just want to get a feel for the problem domain, but poison if it is your foundation, as different parts of your system will race against each other. 

Now you have a decision to make: do I mitigate symptoms one by one as a solid model is able to spot race conditions and find local resolutions, or do I accept the fact that my architecture does not address the core problem and needs to change? 

Resolving symptoms means that every new feature and bug fix will have non-obvious side effects, and complexity will explode as race condition mitigations start to race against each other. After addressing just a few of them, simply understanding how core functionality is implemented becomes a rabbit hole, because it gets harder and harder to discern which code is a workaround and which implements the actual product.  

So, the sane decision seems to be introducing some architectural rigor addressing the core problem, instead of paying a growing symptoms tax for the rest of the project's lifetime. This is what I did—I introduced an internal event queue with a monopoly on mutating state and rewrote the POC to gain the ability to reason about state transitions. 

But this has to be an intentional decision by the person at the steering wheel. Coding models are—for good reasons—skewed towards a minimal change surface and addressing the task at hand (bug, symptom), not the core architectural issue (root cause). Furthermore, already done work (an overly simplistic POC with workarounds) becomes part of their context—a reference point for every future suggestion. 

# Understanding incentives

Working in my spare time on a hobby project and commercial work are very different. Not because the correct decision changed, but because you won't necessarily be able to make the correct choice when the time comes to make this decision. 

In a commercial setting, your POC—including all of the race conditions and lack of coherent architecture—would already be shipped. Your manager would receive a firm handshake, a pat on the back, and a new goal from their boss. So, when during the next sprint the first bug reports start to come in, you or your peer have another decision to make: should we do the minimal effort fix, closing the ticket within an hour using AI, and repeat this process as needed, or should we address the core issue? 

From the technical, financial (for the company), and moral perspective, you should take the systemic solution path. This is the right thing to do, as a day or two will save weeks of work going forward and your peers' sanity. Those will be real financial savings—just not the ones that you or your manager can take any credit for. 

From a rational, career-oriented perspective, you probably should just hide the problem under the rug by throwing some tokens its way. Spending time, effort, and influence to even put this problem on your plate does not benefit you or your manager immediately, and responsibility for future consequences is so fuzzy that after a few months, it is inconsequential. 

It is hard to earn points for solving a problem that is in the making, rather than a pain point felt by the team or the whole company. 

# Realistic outcome 

The problem I am trying to point out is that coding models and their harnesses are built around the same incentive structure that is the main driver of modern software engineering: deliver value instantly, regardless of mid- or long-term costs. When they become the main driver of system evolution, they disincentivize cost/benefit analysis and the weighting of short/long-term consequences, because they take away the pain of dealing with badly designed systems in the short/mid-term—until it becomes truly unmanageable. 

The argument that it is OK as long as you can manage bad design with AI is deeply flawed, because if we learned anything about coding models during the last two years, it is that they deal with compounding errors and unstructured complexity even worse than we do. 

AI-driven/AI-assisted development is not a bad thing in itself, but it drastically lowers the friction for doing the wrong thing for every stakeholder from developers to C-level, where the "wrong thing" is defined as taking short-term shortcuts that have disproportionate long-term costs. It does not apply to every org or team, but we are—just like our coding models—tilted towards the path of least resistance. 