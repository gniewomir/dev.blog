---
authors: ["Gniewomir Świechowski"]
title: "Why mocking is a loan with predatory rate, which you should avoid"
date: "2026-03-10"
tags: ["testing", "Good Practices", "Engineering", "AI", "TypeScript" ]
categories: ["Testing"]
weight: -1
ShowToc: true
TocOpen: true
draft: true
---

More than a decade ago, when I started a deep dive in automated testing as integral part of my process, I got caught for a short while in the worst trap of automated software testing - mocking. It seemed like obvious way to write tests - everybody around was doing it that way and there where a lot of intricate tooling for it. Yet, it just feel wrong after a while. There was a growing cognitive disonance, between what I was learning about what qualities a good test/test suite should exhibit, and results I was getting by relying on it. It lead me to dropping mocking altogether - with rare exceptions, when the tradeoff was acctualy worth it. Like with all such experiences, I went about my business a bit smarter and fully convinced that everybody at some point of their career will have simillar "Aha!" moment - I was wrong.

# How we define mocking? 
Mocking in general is replacing complex - often non-deterministic - dependancies with simulated ones which behaviour you can controll in every detail. The problem is, that in loose conversation between two profesionals, it can refer to two fundamentaly different approaches. The one I will be refering here as root of all evil is using specialized libraries which cheat our code to belive that our mock is a expected dependancy and expose complex api to define it's behaviour. The one, I will be advocating for is using test doubles - objects that fullfill the same contract/interface as mocked dependancy, but handcrafted. Both aproaches have it's place and valid use cases, but sadly, it seems that the first one became a go to solution, when it should be a fallback keept for extraordinary circumstances. 

# Why are we testing at all? 
Let's start with establishing some common ground. Obvious answer to the question, why we need tests, would be that we do it to check that our changes do what they are supossed to do. Writing few automated tests is just a better deal than manually checking after each change, if we haven't broke anything in our own code, and if it still does what it is suposed to do. Fair, this is a good reason to write some tests. The even better one, is that if everybody is doing that, we might check if we haven't broke other people solutions in some way - giving us the psychological safety and confidence to change and improve whole code base, without constant feer of accidentaly breaking things in production. 

But there is more, because with some discipline when it comes to describing/writing our tests - hopefully using language of the problem domain - we might judge, if behaviours that we observe in code are intentional or not. Tests become a living documentation. Not rotting confluence document updated two years ago, which might describe what was correct at the time of writing, but not neccesarliy now. Not well intentioned efforts to recall distant past, by the last guy who is still with the company after two years. Documentation that is up to date, because each passing pipeline proves, that whatever is tested is still expected behaviour. 

It gets even more important in the era of Agentic "AI". LLM's do not "think". LLM's predict. Accuracy of their predictions/output is based on quality of input - and you rarely can do better than good test suite, which will suplement their "understanding" of the code by describing wanted and unwanted behaviours, greatly improving dices when they roll for implmplementation. It also give them ability to self correct, if they fail this roll. Our - human - context window is typicaly too small to fit all edge cases and potential side effects in our head or prompt - esspecialy under pressue "delivery cult" puts most of us. 

Before LLM's testing was a good practice sparing us from a lot of stress, now it becomes the only way, to spare yourself "fingers-crossed" moments after production deploy.

# What qualities a good test should exhibit? 
The problem is, that tests while beneficail are still code and code is liability at the best of times - you can get them wrong and greatly diminish the benefits while imposing steep productivity task on everybody around. So, let's try to define what qualities we probably should strive for in tests - so we can later find out how mocking impede us when trying to do so.

There are qualities, that are easy to asses - either your tests have them or not:
* They need to be fast, because if your test suite takes an hour to run, it will make it completly impractical to use & maintain for both agents and fellow programers. 
* They need to be isolated, because debuging race-conditions in test code is as frustrating & soul-destroying endaveur as doing it in production.
* They need to be deterministic, because gains in velocity & reliability from testing, are proportional to the developers confidence in it - random results just destroy it

But there also qualities, that are a bit more nuanced:
* They need to be easliy readable, because if understanding their before/after is high-effort task, they fail they role as documentation.
* They need to be trustworthy, as every false-positive or false-negative - just like with non-deterministic tests, erodes developer confidance - taking most of the benefits off the table.
* They need to be robust, by testing bahaviour - not implementation, to avoid constant productivity/token tax. They should test if our contract with the rest of system is fulfilled - not how exactly it is fullfiled. 
* They need to be cheap to write and maintain - otherwise, both developers and managers will see them as first place, where corners can be cut, making whole excercise moot. 

# How mocking fails you? 
We can argue that library-built mocks can deliver on first three qualities perfectly fine. They can substitute complex dependancies containig ie. complex calculations or heavy IO - which moves us towards our first goal speed. They can replace non-deterministic behaviours - which allows us to make tests deterministic. They are also typicaly light-weight enough to be recreated from scratch for every test, which gives us isolation. They start to fail hard, when it comes to less binary qualities.

Main pain point is complexity of the mocking api - which is managable, while mocking single call to a stateless dependancy (ie. mocked specification object), but get quickly more and more convoluted, as we need to describe argument expectations and return values for multiple intertwined calls to express dependancy state changes as "snapshot" of particular scenario. 

```TypeScript
CODE
```

Suddenly, signal-to-noise ratio of our test goes down, because it gets harded and harder to find meaningfull information in soup of mocking-framework-specific code and understand what is the "arranged" state for the test. Code wiring test together starts to dominate over test "meat & potatoes", at the same time beeing untestable itself and barerly or not at all reusable. 

You loose a lot of readability - because signal gets lost in mocking framework code. You make the test fragile, because every change in implementation forces you to adjust mock. The mock itself becomes constant source of potential false-positives/false-negatives because you have no bullet-proof way of assesing, if your "snapshot" of dependancy behaviour is correct and matching behaviour of dependancy. 

Your tests start to stand on top of untestable code and become high-effort to write and read, therefore costly to write and maintain, therefore one of the first candidates to be cut down or trimmed, when we need to cut-corners under pressure from management. Mitigating those issues by beeing super-humanely carefull and intentional is just too time consuming. 

What is even more concerning, this kind of mocks are AI agents cryptonite. Ideal tool for Agents that got caught in the death-loop of completly loosing the plot and just trying low-effort workarounds. Just like with TypeScript type assertions, mocks will be used by agents as a escape hatch, allowing to reach expected test result without resolving actuall issue. Which will be missed in review, both because signal-noise ratio of mocking and pure volume of agentic output. 

# What are the Test Doubles?
There is a better way - Test Doubles. Which are in essence a hand-crafted objects which expose the same interface as substituted dependancy. There are few kinds of them according to Gerard Meszaros's. 

* Dummy - which does nothing except filling parameters list, 
* Stub - which provides canned responses, 
* Spy - which records informations about how it was used
* Mock - which, exactly like library-created mocks, contains pre-programmed expectations and responses
* Fake - which is bassicaly a simplified implementation of substituted dependancy 

We will focus on the last one, as first three overlap with what library-created mocks can often deliver without creating systemic issues, and Mock - even handcrafted - comes with a subset of problems introduced by mocking libraries that we described above. 








replacing for example depandancy on S3 blob storage with simple in memory map. 

I want to focus here on the Fake or even more specificaly, a Fake as In-Memory representation of application infrastructure, representing statefull dependancies like database repositories & vendor systems. Mostly, because this is the case where library based mocking fails the hardest, but is often used anyway - just because it is already used in the code base for the simpler scenarios. 



While there is a few different kinds of them, we will focus on one particular kind of Test Double to ilustrate thesis of this article - a Fake, and a specific way to think about - as a in-memory implementation of part of our application infrastructure. 


Which is an object which offers simplified implementation of the dependancy we need to substitute for test. 


# Why test-doubles are superior - most of the time? 






, as it require a lot of advocacy upfront and fliping the deeply embeded mental script segregating test and production code in two speraate buckets with diffrent quality & readability expectations. 

The most powerfull of them will be in-memory implementation. 


# What is a long-term cost of mocking? 

# Why mocking fails even harder with AI 

# Alternative approaches



1. Business incentives,
2. Developer incentives 
3. "long-term" impact 
