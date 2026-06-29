# Adoption Guide

## Purpose

This guide describes the recommended process for onboarding an existing application into the GitOps Garage platform.

The objective is to provide a repeatable methodology that minimizes deployment risks while ensuring consistency across projects.

The process is technology-agnostic whenever possible and focuses on GitOps best practices.

---

# Adoption Process

The onboarding process is divided into several phases.

Each phase has a clear objective before moving to the next one.

```
Assessment

↓

Containerization

↓

Helm Packaging

↓

CI Pipeline

↓

GitOps Repository

↓

Argo CD

↓

Validation

↓

Production
```

---

# Phase 1 - Assessment

Understand the application before introducing automation.

Questions to answer:

* What language is used?
* How is the application currently deployed?
* Are there external dependencies?
* Does the application already run in containers?
* Are configuration files externalized?
* How are secrets currently managed?

Deliverable:

Application assessment document.

---

# Phase 2 - Containerization

If the application is not already containerized, create a production-ready Docker image.

Objectives:

* Small image size
* Reproducible builds
* Health checks
* Non-root execution whenever possible

Deliverable:

Dockerfile

Container image

---

# Phase 3 - Helm Packaging

Package the application as a Helm Chart.

Objectives:

* Parameterized configuration
* Environment-specific values
* Reusable deployment templates

Deliverable:

Helm Chart

---

# Phase 4 - Continuous Integration

Create a Tekton Pipeline responsible for:

* Clone source
* Build application
* Execute tests
* Build container image
* Push image to registry
* Update GitOps repository

Deliverable:

Working CI Pipeline

---

# Phase 5 - GitOps Configuration

Define the desired application state inside the GitOps repository.

Typical resources include:

* Namespace
* Helm values
* Argo CD Application
* Environment configuration

Deliverable:

GitOps repository updated.

---

# Phase 6 - Continuous Deployment

Argo CD continuously synchronizes the desired state with the Kubernetes cluster.

Objectives:

* Automated deployments
* Drift detection
* Rollback support

Deliverable:

Application deployed by GitOps.

---

# Phase 7 - Validation

Validate that:

* Application is reachable.
* Health probes succeed.
* Logs are clean.
* Pipeline completes successfully.
* Argo CD reports a healthy application.

Deliverable:

Deployment validation report.

---

# Phase 8 - Production Readiness

Before handing over the platform, verify:

* Documentation
* Monitoring
* Resource limits
* Security
* Backup strategy
* Disaster recovery considerations

Deliverable:

Production-ready deployment.

---

# Expected Outcome

After completing the adoption process, the application should:

* Be fully managed through Git.
* Deploy automatically.
* Support reproducible deployments.
* Follow GitOps principles.
* Require minimal manual intervention.
