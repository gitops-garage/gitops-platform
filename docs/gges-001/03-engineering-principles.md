## 3.1 Declarative First

Every infrastructure component shall be defined declaratively.

The desired state must always be represented as code and stored in version control.

Manual infrastructure configuration is forbidden.

Benefits:

* Version control
* Auditability
* Reproducibility
* Disaster Recovery
* Predictability

## 3.2 GitOps First

Git represents the single source of truth for the entire platform.

Every operational change must originate from Git.

The cluster must never become the source of truth.

Consequences:

* Every deployment is traceable.
* Every rollback is deterministic.
* Every change is auditable.

## 3.3 Everything as Code

Everything shall be version controlled.

Including:

* Infrastructure
* Kubernetes manifests
* Helm Charts
* Pipelines
* Policies
* Documentation
* Standards
* Diagrams
* ADRs
* Platform configuration

Nothing should exist exclusively inside a running cluster.

## 3.4 Immutable Infrastructure

Containers are immutable.

Applications are immutable.

Images are immutable.

Configuration changes never modify running containers.

Instead:

Application → Image → Registry → Git → ArgoCD → New Deployment

## 3.5 Platform over Projects

The platform provides reusable capabilities.

Applications consume platform services.

Applications must never implement deployment logic internally.

Examples of platform responsibilities:

* CI
* CD
* GitOps
* Registry
* Security
* Observability
* Deployment
* Rollback
* Release automation

## 3.6 Standardization over Customization

The platform favors consistency over individual optimizations.

Every exception increases operational complexity.

Engineering effort should prioritize reusable patterns rather than one-off solutions.

## 3.7 Automation First

Every repetitive task should eventually become automated.

Manual operational procedures represent technical debt.

The long-term objective is zero-click deployments.

## 3.8 Security by Default

Security shall be integrated into the platform rather than delegated to application teams.

Every application inherits a secure baseline.

Security is mandatory, not optional.

## 3.9 Least Privilege

Applications receive only the permissions required to perform their function.

Permissions shall always be explicitly granted.

Default access is denied.

## 3.10 Reproducibility

Given:

* same Git revision
* same Helm Chart
* same OCI image
* same Values

the resulting deployment shall always be identical.

Platform behavior must be deterministic.