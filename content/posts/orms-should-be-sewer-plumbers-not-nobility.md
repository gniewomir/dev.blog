---
authors: ["Gniewomir Świechowski"]
title: "ORMs should be sewer plumbers - not nobility"
date: "2026-04-02"
tags: ["Architecture", "Engineering", "AI", "Good Practices", "Domain Driven Design"]
categories: ["Architecture"]
weight: -1
ShowToc: true
TocOpen: true
draft: false
---

There is a concept that is often misunderstood as “over-engineering” by many developers and managers: why we should not use ORM models as domain entities. My thoughts are applicable mostly to apps where business logic and state mutations are complex, but main performance bottleneck is reads. Yet, I lost count long ago of how many times I was promised a 'simple CRUD' app, only to find something that was neither simple nor CRUD. It was just hard to reason about, because the ORM models had outstayed their welcome as a proper domain substitute.  

## 1. The Write vs. Read Symmetry Fallacy

The ORM creates a false impression that writing and reading data to and from persistence are the same responsibility. Yet, we care about correctness when writing and performance when reading. There is no symmetry here.

ORM models help somewhat with the first problem (they can validate, even if they aren't suited for enforcing invariants across multiple entities), but they actively hinder solving the second. When the ORM is the only tool available, every performance problem looks like a nail. Developers will wrestle with N+1 problems and complex ORM wiring instead of just writing the optimized SQL query the situation demands.

Then after some time, someone will propose a distributed system to fix degrading performance—a transition that is costly, complex, and typically impossible to get right for a company that was unable to maintain a healthy monolith. In a distributed setup, the cost of dealing with that will be pushed upstream to the teams managing API consumers. It will not disappear.

## 2. The Database Model = Domain Entity Fallacy

The ORM creates a false impression that your database models are your domain entities. That can work until you need your first aggregate or a serious change—especially with the Active Record pattern in play. If your line-item is just another service with a few endpoints rather than part of a strict cart aggregate, you can safely assume it will eventually be modified out of turn (e.g., by a queue DLQ redrive after an order is already fulfilled). Now imagine a similar case for a payments module.

Your developers will avoid mirroring the domain in the database schema and code like the plague, as it becomes a high-effort/high-risk activity. Instead of a domain model describing your business, you will get a database model reflecting the difficulty of changing the schema and attached code. This drift is not free—it puts a growing complexity/time/cost tax on every change request/bug report.

A real example I've seen in production: a yacht modeled as a house with an engine, sails, and a home port, with all the special cases scattered across related models & code. Deep coupling created by the ORM made it impractical to model them separately. Now imagine extending that project to handle RVs. I noped out of the aforementioned project to preserve my sanity—there was no realistic way to untangle it.

## 3. The API Resource = Database Model Fallacy

The ORM creates a false impression that the shape of your REST/GraphQL resources should match your database models. They do—for only a short while at the start of the project. When the drift becomes visible, you are already locked-in with workarounds bolted on top in the meantime.

Later, it will become obvious that nobody has thought through what data you should expose and to whom—going with the low-effort default of mapping one-to-one unless explicitly asked to do otherwise, so your public interface surface to maintain is huge. This inevitably leads to the nightmare of property-level authorization rules (instead of clean, endpoint-level rules) and leaves you with no clear vision for how to version your API.

## 4. Integration Tests = Best Fallacy

Heavy use of ORMs pushes your test pyramid towards a pear shape at best and an inverted pyramid at worst. Even rational—not maximalist—coverage of a complex business application will require handling a lot of edge cases for multi-factor decisions. They are typically super cheap to unit test but grow more and more expensive the higher in the hierarchy they are tested.

If your business invariants are tightly coupled with the database through the ORM, then we are entering either the territory of heavy mocking or moving our coverage from fast and cheap unit tests towards expensive and slow integration/e2e tests. In both cases, testing becomes a complex, high-effort/high-cost activity—and people don't do high-effort if they have any say in the matter.

One way or another, you will pay through the fragility of a poorly tested system, waiting for painfully slow test suites and CI pipelines, and long hours spent on writing tests—not features; then you will pay once more for remediation efforts for the aforementioned problems.

## The Plumber vs. First-Class Citizen

What I’m trying to convey is that treating the ORM as a first-class citizen of your domain—instead of a plumber working in the sewer of the infrastructure layer—encourages the wrong (incomplete, leaky, plainly wrong) abstraction for each of the described cases, encourages lazy design, and pushes developers toward ORM-specific workarounds instead of understanding the underlying database.

ORMs are a harness for database writes—not a substitution for database knowledge, a domain modeling tool, or an API prototype.

## Lowest Resistance Path is Human Nature

In an ideal world, all the mentioned problems can be solved even with the ORM as a first-class citizen and without a separate domain-entity abstraction. It just requires clear standards, consistency, and discipline maintained across the whole engineering org for years. Easy.

We don’t live in that world—your developers will take the path of least resistance allowed by your architecture nine times out of ten. So, as a cherry on top, you get more and more inconsistency—confusing both coding assistants and humans.

Architecture choices like delegating the ORM to a subservient role in your infrastructure layer instead of the core of your domain are the most effective way of counteracting the internal rot of your product. They become the new default, as both developers and agents tend to mimic existing structures, and can be enforced by automated checks.

## Show Me The Money

I understand that advocating for abstraction is a voice crying in the wilderness without a spreadsheet describing profits and costs—which, when laying the foundation, will show roughly measurable costs but unclear savings. Yet, regardless of our apparent inability to measure the hidden costs of poor architectural choices upfront, at some point somebody has to ask: how come the complexity of the business domain is roughly the same, and we deliver at a similar pace, but we had to grow the engineering org by 100% in the last 5 years just to keep up? How much money does that cost? Who should own it?

With the rise of AI-assisted or AI-driven coding, these costs and questions may surface much faster—maybe even fast enough to put a price tag on gradually slower output, more defects, and costs that creep up unnoticed for years due to unclear reasons. "AI" will drastically accelerate the timeline from prototype to product to dreaded "maybe we should rewrite?" or "microservices, anyone?". Ultimately, the currently hyped Context Engineering starts with sound engineering.