---
layout: post
title: "Outbox Pattern"
date: 2022-10-13
tags:
 - [outbox pattern]
 - [2pc]
 - [two phase commit]
 - [broker]
 - [Transaction Log Tailing Pattern]
published: true
---

# Some links:
- 2021 - https://microservices.io/patterns/data/transactional-outbox.html
- Chris - 

- 2019 - https://medium.com/engineering-varo/event-driven-architecture-and-the-outbox-pattern-569e6fba7216
- Rod Shokrian - 

- 2019 - https://debezium.io/blog/2019/02/19/reliable-microservices-data-exchange-with-the-outbox-pattern/
- Gunnar Morling - 

# Some links agains

- 2022 - https://softwaremill.com/microservices-101/
- Krzysztof Atłasik - 

- 2022 - https://towardsdatascience.com/distributed-transactions-cdc-event-sourcing-outbox-cqrs-patterns-ee0cf70339b1
- Pankaj Jainani - 

- 2022 - https://softwareengineering.stackexchange.com/a/437957/217727
- Ewan - 

- 2022 - https://betterprogramming.pub/an-alternative-to-outbox-pattern-7564562843ae
- dtm - 

- 2021 - https://exactly-once.github.io/posts/improving-outbox/
- @SzymonPobiega - 

- 2021 - https://www.squer.at/en/blog/stop-overusing-the-outbox-pattern/
- David Leitner - 

- 2020 - https://exactly-once.github.io/posts/outbox/
- @SzymonPobiega - 


# My answer:
Note: 
- Outbox Pattern usually only guarantees at-least-once-delivery
- Limits the applicability of the Outbox pattern to the relational databases
- Table can sometimes put significant stress on your database
- You can create another background process that will delete old and already sent messages