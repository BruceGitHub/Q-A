---
layout: post
title: "How to design an aggregate "
date: 2022-01-25
tags:
 - [ddd]
 - [architecture]
 - [domain driven design] 
 - [aggregate] 
 - [domain model]
 - [ubiquitus language]
 - [event sourcing]
 - [repository]
published: true
---

# Some links:

- 2021 - Derek Comartin - https://codeopinion.com/aggregate-root-design-behavior-data/
Separate data from behavior, so two-class data, one class only with data  for the ORM one form Method. 
Without ORM obviously, we need to implement the dirty check pattern a manner is with events

- 2021 - Awkward Aggregate Root relationships and how to rethink them - Nick Chamberlain - https://buildplease.com/pages/on-paper/
How to model an Aggregate Root without computer

- 2019 - All our aggregates are wrong - Mauro Servienti - https://www.youtube.com/watch?v=hev65ozmYPIe
Repo: https://github.com/mauroservienti/all-our-aggregates-are-wrong-demos#ndc-copenhagen
Design around the behaviour. 
Domain expert trap, the domain expert gives some indications upon on its point of view. This isn't the direct "artifact" that go in the code solution

- 2011- Effective Aggregate Design - Vaughn Vernon 
https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf
https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf
https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf

- 2017 - How do We Write Factories for Event Sourced Aggregates? - Nick Chamberlain - https://buildplease.com/pages/constructing-aggregates
Suggests to use a factory to create an AggregateRoot, in particular, suggest to use `ubiquitous language` not `create` for example but `hire` `customer`

- 2013 - Martin Fowler - https://martinfowler.com/bliki/DDD_Aggregate.html
>Any references from outside the aggregate should only go to the aggregate root. The root can thus ensure the integrity of the aggregate as a whole.

- 2009 - Don’t Create Aggregate Roots - Udi Dahan - https://udidahan.com/2009/06/29/dont-create-aggregate-roots/
Draft: "Aggregate root isn't entity is a use case"


# What means transactional boundary 
wip 

# My answer:
First, the transaction boundary rule for the aggregate isn't a rule is 
good guidelines, suggestions.
The origin of this is 
- to void to load more data from the DB, 
- to avoid the problem of the lock from the persistent layer.
- to keep the concept simple and testable 

In fact, in past was common practice to persist a huge quantity of data, into the persistent layer, 
so more locks and more failed transactions, when workload increased