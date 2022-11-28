---
layout: post
title: "Template"
date: 2022-11-28
tags:
 - [soa]
 - [publish]
 - [subscribber]
 - [event] 
 - [command]  
 - [message]  
 - [sub/sub]
published: true
---

# Some links:

- YEAR - http://link
- Author - 



# My answer:
A tipical flow:
Logic schema:
    compA
        - a1
        - a2 
        - a3

    User

User post to CompA (a1) post `COMMAND` to `queue`
CompA (a2) > read the `queue` do the work emit `EVENT` accomplished to `internal queue`
CompA (a3) > read the `internal queue` and emit `self event` 

               a1            a2          a3  
distilled flow:`HTTP POST` > `COMMAND` > `EVENT`