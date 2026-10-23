---
name: team-topologies
description: Team Topologies reference and review checklist (Skelton & Pais). Use when designing or reviewing team structure, assigning ownership, sizing teams, or drawing a team map; when someone names a team type, interaction mode, cognitive load, Conway's law, or fracture planes.
---

# Team Topologies

Based on Anders Skifte's summary of the book (Smidigalliansen, 2019): https://medium.com/smidigalliansen/oppsummering-av-team-topologies-5a5ab0bef926. The goal throughout is **fast flow**: the shortest time from a need appearing to its fix running in production. Judge every choice by what it does to flow.

## Steps when reviewing a team design

Work through every check below against the proposal in front of you. For each one, record a verdict (holds, strained or broken), the team it concerns, and the evidence. The review is done when every check has a verdict and every team has been named in at least one.

1. **Type**: each team is exactly one of the four types, and its mission matches that type's job.
2. **Size**: each team has 5–9 people. List the teams outside that range and say why they're allowed to be.
3. **Ownership**: each part of the system has one owning team. Look for anything owned by two teams and anything owned by none.
4. **Cognitive load**: no team holds two complicated domains. Name the intrinsic and extraneous load each team carries.
5. **Interactions**: every team-to-team relationship is one of the three modes. Collaboration has an end date.
6. **Flow**: follow one customer-facing change from idea to production. Count the handoffs and the queues it waits in.
7. **Conway**: the team boundaries match the architecture you want. Name the places where they cut against it.
8. **Anti-patterns**: any team built around an activity or a skill is called out, along with its conversion path.

## Teams

A **team** is a stable group of 5–9 people working as one unit toward a shared goal. It is the smallest unit of delivery: give work to teams and let each team decide who does what. Above about nine people, trust weakens (Dunbar's number) and speed, quality and innovation drop.

- **Stable**: trust takes time to build, so change teams only when needed and keep a team that is performing well intact. Adding people lowers capacity at first (Brooks's law).
- **Owned**: each team has bounded areas it owns outright, ideally with the autonomy to plan its own work. When two teams work on the same part of the system, nobody really owns it.
- **Diverse**: a few specialists plus several T-shaped generalists. A team made only of specialists who stay in their lane produces bottlenecks.

## The four team types

Limiting yourself to four types removes ambiguity about roles.

- **Stream-aligned**: owns the whole value stream for one slice of the business (a product, a service, a user journey), from idea to production. This is the primary type, and every other type exists to serve it. It is cross-functional and autonomous: security, design and UX, development, operations, measurement, testing and product ownership live inside it. You can tell it's working when changes flow steadily, the team experiments and learns, it pays down technical debt, and handoffs are rare or absent.
- **Enabling**: specialists who help stream-aligned teams pick up a missing capability, such as continuous delivery. The work is time-limited, and the team aims to make itself unnecessary. If it stays, it becomes a bottleneck. A community of practice does a similar job part-time and more broadly.
- **Complicated subsystem**: builds and maintains a part of the system that only specialists can understand, such as a video codec or a face-recognition engine, so stream-aligned teams don't have to carry that load.
- **Platform**: provides internal services as a product: self-service APIs, tools, knowledge and support. It succeeds when its APIs are stable, high quality and easy to use for developers. Aim for the **thinnest viable platform**: only as much as speeds up the teams that build on it. A platform team is still useful when the platform is mostly third-party services: someone has to notice what is outdated, upgrade it, and bring in what's new.

To convert an existing team, pick the type that best describes how it should work. A DBA team, for example, becomes an enabling team that teaches others to handle storage.

## The three interaction modes

- **Collaboration**: two teams work closely for a defined, limited period, for example to explore new technology or in early-stage innovation. It works best when their skills differ, and it needs shared ownership of the outcome. It costs cognitive load and blurs boundaries, so always give it an end date.
- **X-as-a-Service**: one team consumes another team's API or service. Boundaries are clear and little communication is needed.
- **Facilitating**: one team coaches another so it becomes self-sufficient quickly. This is the enabling team's usual mode.

Any other kind of interaction is waste: it points to unclear boundaries or a team whose purpose isn't understood. Expect modes to change over time. Collaboration often moves to occasional collaboration and then to X-as-a-Service. Seating can steer the mode: put teams together for collaboration, and further apart to push them toward APIs.

## Cognitive load

Cognitive load sets how large and varied a team's area can be. Size the software to fit the team, not the other way round. That usually favours small, loosely coupled services over arguments about monoliths versus microservices.

- **Intrinsic**: the difficulty that comes with the skills and technology, such as a hard language or a growing codebase. Reduce it with training, pairing, technology choices and narrower scope.
- **Extraneous**: mechanics that don't need to be in anyone's head, such as service configuration or provisioning. Automate them away, document APIs, and make work in progress visible.
- **Germane**: the valuable thinking, such as understanding the business domain or how services should talk to each other. Protect most of the team's capacity for this.

Load is hard to measure, so ask the team whether they can do their work effectively. When an area outgrows a team, split it between teams. Don't make several teams share one large area. A team with two complicated domains usually becomes two teams. Overload shows up as lower motivation, mastery and autonomy, and the team breaks into individuals working alone.

## Conway's law

> "Organizations which design systems … are constrained to produce designs which are copies of the communication structures of these organizations."

The org design always shows up in the architecture. When the org doesn't match the architecture you want, change one of them. Reshaping teams to get the architecture you want is the **inverse Conway maneuver**. Org charts show reporting lines, not who really depends on whom, so design from how work actually flows. Split teams first and the system second. Splitting a monolith on the wrong lines gives a distributed monolith, where almost every change touches several services.

## Fracture planes

Natural places to split a monolith or a domain:

- **Business domain**: subdomains, such as playlists, discovery and playback in a music service.
- **Regulation**: keep strictly regulated parts apart so the rest isn't held to the same rules.
- **Rate of change**: a monolith moves only as fast as its slowest part.
- **Performance**: a high-traffic part that has to scale on its own.
- **Location, risk, technology, personas**.

A quick test: "Could we offer or consume this part as a service?" If yes, it's a candidate for its own team.

## Anti-patterns

- **Ad hoc teams**: teams created as a reaction to an incident, such as a DBA team after an outage or a QA team after a bug spike. They create silos and handoffs.
- **Frequent reshuffling** of team members.
- **Teams built around activities or skills**: one-way pipelines from specification to design, code, test, release and operations, with no feedback from production. Build teams around business areas instead.
- **Work routed by who knows what** instead of by what matters most.

## Signals that a team or its area should change

- **The area is too big for the team**: other teams wait a long time for changes, the same people always get changes to one area even when busy or away, and people complain about missing documentation.
- **Delivery has slowed**: throughput and lead time are trending down, changes feel slower, work in progress grows, and more work is blocked waiting on someone outside the team. Common causes are new silos the team depends on, technical debt that turns small changes into regression testing, and missing telemetry.

## Beyond structure

Team design reaches its potential only with good leadership, a healthy culture and modern technical practice, continuous delivery above all (see *Accelerate*). Well-designed teams also make the organisation better at sensing: picking up signals from inside and outside and responding quickly.

## Norwegian terms

stream-aligned = verdistrøm-team · fracture plane = spalteflate · community of practice = faggruppe · cognitive load = kognitiv last (iboende / overflødig / relevant) · collaboration / facilitating = samarbeid / fasilitering
