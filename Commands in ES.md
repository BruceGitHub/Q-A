---
layout: post
title: "Command in Eventsourcing"
date: 2022-05-12
tags:
 - [es]
 - [event sourcing]
 - [command]
 - [value object]
 - [scalar]
published: true
---

# Some links:
-  


# My answer:

The basic idea is that a "command" is part of the domain and a "command" is a value object, so go over the wire
the basic schema is this 


```
incoming request: primitive as parameters
internal: parse to value obejct
outgoing: primitive as parameter 
+o-
```
