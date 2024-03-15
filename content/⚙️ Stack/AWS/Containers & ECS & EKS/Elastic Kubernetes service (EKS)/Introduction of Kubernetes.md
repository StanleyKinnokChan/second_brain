# Introduction of Kubernetes

- container orchestration system
- automate the deployment, scaling & management of containerized application
- cloud agnostic, on-premise with cloud platform

**High-level architecture**

[[Introduction of Kubernetes/Untitled.png]]

[[Introduction of Kubernetes/Untitled 1.png]]

**Concept:**

- cluster - a deployment of kubernetes, management, orchestration
- Note - Resources; pods are placed on node to run
- Pod - 1+ Containers; smallest unit in kubernetes; often 1 container 1 pod
- service - abstraction, service running on 1 or more pods
- Job - ad-hoc, creates one or more pods until completion
- ingress - exposes a way into a service (ingress⇒ routing ⇒ service ⇒ 1+pods)
- ingress controller - used to provide ingress (e.g. AWS LB controller uses ALB/NLB)
persistent storage (PV) - volume whose lifecycle lives beyond any 1 pod using it
