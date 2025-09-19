# OPS

## Release: Promote tested models and pipelines to production-readiness.

- Enforce **quality gates** and validate readiness: Apply measurable criteria such as performance thresholds, robustness checks, basic security requirements, and auditability to ensure compliance and reproducibility. Complement automated validations with expert reviews involving data scientists, ML engineers, meteorologists, and compliance officers before promotion.

- **Register** release candidates: Store trained models, metadata, and lineage in a model registry (e.g., *MLflow*) assigning a unique version number to support promotion workflows and enable traceability.

- Manage release **stages**: Tag versions and lifecycle stages (e.g., *Staging*, *Production*, *Archived*) for code, container images, and models. Automate stage-tagging in CI/CD pipelines to maintain consistency.

- Integrate releases into **CI/CD** pipelines: Automate the execution of quality gates and artifact stage-tagging as integral parts of the release workflow. Ensure versioned releases support rollback mechanisms to restore previous stable states in case of failure.

## Deploy: Serve models reliably across deployment stages.

- Choose deployment **host**: Select the deployment infrastructure — HPC clusters, cloud platforms, or on-premises — based on resource availability, data privacy, security, scalability, and data sovereignty requirements.

- Define deployment **targets**: Determine execution mode: batch jobs, real-time APIs (e.g., REST), edge deployments, or embedded systems, based on latency, throughput, and use case needs.

- Select deployment **platform**: Choose a suitable framework for your target and host. Examples include [*FastAPI*](https://fastapi.tiangolo.com/) for REST endpoints or [*Kubernetes Jobs*](https://kubernetes.io/docs/concepts/workloads/controllers/job/) for batch workloads.

- **Decouple configuration** setup: Inject runtime settings (e.g., endpoints, thresholds) via environment variables or config files to separate logic from environment-specific concerns.

- Manage **infrastructure with code**: Use Infrastructure as Code (IaC) tools like [*Terraform*](https://www.terraform.io/) to provision, version, and manage infrastructure (e.g., [*AWS Lambda*](https://aws.amazon.com/lambda/), [*Kubernetes*](https://kubernetes.io/) clusters), enabling repeatable and auditable deployments.

- **Orchestrate** end-to-end pipelines: Deploy complete inference workflows — preprocessing, inference, postprocessing, and verification — using orchestration tools (e.g., [*AWS Step Functions*](https://aws.amazon.com/step-functions/), [*ecFlow*](https://confluence.ecmwf.int/display/ECFLOW)). Version orchestration code alongside application code.

- **Automate** with CI/CD: Automate deployments of validated release candidates with CI/CD tools (e.g., [*GitHub Actions*](https://github.com/features/actions), [*GitLab CI*](https://docs.gitlab.com/ee/ci/), [*Jenkins*](https://www.jenkins.io/)), including logging and approval workflows.

- Deploy **champion** and evaluate **challengers**: Serve champion models to production traffic; optionally deploy challengers via shadow mode or A/B testing to evaluate performance in parallel under real conditions.

- Follow **GitOps** practices: Use [Git](https://git-scm.com/) as the single source of truth for infrastructure, code, and deployment configurations. Drive all changes through pull requests and automate validation and delivery via CI/CD pipelines. This ensures reproducibility, auditability, and safe rollbacks across environments.

## Operate: Run and manage the production system.

- Ensure **availability** and scalability: Use orchestration tools like [*Kubernetes*](https://kubernetes.io/) for autoscaling and load balancing, or job schedulers and resource managers in HPC and batch environments.

- **Log** and monitor system behavior: Centralize logs for infrastructure, inference calls, and runtime exceptions using tools like [*Prometheus*](https://prometheus.io/), [*Loki*](https://grafana.com/oss/loki/), or [*Grafana*](https://grafana.com/).

- Handle **secrets** and **credentials** securely: Use tools like [*HashiCorp Vault*](https://www.vaultproject.io/) to inject secrets at runtime.

- Enforce **access control**: Apply [Role-Based Access Control (RBAC)](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) to define who can deploy, access data, or update models across environments.

- **Service Level Agreements** (SLAs): Define and monitor clear performance, availability, and latency targets to meet business and user expectations.

- Define operational **responsibilities**: Clarify operational responsibilities and communication paths among data scientists, ML engineers, data engineers, and operators to enable rapid incident response, continuous monitoring, and seamless model updates.

## Monitor: Track model performance and behavior over time.

- Detect **data drift**, **prediction skew**, and **performance degradation**: Continuously monitor changes in input data distributions and model outputs. Regularly validate model predictions against ground truth to identify shifts or declines in accuracy.

- **Alert** on anomalies: Set thresholds for key metrics like latency, confidence scores, error rates, and data quality. Automatically trigger notifications (e.g., Slack, email) when anomalies occur.

- **Log** inputs, outputs, and metadata: Record detailed inference data — including input features, predictions, and context metadata — for auditability, debugging, and root cause analyses.

- Implement **feedback** loops: Gather feedback from users and domain experts, and incorporate insights to improve models and data pipelines iteratively.

- Maintain scalable **monitoring infrastructure**: Use robust monitoring and logging stacks ([*Prometheus*](https://prometheus.io/), [*Grafana*](https://grafana.com/), [*ELK* stack](https://www.elastic.co/what-is/elk-stack)). When possible, integrate ML monitoring into existing infrastructure to unify operations, reduce complexity, and optimize maintenance.
