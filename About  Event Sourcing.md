---
layout: post
title: ""
date: 2023-01-11
tags:
 - [es]
 - [event sourcing]
 - [architecture]
published: true
---

# Pitfall
## Dependencies between events
Events should be autonomous and atomic. They should not have any dependencies on any other events.

## Leaky events
An event should be an abstraction that represents a business process. It shouldn’t include the internal implementation details of a service

## Entity based 
This type of entity-based event lacks clarity. It’s not immediately obvious what business process is being represented by

## Means of event
Events should be specific in that they model a single business process. It should be possible to understand what an event means from the title alone

## Sequence
Given that messaging is asynchronous you cannot guarantee the order in which events will be sent, received and processed. 

## Self contained
Events should be self-contained. Publishers should not make any assumptions around how events will be processed by a consumer.

## Commands event
Commands can be useful, but they can undermine service autonomy so should be used sparingly.

## Query event
Commands can be useful, but they can undermine service autonomy so should be used sparingly.

## Events as method calls
??

## Too few messages
??

Reference:

2018 - https://www.ben-morris.com/event-driven-architecture-and-message-design-anti-patterns-and-pitfalls/

