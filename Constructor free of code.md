---
layout: post
title: "Constructor free of code"
date: 2022-03-30
tags:
 - [ddd]
 - [architecture]
 - [domain driven design] 
 - [aggregate] 
 - [domain model]
 - [invariant]
 - [constructor]
published: true
---

# Some links:

WIP Study
- https://localheinz.com/blog/2022/03/26/naming-constructors
- https://verraes.net/2014/06/named-constructors-in-php/
- https://blog.millermedeiros.com/constructors-should-not-cause-side-effects/
- Meyer's OOSC. I
- If a side effect is only concrete — does not affect the abstract state — it is harmless. In the object-as-machine metaphor, functions producing concrete-only side effects correspond to query buttons that may produce an internal state change having absolutely no effect on the answers given by any query button. For example the machine might save energy by automatically switching off some internal circuits if nobody presses a button for some time, and turning them on again whenever someone presses any button, queries included. Such an internal state change is unnoticeable from the outside and hence legitimate.
- https://tmont.com/blargh/2014/4/constructors-should-not-have-side-effects
- http://misko.hevery.com/code-reviewers-guide/flaw-constructor-does-real-work/
- https://www.yegor256.com/2015/05/07/ctors-must-be-code-free.html
- https://matthiasnoback.nl/2018/07/objects-should-be-constructed-in-one-go/
- https://stackoverflow.com/a/1373419
- https://softwareengineering.stackexchange.com/questions/343447/should-constructors-ever-be-used-only-for-side-effects



# My answer:
