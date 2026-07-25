---
authors: ["Gniewomir Świechowski"]
title: "Infrastructure-As-Code is still code"
date: "2026-07-25"
tags: ["AI", "Infrastructure", "TDD", "IaC", "Testing", "DevOps"]
categories: ["AI", "Software Engineering"]
draft: false
ShowToc: false
---

I was – and I still am – a cynic when it comes to how AI will affect software development (whole "it's an amplifier" argument + unchanged incentives). Still, after finding a flow which fits my brain, I cannot imagine working without it.

Doing TDD when "devopsing" is hard, so the default observed in the wild was "get it right and pray we do not need to touch it" most of the time. Which often meant that Infrastructure-As-Code made things simpler, but reproducibility was not something you really wanted to depend on.

Now, with a good workflow – while still not free – it's low friction. The agent deals with all the little hoops that made it painful, reducing the number of side quests. You move faster, so return on investment also shows earlier, so you stick to process, avoiding complacency.

I cannot stress enough how good it feels to be able to confirm facts about infra in a repeatable way. It won't save bad design from "Black Friday"-like scenarios, but the number of stupid human/agent-introduced errors/problems it prevents makes it worth it (just don't do it by hand – it has to be part of the workflow).

What remains is the unavoidable slowness of acceptance tests that sometimes need teardown/re-apply of Terraform state, provision, etc. But I take it over the fragility of untested code any day. Infrastructure-As-Code is still code. Untested code is Schrödinger's Code, and I hate opening boxes I do not already know the contents of outside my own dev machine.
