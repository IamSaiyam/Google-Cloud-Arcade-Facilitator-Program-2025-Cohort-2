# Continuous Delivery with Jenkins in Kubernetes Engine

**Lab Duration:** 1 hour 15 minutes  
**Difficulty:** Intermediate  
**No cost**

---

## Overview

This lab focuses on implementing a complete **Continuous Delivery (CD) pipeline** using Jenkins deployed on Google Kubernetes Engine (GKE). It explores how containers, Kubernetes, and Jenkins integrate to automate building, testing, and deploying applications.

![Kubernetes Engine](https://cdn.qwiklabs.com/1b%2B9D20QnfRjAF8c6xlXmexot7TDcOsYzsRwp%2FH4ErE%3D)

---

## New Technologies & Concepts Introduced

- **Google Kubernetes Engine (GKE):** Managed service to deploy, manage, and orchestrate containerized applications with Kubernetes.
- **Jenkins:** Industry-standard open-source automation server for CI/CD pipelines.
- **Helm:** Kubernetes package (chart) manager to deploy complex applications easily.
- **Continuous Delivery/Deployment:** Automated pipeline approach to push code from development to production, including canary releases for safe incremental updates.
- **Canary & Production Deployments:** Releasing new versions to a small set of users first (canary) before serving everyone (production).

---

## What This Lab Teaches

- Provisioning a Kubernetes cluster on GKE for CI/CD workloads.
- Deploying Jenkins on Kubernetes using Helm.
- Configuring Jenkins so it can interact with container registries and source control (GitHub).
- Setting up RBAC (role-based access control) for secure deployments.
- Creating and scaling multiple Kubernetes deployments (canary, production) for the same service.
- Automating the build/test/deploy lifecycle with Jenkins pipelines (including writing/modifying a Jenkinsfile).
- Performing canary deployments for safer releases.
- Using `kubectl` for cluster management and `helm` for application deployment.
- Retrieving and using Jenkins admin credentials via Kubernetes secrets.
- Using service IPs and load balancers to access deployed applications.

---

## Sample Useful Commands Learned

Provision Kubernetes Cluster:
```
gcloud container clusters create jenkins-cd
--num-nodes 2
--machine-type e2-standard-2
--scopes "https://www.googleapis.com/auth/source.read_write,cloud-platform"
```


Deploy Jenkins with Helm:
```
helm repo add jenkins https://charts.jenkins.io
helm repo update
helm install cd jenkins/jenkins -f jenkins/values.yaml --wait
```


Scale a Kubernetes Deployment:
```
kubectl scale deployment gceme-frontend-production -n production --replicas 4
```


Check front end service version using curl:
```
curl http://$FRONTEND_SERVICE_IP/version
```


Looping over service version output (test canary/production split):
```
while true; do curl http://$FRONTEND_SERVICE_IP/version; sleep 1; done
```

Get Jenkins admin password from Kubernetes secret:
```
printf $(kubectl get secret cd-jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
```
---

## What I Learned

- **How to architect and deploy a multi-environment (canary, production) application with Kubernetes and Jenkins.**
- **The benefits of containerized builds and ephemeral build agents in Kubernetes for efficiency and scalability.**
- **Using Helm simplifies the deployment and management of complex apps such as Jenkins on Kubernetes.**
- **How to write and customize Jenkinsfiles to define robust deployment pipelines.**
- **Practical canary deployment strategies for safer rollouts and real-world testing.**
- **How continuous integration and continuous delivery (CI/CD) can accelerate software development and improve reliability.**
- **How GKE's global load balancer and Kubernetes services route user traffic efficiently and securely.**
- **Integrating DevOps best practices with Google Cloud tools and open-source automation frameworks.**

---

This lab provided practical experience with modern DevOps tooling and scalable application delivery using Kubernetes and Jenkins—skills fundamental to any cloud native and container-based development workflow.