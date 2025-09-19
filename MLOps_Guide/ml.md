# ML

## Data: Ensure reproducibility and lineage of datasets.

- Apply **preprocessing** steps (normalization, temporal slicing) as part of reproducible pipelines.

- Maintain the original data in its native format for long-term archival and traceability, and **transform** it into datasets — *Zarr* for raster and large datasets, or formats like Parquet or CSV where appropriate — optimized for the specific requirements of your machine learning task.

- Adopt robust data **versioning** practices for all datasets using tools like [Data Version Control (*DVC*)](https://dvc.org), combined with metadata to document changes in data sources, processing steps, and timestamps.

- Store and track **metadata** (e.g., data origin, version, access time, variable list) throughout the ML lifecycle — from training to inference — to ensure the consistency, reproducibility, and traceability of the data used. This enables reliable and auditable predictions in production environments.

- Integrate automatic data **validation** into the ML pipelines to ensure data integrity and scientific reliability. Validate spatial and temporal coverage, units, value ranges, and missing data using tools like [*xarray*](http://xarray.pydata.org) and [*Great Expectations*](https://greatexpectations.io).


### Related E-AI resources:
- Weather and Climate data sources in [E-AI Data Inventory](https://github.com/eumetnet-e-ai/wg1_data_curation/blob/main/gap_analysis/e_ai_data_gap_analyses.md#current-data-inventory)
- [Anemoi Datasets Catalogue](https://anemoi.ecmwf.int/datasets)


## Model: Train, evaluate and register ML models.

- Build and refine ML models through clear, testable **experiments**: Systematically vary model architectures, training parameters, and optimization techniques to evaluate performance and identify the most effective approach. Define hypotheses or performance targets, use fixed evaluation protocols, and vary only one factor at a time to isolate its impact.

- **Log** comprehensive experiment information using tools like [*MLflow*](https://mlflow.org) to support reproducibility, performance analysis, and model management:

  - Reproducibility: Record configurations such as parameters and hyperparameters, input data provenance, environment metadata (e.g., Python environment, ML library versions), and the git commit hash.

  - Performance analysis: Capture model metrics (e.g., accuracy, loss), system metrics (e.g., CPU usage, memory), and visualization artifacts (e.g., plots).

  - Models and checkpoints:
    - Avoid logging full model files or checkpoints by default; instead, log their file paths to conserve storage.
    - Explicitly log models when they are promoted to staging or production environments.

- Use a **Model Registry** — such as MLflow — to register selected models from experiments as part of a central system for cataloging, versioning, and managing ML models throughout their lifecycle. This enables systematic tracking of model versions, metadata, and lineage. The registry also enables controlled promotion of models to staging and production.

- Maintain a **shared repository** of standardized model architectures to facilitate collaboration, promote reuse, and prevent duplication across teams.

### Related E-AI resources:
- Tutorial ([slides](https://github.com/eumetnet-e-ai/tutorials/tree/main/tutorial5) and [record](https://tlnt19059.sharepoint.com/sites/E-AI/_layouts/15/stream.aspx?id=%2Fsites%2FE%2DAI%2FShared%20Documents%2FTutorials%2FE%2DAI%20Tutorial%20Basics%205%20MLOps%2D2025%2D02%2D19%201100%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2E29972ffb%2D2843%2D4759%2Dbe92%2Dfa35d97c06fd)) and workshop on MLflow.
- Neural Network Architectures in [mfai](https://github.com/meteofrance/mfai) and [Anemoi](https://anemoi.readthedocs.io/projects/models/en/latest/).
- Anemoi’s [Experiment Tracking](https://anemoi.ecmwf.int/experiments) and [Model Catalogue](https://anemoi.ecmwf.int/weights).
