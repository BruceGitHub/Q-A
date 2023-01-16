---
layout: post
title: "Cron vs Ner coding style"
date: 2022-07-02
tags:
 - [cron]
 - [distruited system]
 - [events]
 - [time]
 - [scheduler]
published: true
---

# Some links:

- 2022 - https://luke-gee.medium.com/representing-the-passage-of-time-in-an-event-driven-system-48fc358316e0
- Luke Gee - 

- 2019 - https://verraes.net/2019/05/patterns-for-decoupling-distsys-passage-of-time-event/
- Mattia Verraes - 

- 2018 - https://blog.arkency.com/modeling-passing-time-with-events/
- PAWEŁ PACANA - 

- xxxx - https://szymonpobiega.github.io/SendingMessagesToTheFuture/#/37
- Szymon Pobiega -  


# My answer:
Cron can be util when we need to schedule the same activity at the same time many times
I think that Cron it's ok when:
- the time to check its precise 
- we always have the work to do

I think the Cron isn't ok when:
- the time to check isn't precise
- we haven't always the work to do, but it depends on other gears

I both cases the logic to perform the sigle task, should be put in specific business boundary 

                 +--> handler message
                 |
CRON             |
 |      +------+ |
 +----->| event+-+
        +------+ |
                 |
                 +--> class specifc
