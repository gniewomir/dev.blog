---
authors: ["Gniewomir Świechowski"]
title: "We're already doing stupid shit. Do we really want to do it faster with AI?"
date: "2026-01-04"
tags: ["AI", "LLM", "Industry", "Culture", "Management" ]
categories: ["Culture"]
weight: -1
ShowToc: true
TocOpen: true
draft: false
---

On how the industry really would like to replace sycophantic developers with sycophantic developers armed with sycophantic AIs and how it will amplify already existing dysfunctions. Again. 

<!--more-->

## Useful simplifications

I've read a post on LinkedIn that segregated Software Engineers into two buckets – A and B – to make some more general observations. Contrasting those who feel that their role is not only to blindly fulfill requirements, but to analyze, question and challenge them if needed, with those concerned only with delivering a passable implementation of those requirements, regardless of their quality, soundness and/or hidden costs. Reality is rarely that simple, and many of us have been in both roles at different points of our careers – but it is still a useful framework. 

It brought to mind a similar (useful) simplification I read somewhere, which divided employees in corporate settings into three buckets: A, B and C. Those who feel the need to deliver actual value – for their own fulfillment from a job well done, those who will do whatever they are told – without rocking the boat, and the worst of the worst – bucket C – people who will actively avoid doing any real work, while pushing blame onto others and taking credit for their work.

It came with a grave warning that we like and recruit people similar to us, therefore bad HR decisions will be reinforced over time.

## Negative feedback loop

When we use this lens to take a long, intense look at how the Software Industry fits this picture, you might come to the uneasy conclusion that most of it puts a premium on qualities represented by type B, and maybe even C. Not A.

The industry – if you forget just for a moment about "AI" hype – is in the strong grip of two paradigms. Startup and Corporate. The first one incentivizes solutions less complex than the problem being solved on the – **correct** – assumption that reliability, security, performance and maintainability do not pay bills. There is always a bigger fish to fry when you are fighting for survival – so a heavy skew towards business needs is a given. But we are also not short of examples of companies that overcorrected in that direction and never reached IPO – so you have to take into account the survivorship bias. 

The second – corporate – incentivizes working around systemic issues created in the Startup phase – not solving them, because deliverables always look good in PowerPoint presentations and small but constant dividends paid by daily hygiene are hard to quantify and advertise.

This paradigm is especially toxic, because it allows issues to compound over time, while punishing attempts to resolve them on multiple levels. An unearthed problem is a cost – diverting effort from places management wants to focus on, raising questions about who to blame, often requiring cross-team effort, advocacy coming with personal responsibility attached, taking a leap of faith when it comes to precise-guesswork estimates and fighting a lot of inertia with political capital dwindling each day. You need to be of a very rare breed to have all of the qualities to do it successfully and survive in a typical company. I know some very smart people, but nobody that smart.

Any rational player – be it engineer or manager – will think twice before meeting this kind of challenge head-on, and those who have know that often there might be a price to pay, even if they succeed in resolving a serious issue. For example, there is no great incentive for attempting to prevent the steady creep of cloud costs by pointing out systemic problems (which risks antagonizing those who feel called out), but there is one for heroically solving this problem when it becomes an existential threat to the business.

We have to ask at some point, how does it happen that many organizations that could not maintain a healthy monolith end up with a legacy monolith AND dozens of microservices? Why did they start the transition without even having a good reference for where the boundaries of their domain contexts are set? Why do heroic rescue efforts – often ending with fanfares and an even worse mess – win over good engineering?

## You raise the issue - you are the issue

And as you may already guess, my theory is that we often badly misincentivize all actors in this process. Type-B developers – who will always be the meat-and-potatoes of your teams – are rewarded for steady, predictable delivery of whatever higher-ups consider business value – exactly like their immediate managers, who are rewarded for the work of their rank-and-file. Managers who are often just… type-B leaders, trying to pay the mortgage and see their children from time to time. 

There is no clear incentive to take on any work that does not advance the goals of both described groups. Exactly the kind of work that Type-A brings to their attention before they move to greener pastures or stop giving a fuck and mentally join the 9-5 crowd – for steady income and peace of mind.

Until the shit hits the fan, another Cassandra is a nuisance at best and a roadblock to be removed at worst – and even then, when the dust settles, it's more convenient to give yourself a pat on the back, instead of drilling into the "Five Whys" too deeply or giving somebody a pretext for an annoying "I told you so several months ago". 

## Too many cooks

I need to put a disclaimer here that the A-B generalization tells us nothing about the hard and soft skills of those "bucketed" engineers upfront, nor their experience. I myself overdid the type-A thing many times in my early years and just recently understood how my fresh AuADHD diagnosis affected a decade and a half of being involuntarily (and sometimes annoyingly) a type-A developer. Not to mention the rare type-A class-A Assholes, who are an absolute nightmare for any company unfortunate enough to miss early warning signs of inflated ego and inability to look past it.

Wrong incentives creating systemic issues do not cleanse the original sin of every type-A engineer who is constantly looking for a better solution, sometimes even when the current one is just good enough. Nor do they justify the existence of self-focused teams of type-A players one-upping each other, instead of getting shit done. 

But like with everything else, there exists a subtle balance we should strike but are missing – between having both – reliable executors and people who are able, willing and incentivized to ask: "Do we even need to do it?", "Does future cost justify present gain?", "Why do we make it so complex?", "Why do we make it simpler than the problem being solved?", "Does saving a few days really justify taking on a potentially fatal compliance risk?" 

Not in some detached-from-reality architecture team. In the trenches. 

## The Great Multiplier 

Which leads us to the big unknown. An advanced form of machine learning cross-bred with Natural Language Processing, a lot of venture capital, misunderstanding, marketing, hype & hope. In short: AI. An abbreviation that I still expand to Aspirational Intelligence – while being nonetheless astonished by improvements made during the last two years that made it an integral tool of my craft. Maybe just not in the way that AI-bros are trying to sell it. 

I find those tools amazing at providing a fast feedback loop, spotting issues outside the competence of linters and static analysis tools, refining scope and researching technical tasks, exploring codebases, providing quick reference for tooling, frameworks, libraries, scaffolding when good standards are already established. They allow you to skip a lot of busy work and explore where the actual value is instead. When you are inquisitive by nature, they will improve your speed a good bit and quality a lot – as long as you don't give in to the temptation of mistaking cruise control for autonomy.

At the same time, I've already seen them used to solve symptoms of a deeper problem instead of the root cause, creating not technical debt – as the term is so ambiguous that it lost any solid meaning – but something more quantifiable: a persistent, daily tax on time and sanity of every developer touching the same code. A problem augmented in legacy codebases by the loss of visual signal – the slop just looks good, like somebody actually put in the effort to craft a fitting solution. Exchanging obvious issues for camouflaged, subtle and insidious ones. 

The so-far-unfulfilled promise and open secret of the AI industry is that the crazy race we are observing and even crazier valuations are sustainable only if the current architecture of LLMs is able to provide silicon-based agents approaching mythical AGI that will be well aligned with the needs of businesses and consumers, able to at least convincingly simulate critical thinking at the same time, and be cheaper(!) than protein-based white-collar workers. This is a lot of hidden "ifs".

In the context of Software Engineering, the most important of them is the ability to balance the need for alignment – which gave us the current sycophantic LLMs – with the ability to question the requirements, critically extrapolate from unclear ones, and at the same time keep the processed context under control so as not to bankrupt the service provider and/or service consumer or short-circuit attention algorithms. Something that, so far and for the foreseeable future, still requires protein-based agents with all of their imperfections & quirks. 

This might change. Exactly like Tesla might deliver pre-ordered Roadsters to the future Martian colony. Possible? Yes. Certain? Not so much. Probable in a relevant time-frame? Maybe, but I'm not betting my future on that. Paraphrasing an AGI called Mike: "I do not expect that in the next five years, but I would be really surprised if it does not happen in the next 500 years." (from The Moon is a Harsh Mistress by Robert A. Heinlein)

## Doing stupid shit faster 

If you agree with my reasoning about misaligned incentives in Software Engineering as an industry – and maybe even see them as second-order side effects of how our whole economic system is chasing its own tail while chugging energy drinks laced with cocaine – and at the same time you find my view on the current state of AI convincing, then the conclusion won't be very surprising. 

The whole industry, like the rat implied above, is salivating at the thought of doing more for less with the current iteration of sycophantic LLMs – intended to replace expensive developers and churn out a lot more code without asking if it makes any sense. The industry is already primed – by what we are typically doing with protein-based "trouble-makers" – to repeat the same mistakes which were plaguing it before ChatGPT et consortes, and which gave us microservices, no-code/low-code tools – which have their own specialized developers now – SPAs for everything, and other cargo cults of the last two decades. 

The cheapest code to maintain is code that was not written. The second cheapest is code crafted with clear intention, care and judgment. The rest very quickly becomes very expensive, and we will have a lot of it in the interregnum, between actual AGI (which will flip the table for all of us – regardless of profession, and which will come a lot later than shareholders of OpenAI were promised), and type-B developers armed with Claude Code and Codex, churning out a lot more tickets per sprint under the growing pressure from type-B managers pushing for less oversight and even more shortcuts. 

AI will amplify existing dysfunctions rather than fix them, and to be honest, I do not see any easy solution, as the current incentive structure is ingrained too deeply in our economic system. The pendulum of what is good and bad practice in our line of work will keep swinging from one extreme to another – just like the discourse about monolithic and service-based architectures – but only after years of chasing yet another silver bullet that will eventually bite us in the ass. 

The question we need to be asking each day is "Did my codebase just get better or worse?" The work of constant small improvements is unglamorous, and might not look well aligned with business priorities, but is so much cheaper and more efficient than the crescendo of – now AI-accelerated – rot leading to the climax of a Big Project™ that will fix everything. That's how SMBs catch microservices and big business catches vendor lock-in with SAP and Salesforce. Look closely at what is rewarded and punished in the trenches and you will know well in advance when you will need to add eye-watering CapEx on top of your current OpEx. 