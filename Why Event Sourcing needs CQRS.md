---
layout: post
title: "Why Events Sourcing Needs CQRS"
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
 - [consistency]
 - [invariant]
 - [context]
published: true
---

# Questions
- One of the largest issues when using Event Sourcing is that you cannot ask the system a query such as “Give me all users whose first names are 'Greg'”. This is due to not having a representation of current state"

# Video:

- 2014 - Event Sourcing - https://youtu.be/8JKjvY4etTY?t=1801 
- Greg Young -
I can't query of serie of Events