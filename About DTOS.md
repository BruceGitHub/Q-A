---
layout: post
title: "Template"
date: 2022-09-02
tags:
  - [architect]
  - [blog]
  - [design]
  - [dtos]
  - [dop]
published: true
---

# Some links:

- 2020 - https://blog.scottlogic.com/2020/01/03/rethinking-the-java-dto.html
- Steven Waterman -

- https://en.wikipedia.org/wiki/Data_transfer_object

  -- This pattern is often incorrectly used outside of remote interfaces. This has triggered a response from its author[3] where he reiterates that the whole purpose of DTOs is to shift data in expensive remote calls.

  -- A value object is not a DTO. The two terms have been conflated by Sun/Java community in the past

- https://web.archive.org/web/20090426060748/http://blogs.codehaus.org/people/tirsen/archives/000859_data_transfer_objects_makes_me_sick.html

  -- Data Transfer Objects are meant for one single thing, transfer data over a distribution boundary.
  
  -- I personally like the disconnected recordset paradigm which is in the forefront in ADO.NET, but I'm not aware of any non-proprietary implemenations in Java, but auto-generated VO/DAOs are nice too.

- https://web.archive.org/web/20050502011054/http://www.nsquared2.net/johan/viewpost.aspx?PostID=115
- https://www.yegor256.com/2016/07/06/data-transfer-object.html

- https://martinfowler.com/bliki/LocalDTO.html

  -- "Don't underestimate the cost of [using DTOs].... It's significant, and it's painful - perhaps second only to the cost and pain of object-relational mapping".
  
  -- One case where it is useful to use something like a DTO is when you have a significant mismatch between the model in your presentation layer and the underlying domain model.

- https://docs.microsoft.com/en-us/aspnet/web-api/overview/data/using-web-api-with-entity-framework/part-5

  -- A DTO is an object that defines how the data will be sent over the network.

- https://martinfowler.com/eaaCatalog/dataTransferObject.html

- https://jimmybogard.com/immutability-in-dtos/

- https://softwareengineering.stackexchange.com/questions/400953/service-layer-returns-dto-to-controller-but-need-it-to-return-model-for-other-se

  -- A really simple rule of thumb is that you should only use a DTO object when you need to ... transfer data.

- https://docs.microsoft.com/en-us/archive/msdn-magazine/2009/august/pros-and-cons-of-data-transfer-objects

  -- From a pure design perspective, DTOs are a real benefit, but is this theoretical point confirmed by practice, too? As in many architecture open points, the answer is, it depends.

  -- The only alternative to using DTOs is to reference the domain model assembly from within the presentation layer.

  -- Realistically, you can do without DTOs only if the presentation layer and the service layer are co-located in the same process.

  - https://www.pragmaticobjects.com/chapters/010_objects_and_data.html
  
    -- Abstractions based on data are usually unstable

  - http://www.servicedesignpatterns.com/RequestAndResponseManagement/DataTransferObject
  
    -- Data Transfer Objects (a.k.a. DTOs) are reusable classes that contain related data and no business logic.

- https://www.baeldung.com/java-microservices-share-dto
- https://cassiomolin.com/2016/03/23/why-you-should-use-dtos-in-your-rest-api/
- http://wiki.c2.com/?DataTransferObject
- https://www.yegor256.com/2020/05/19/veil-objects.html
- https://pauldambra.dev/2014/04/a-dto-by-any-other-name-would-implement.html
- https://www.adam-bien.com/roller/abien/entry/how_evil_are_actually_data

# Alternative:

- https://vaadin.com/learn/tutorials/ddd/ddd_and_hexagonal#_domain_payload_objects
- https://www.g4s8.wtf/posts/2019-09-06-instead-of-dto/
- https://web.archive.org/web/20170620063845/https://vaughnvernon.co/?page_id=40



# My answer:
