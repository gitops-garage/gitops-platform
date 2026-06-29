## 1. Git is the Single Source of Truth
**Never rely on manual changes in the cluster.**
The Git repository is the absolute authority for infrastructure and application state. All changes must be committed to Git first. Manual modifications are forbidden and will be automatically reverted by our reconciliation tools to prevent configuration drift and ensure consistency.

## 2. Total Reproducibility
**Everything is reproducible from Git.**
If a cluster is lost or corrupted, the entire platform must be instantly rebuildable from scratch using only the Git configuration. We design for immutable infrastructure, ensuring no "snowflake" environments and guaranteeing instant disaster recovery.

## 3. Simplicity Wins
**Choose the simplest solution.**
If a task can be solved with one tool instead of three, we choose the one. We prioritize simplicity, maintainability, and reliability over complexity, reducing the blast radius of failures and lowering operational overhead.

## 4. Templates Over Unique Projects
**Build once, reuse everywhere.**
We avoid one-off solutions. Every component, pipeline, or module is designed as a reusable template (e.g., Helm Charts) to ensure consistency, speed, and standard quality across all client deployments.

## 5. Documentation as Code
**Docs are as important as code.**
Documentation lives in the repository, is versioned, and requires review. It must be comprehensive enough for a client to understand, operate, and troubleshoot the platform independently without constant support intervention.