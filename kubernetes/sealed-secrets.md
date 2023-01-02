---
layout: post
title: ""
date: 2023-01-02
tags:
 - [k8s]
 - [kubernets]
 - [sealed-secrets]
 - [pro]
 - [const]
published: true
---

# Vault
- https://github.com/bitnami-labs/sealed-secrets

- https://auth0.com/blog/kubernetes-secrets-management/
```yaml
Disadvantages
- Since it unseals the sealed secrets into regular secrets, you can still decode them if you have access to the cluster and namespace.
- Requires resealing for each cluster environment, as the key pair will be unique for each cluster.
```

