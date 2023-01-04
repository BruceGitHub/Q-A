---
layout: post
title: ""
date: 2023-01-02
tags:
 - [sc]
 - [k8s]
 - [kubernets]
 - [secretes]
published: true
---

# SECRETS IN CONFIG-MAP
- https://kubernetes.io/docs/tasks/configmap-secret/managing-secret-using-config-file/
- https://www.cloudytuts.com/tutorials/kubernetes/how-to-configure-node-based-apps-in-kubernetes/
- https://youtu.be/tWc3wfC8sOc?t=904
- https://hackernoon.com/kubernetes-secrets-and-configmaps
- https://unofficial-kubernetes.readthedocs.io/en/latest/concepts/configuration/secret/
- https://itnext.io/kubernetes-explained-deep-enough-configuration-cd4a9d1d8dcd 
- https://azuredevcollege.com/trainingdays/day7/challenges/challenge-3.html



  Example of secrets with custom path
  ```yaml
    {
    "apiVersion": "v1",
    "kind": "Pod",
    "metadata": {
        "name": "mypod",
        "namespace": "myns"
    },
    "spec": {
        "containers": [{
        "name": "mypod",
        "image": "redis",
        "volumeMounts": [{
            "name": "foo",
            "mountPath": "/etc/foo",
            "readOnly": true
        }]
        }],
        "volumes": [{
        "name": "foo",
        "secret": {
            "secretName": "mysecret",
            "items": [{
            "key": "username",
            "path": "my-group/my-username"
            }]
        }
        }]
    }
    }  
  ```  

# SECRETS TYPE
- https://spacelift.io/blog/kubernetes-secrets#types-of-kubernetes-secrets
- https://kubernetes.io/docs/concepts/configuration/secret/#docker-config-secrets

# Vault
- https://www.vaultproject.io/use-cases/kubernetes [annotated](/kubernetes/secrets-best-pratics.md)
- https://github.com/bitnami-labs/sealed-secrets [annotated](/kubernetes/sealed-secrets.md)
    - https://auth0.com/blog/kubernetes-secrets-management/
    
- https://www.cncf.io/blog/2022/01/25/secrets-management-essential-when-using-kubernetes/

- https://aws.amazon.com/it/secrets-manager/
- https://www.godaddy.com/engineering/2019/04/16/kubernetes-external-secrets/
- https://secrethub.io/docs/guides/config-files/
- https://www.godaddy.com/engineering/2019/04/16/kubernetes-external-secrets/