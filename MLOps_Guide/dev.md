# DEV

## Plan: Define objectives, data strategy, evaluation protocols, and collaboration frameworks.

- Define Clear **Objectives** and Success Criteria: Align business/scientific goals with measurable metrics and baselines.

- Engage Stakeholders and Clarify **Requirements** and Constraints: Collaborate early with data scientists, domain experts, operations, and users to set requirements, data availability, compute, timelines, and interpretability needs.

- Set **Evaluation** Protocols and Baselines: Define validation methods, datasets, and baseline models for performance context.

- Specify **Data** Strategy: Outline data scope, sources, quality, update frequency, and access methods.

- Establish **Traceability** and Compliance: Track code, data, models, and experiments with tools like *GitHub*, [*DVC*](https://dvc.org), and [*MLflow*](https://mlflow.org) for reproducibility and compliance. Use **Architecture Decision Records (ADRs)** to document key ML decisions — such as model choice, data strategy, or deployment approach — with context and rationale, enabling collaboration and auditability.

- Identify **Risks** and Mitigation Plans: Recognize blockers (data, scalability, performance) and plan fallback strategies.

- Plan Deployment and **Lifecycle**: Define deployment modes (online, batch, edge), monitoring needs, and update/retirement strategies.

- Define **Development** Practices: Minimize technical debt, reuse solutions, maintain compatibility, and foster peer-reviewed workflows within a structured development approach that promotes iterative planning and cross-functional alignment, such as *Kanban* or *SCRUM*, supported by tools like *JIRA*.

- Use **Organizational** Practices: Apply and contribute to existing best practices to align with organizational standards. Leverage organization-wide enabler teams, councils, or communities of practice to assess and refine approaches for broader adoption, supporting scalable and consistent MLOps across teams.

## Code: Develop modular, testable, and version-controlled ML code and pipelines.

- Follow clean code **principles**: Apply [*The Zen of Python*](https://peps.python.org/pep-0020/), KISS ([*Keep It Simple, Stupid*](https://en.wikipedia.org/wiki/KISS_principle)), DRY ([*Don’t Repeat Yourself*](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)), YAGNI ([*You Aren’t Gonna Need It*](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it)), and TDD ([*Test-Driven Development*](https://en.wikipedia.org/wiki/Test-driven_development)) to write readable, maintainable, modular, and testable ML components such as preprocessing, training, evaluation, and inference.

- Use and contribute to **shared standards**: Adopt and enhance organizational ML scaffolds, blueprints, libraries, and coding conventions. Build reusable libraries and use templating tools like [*cookiecutter*](https://cookiecutter.readthedocs.io) to automate and enforce shared standards across teams.

- Manage **configurations** cleanly: Use [*Hydra*](https://hydra.cc) for structured configuration management and [*Pydantic*](https://docs.pydantic.dev) for schema validation and type safety.

- Secure **secrets**: Avoid hardcoding; use environment variables or secret managers, and exclude sensitive files (e.g., `.env`) from version control (e.g., `.gitignore`).

- Track and **version** everything: Use Git, [*MLflow*](https://mlflow.org), and [*DVC*](https://dvc.org) to track code, data, models, and pipelines for reproducibility and traceability.

- **Document** code and workflows: Use docstrings, Markdown, and notebooks to communicate intent and enable collaboration.

- **Visualize*** model behaviour: Integrate tools like *Matplotlib*, *Jupyter Notebooks*, *MLflow UI*, or custom dashboards to explore data, inspect training curves, compare against baselines, and interpret model outputs.

- **Enforce collaboration**:
  Use *GitHub* pull requests and *JIRA* for peer review, issue tracking, and managing technical debt.

- **Automate with pipelines**:
  Use **DVC** or **Snakemake** to structure repeatable workflows from data to model output.


## Build: Prepare the system for execution and deployment.

- Manage **dependencies**: Use tools like *poetry* to pin and manage library versions consistently.

- **Containerize** environments: Build reproducible containers (e.g., *Docker*, *Apptainer*) with fixed OS, library, and base image versions. In HPC or container-restricted environments, use rootless tools like *Kaniko* for secure, Dockerless image creation.

- Use layered container images with a **shared base**: Build from a minimal, organization-wide base image (e.g., a customized `python:3.11-slim`) and layer project-specific dependencies on top. This speeds up builds via caching, improves consistency across projects, and simplifies updates and security patching.

- Use container **registries**: Store and version images in registries like *AWS ECR*, *GitHub Container Registry*, or *Nexus* to enable traceable, auditable builds.

- Run **linting** and **static analysis**: Enforce code quality by integrating tools like *black*, *pylint*, *mypy*, and optionally platforms like *SonarQube* for advanced code inspections, security checks, and maintainability metrics.

- Run **security** and compliance scans: Integrate automated tools (e.g., *Trivy*) and generate Software Bill of Materials (SBOMs) during builds to detect vulnerabilities, insecure dependencies, license issues, and maintain transparent component inventories.

- Integrate with **CI/CD**: Automate builds, tests, linting, static analysis, security scans, and deployments using CI/CD tools (*GitHub Actions*, *GitLab CI*, *Jenkins*). Contribute to portable, reusable scripts that encapsulate the CI and CD workflows, and are decoupled from specific engines or projects.

- **Cache** and reuse artifacts: Use caching strategies to avoid redundant computations in builds or training – such as storing intermediate datasets, preprocessed features, or compiled artifacts.

- **Integrate model** artifacts: Declare the model version in version-controlled code (e.g., config file or pipeline script) and pull it from the model registry during image build time. This enables reproducible, auditable, and **GitOps-compliant** deployments.


## Test: Ensure your ML code, data, and models behave as expected.

- **Unit & integration**: Write unit tests for core components (e.g., preprocessing, metrics) and integration tests to validate end-to-end workflows.
  Use mocking to isolate external dependencies.

- **Data validation**: Test input data and preprocessing pipelines for schema consistency, data quality, drift, leakage, and physical plausibility.

- **Configuration reproducibility**: Verify experiment configurations yield reproducible results. Check artifacts can be reconstructed from logged parameters, data, and code versions.

- **Model evaluation**: Benchmark models against performance thresholds and baselines across regimes, geographies, or forecast lead times. Ensure model artifacts serialize and reload consistently for deployment.

- **CI automation**: Automate all tests in CI pipelines. Monitor regressions, test coverage (e.g., with *pytest-cov*), and make results visible and auditable.
