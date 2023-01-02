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
```txt
Disadvantages
- Since it unseals the sealed secrets into regular secrets, you can still decode them if you have access to the cluster and namespace.
- Requires resealing for each cluster environment, as the key pair will be unique for each cluster.
```

- https://codefresh.io/blog/handle-secrets-like-pro-using-gitops/

- https://medium.com/@gundogdu.emre/kubernetes-secret-management-alternatives-f2b3427a745
```txt
- the SealedSecret and Secret must have the same namespace and name. This is a feature to prevent other users on the same cluster from re-using your sealed secrets
- Sealing key renewal: Sealed secrets are not automatically rotated and old keys are not deleted when new keys are generated. Old sealed secrets resources can be still decrypted (that’s because old sealing keys are not deleted).
- The sealing key renewal and SealedSecret rotation are not a substitute for rotating your actual secrets.
- Needs CRS for custom resource SealedSecret
- Needs kubeseal client side binary to encrypt secret
- sealed-secret.yaml keep with other manifest in git, secret.yaml can be deleted because it never used.
- It is not support external secret store like Vault, Cloud Provider Services (KMS, SSM, Azure Keyvault etc.)
```

