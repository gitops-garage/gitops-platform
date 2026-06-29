# Platform Design

## Purpose

GitOps Garage is designed to provide a reusable, Kubernetes-native GitOps platform that enables fast, consistent and reliable application delivery.

The platform is built around simplicity, reproducibility and standardization, allowing new projects to be onboarded with minimal effort while following the same operational model.

## Design Goals

* Standardize application delivery.
* Minimize manual operations.
* Keep Git as the single source of truth.
* Be cloud-agnostic.
* Support multiple Kubernetes distributions.
* Encourage reusable components over project-specific implementations.

## Architectural Principles

### Git as the Source of Truth

All platform and application changes must be declared in Git repositories.

### Kubernetes Native

The platform should leverage Kubernetes primitives whenever possible instead of introducing unnecessary abstractions.

### Reusable Components

Pipelines, Helm charts and deployment manifests should be reusable across different projects.

### Separation of Responsibilities

The platform separates:

* Application source code
* CI pipelines
* GitOps configuration
* Runtime infrastructure

This separation improves maintainability and simplifies onboarding.

## Platform Components

The platform is composed of:

* Source Control (Gitea)
* CI Pipelines (Tekton)
* GitOps Controller (Argo CD)
* Kubernetes Runtime
* Helm Charts
* Supporting automation scripts

## Repository Philosophy

Every directory has a single responsibility.

The repository is intentionally structured to remain understandable as the platform grows.

## Future Evolution

Future versions will introduce:

* Shared pipeline catalog
* Bootstrap automation
* Policy management
* Infrastructure provisioning
