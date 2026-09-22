# Long-Range Interdependencies Aware Signal Analysis (LRIA)

Official implementation of the paper:

**Long-Range Interdependencies Aware Signal Analysis for Rapid and Accurate Obstructive Sleep Apnea Prediction**

Published in **Nature Communications (2026)**.

📄 **Paper:** https://doi.org/10.1038/s41467-026-76274-0

LRIA is a signal-analysis framework designed to capture long-range interdependencies in physiological signals. The framework extracts fractional-dynamics-based coupling representations from multichannel polysomnography (PSG) signals and integrates them with deep learning models for obstructive sleep apnea (OSA) prediction.

---

## Repository Structure

```text
.
├── LRIA/                       # MATLAB implementation of LRIA
├── Figures/                    # Figures and visualization results
├── dataprocess.ipynb           # SHHS preprocessing and feature generation
├── train_transformer.ipynb     # Baseline Transformer/Informer training
├── train_twotower.ipynb        # LRIA Two-Tower Transformer training
└── plot.ipynb                  # Result visualization
```

---

## Dataset and Sample Data

### Sample Data

A small subset of the SHHS dataset used for testing the preprocessing and LRIA pipelines is available here:

**Google Drive:**  
https://drive.google.com/drive/folders/1-JiQKihFVLfssGcDizrpFCd1lpB_VfeD?usp=sharing

The sample package contains:

- `visit_1/` — sample raw SHHS Visit 1 recordings for subjects `77`, `81`, `82`, `83`, and `84`.
- `shhs1_ahi_pruebas.xlsx` — AHI information used to generate OSA severity labels.

The sample data are intended primarily for verifying the preprocessing and feature-extraction pipeline.

### Full Datasets

The full datasets used in the paper are available from their original repositories. Access may require registration, a data-use agreement, or approval from the corresponding data provider.

| Dataset | Repository | Download / Access |
|---|---|---|
| **SHHS (Sleep Heart Health Study)** | National Sleep Research Resource (NSRR) | https://sleepdata.org/datasets/shhs |
| **MESA (Multi-Ethnic Study of Atherosclerosis)** | National Sleep Research Resource (NSRR) | https://sleepdata.org/datasets/mesa |
| **MrOS (Osteoporotic Fractures in Men Study)** | National Sleep Research Resource (NSRR) | https://sleepdata.org/datasets/mros |
| **West Romania cohort** | Restricted clinical dataset | Available upon request for non-commercial academic research; see the paper for access details |

For reproducing the **SHHS experiments** provided in this repository, please download the **SHHS Visit 1** polysomnography recordings and corresponding metadata from NSRR.

> **Note:** We do not redistribute the complete PSG datasets in this repository. Please follow the access requirements, licenses, and data-use policies of the corresponding data providers.

---

## LRIA Feature Extraction

The `LRIA/` directory contains the MATLAB implementation of the **Long-Range Interdependencies Aware (LRIA)** signal analysis framework.

LRIA models multichannel physiological signals using fractional dynamics and estimates a coupling matrix that captures long-range interdependencies among physiological processes.

The resulting coupling matrices can be used either:

1. directly as compact input features for a neural network; or
2. together with raw physiological signals in the Two-Tower Transformer architecture.

Please refer to the **Methods** section of the paper for the mathematical formulation and estimation procedure.

---

## SHHS Data Processing and Model Training

### Environment

The experiments were developed using:

```text
Python 3.8.10
MATLAB
```

Additional Python dependencies can be installed according to the imports specified in the provided notebooks.

### 1. Data Preprocessing 

Run:

```text
dataprocess.ipynb
```

This notebook processes the raw SHHS recordings, extracts the selected physiological channels, generates model inputs, and constructs the OSA severity labels.

The SHHS experiments use five physiological signals:

- SpO2
- Heart Rate
- Thoracic Respiratory Effort
- Abdominal Respiratory Effort
- Airflow

The recordings are divided into **10-minute windows** for model training and evaluation.

### 2. Baseline Transformer

Run:

```text
train_transformer.ipynb
```

This notebook implements the baseline Transformer model.

### 3. LRIA Two-Tower Transformer

Run:

```text
train_twotower.ipynb
```

This notebook implements the proposed **LRIA-based Two-Tower Transformer**.

> **Computational Cost:** Training on the full SHHS dataset takes approximately **4–5 hours per epoch** for both the baseline and Two-Tower models under our experimental setup. Actual runtime may vary depending on hardware and preprocessing configuration.

---

## Results and Visualization

The `Figures/` directory contains figures generated from the experiments reported in the paper.

Run:

```text
plot.ipynb
```

to reproduce the corresponding result visualizations.

---

## Citation

If you find this repository or LRIA useful in your research, please cite:

```bibtex
@article{wang2026lria,
  title   = {Long-range interdependencies aware signal analysis for rapid and accurate obstructive sleep apnea prediction},
  author  = {Wang, Zhenkun and Yin, Chenzhong and Cheng, Anzhe and others},
  journal = {Nature Communications},
  year    = {2026},
  doi     = {10.1038/s41467-026-76274-0}
}
```

---

## Data Availability

The **SHHS**, **MESA**, and **MrOS** datasets are available through the [National Sleep Research Resource (NSRR)](https://sleepdata.org/).

The **Human Sleep Project** dataset is available through the [Brain Data Science Platform (BDSP)](https://bdsp.io/).

The **West Romania clinical dataset** is available under restricted access because the participant consent and institutional ethics agreements do not permit unrestricted public redistribution. Access may be requested for non-commercial academic research purposes. Please refer to the **Data Availability** section of the paper for the detailed access procedure.

---

## License

Please refer to the repository license for terms governing use of the source code.

The external datasets are subject to their respective licenses, data-use agreements, and access policies.
