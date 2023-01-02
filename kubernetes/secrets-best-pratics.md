---
layout: post
title: ""
date: 2023-01-02
tags:
 - [bestpratics]
 - [k8s]
 - [kubernets]
 - [secretes]
published: true
---

# Store secrets in file instead to pass with ENV 

Secrets with `data` (encoded) and `stringData` (plain)
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: YWRtaW4=
stringData:
  username: administrator
```

# Layer of isolation