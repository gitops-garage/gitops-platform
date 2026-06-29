# Repository Architecture

## Purpose

GitOps Garage is designed as a modular platform composed of multiple repositories, each with a single responsibility.

Instead of maintaining all platform components in a monolithic repository, GitOps Garage separates documentation, reusable platform components, example applications and automation into dedicated repositories.

This approach improves maintainability, scalability and allows each repository to evolve independently while keeping a consistent development workflow.

---

# Repository Overview

The GitOps Garage organization is structured around several repositories, each responsible for a specific area of the platform.

| Repository       | Purpose                                                                     |
| ---------------- | --------------------------------------------------------------------------- |
| gitops-platform  | Core platform documentation, architecture and reusable Kubernetes resources |
| gitops-examples  | Sample applications demonstrating the platform capabilities                 |
| gitops-bootstrap | Automated installation and bootstrap process                                |
| gitops-catalog   | Reusable Tekton Tasks, Pipelines and Helm components                        |
| gitops-gitops    | GitOps configuration repositories consumed by Argo CD                       |

---

# Responsibilities

## gitops-platform

The central repository of the project.

Contains:

* Platform architecture
* Documentation
* Kubernetes manifests
* Helm charts
* Platform configuration
* Design decisions

This repository represents the product itself.

---

## gitops-examples

Contains sample applications used to validate and demonstrate the platform.

These examples should remain intentionally simple and focus on showcasing the GitOps workflow rather than application complexity.

---

## gitops-bootstrap

Responsible for installing and configuring the platform.

Typical responsibilities include:

* Namespace creation
* Platform installation
* Initial configuration
* Cluster bootstrap
* Optional Ansible automation

---

## gitops-catalog

A reusable catalog of CI/CD building blocks.

Examples:

* Tekton Tasks
* Tekton Pipelines
* Helm libraries
* Shared templates

Projects should consume these resources instead of duplicating them.

---

## gitops-gitops

Stores the desired state of Kubernetes environments.

This repository is continuously monitored by Argo CD and acts as the deployment source for applications.

---

# Repository Relationships

Each repository has a single responsibility but collaborates with the others through GitOps principles.

Typical flow:

Developer
→ gitops-examples
→ Tekton Pipeline
→ Container Registry
→ gitops-gitops
→ Argo CD
→ Kubernetes Cluster

The platform repository provides the reusable building blocks used across the ecosystem.

---

# Naming Conventions

Repositories follow a consistent naming strategy.

Examples:

* gitops-platform
* gitops-bootstrap
* gitops-catalog
* gitops-examples
* gitops-gitops

This convention improves discoverability and reinforces the platform identity.

---

# Future Repositories

As GitOps Garage evolves, additional repositories may be introduced.

Possible future repositories include:

* gitops-observability
* gitops-policies
* gitops-terraform
* gitops-openshift
* gitops-website

New repositories should only be created when they represent an independent responsibility.

---

# Design Decision

GitOps Garage intentionally favors multiple focused repositories over a monolithic structure.

This design promotes:

* Clear ownership
* Better reuse
* Easier onboarding
* Independent versioning
* Simpler maintenance
* Better scalability

Every repository exists for a specific purpose and contributes to the overall platform architecture.
