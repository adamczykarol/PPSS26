# Project Description: Transverse Tau Polarization in Semitauonic B Decays at Belle II

## Overview

This project is a feasibility study to measure the **transverse tau polarization** in semitauonic B meson decays at the [Belle II experiment](https://www.belle2.org/) (KEK, Tsukuba, Japan). It is developed as part of the **IFJ PAN Particle Physics Summer Student (PPSS) Programme 2026**.

---

## Physics Motivation

The Standard Model (SM) of particle physics predicts the polarization of the tau lepton produced in the decay

```
B → D(*) τ ν_τ
```

with high precision. Any deviation from the SM prediction of the transverse polarization **P_T(τ)** would be a clear sign of New Physics beyond the SM, such as contributions from charged Higgs bosons, leptoquarks, or other extensions.

The Belle II experiment, with its high luminosity and clean e⁺e⁻ collision environment, provides a unique opportunity to measure such observables with unprecedented precision.

---

## Observables

The key observable is the **transverse polarization of the tau lepton**:

```
P_T(τ) = (N_+ − N_−) / (N_+ + N_−)
```

where N_+ and N_− are the numbers of tau leptons with positive and negative helicity, respectively.

The polarization is accessed through the **angular distribution** of the tau decay products (e.g., π from τ → π ν).

---

## Analysis Strategy

1. **Event selection** – select B → D(*) τ ν_τ signal candidates using the full-reconstruction (FEI) tag side.
2. **Exploratory Data Analysis (EDA)** – understand the kinematic distributions and identify discriminating variables.
3. **Background suppression** – train a Boosted Decision Tree (BDT) to separate signal from the dominant background contributions (continuum, semileptonic B decays with lighter leptons, etc.).
4. **Template fits** – extract signal yields using fits to BDT output and kinematic distributions.
5. **Sensitivity study** – estimate the expected statistical and systematic uncertainties on P_T(τ) as a function of the Belle II integrated luminosity.

---

## Repository Structure

```
PPSS26/
├── docs/
│   ├── project_description.md    ← this file
│   └── jupyter_at_athena.md      ← how to run Jupyter on the Athena cluster
├── notebooks/
│   ├── 01_eda.ipynb              ← Exploratory Data Analysis
│   ├── 02_bkg_studies.ipynb      ← Background Studies
│   ├── 03_bdt.ipynb              ← BDT training
│   └── 04_sensitivity.ipynb      ← Sensitivity Studies
└── README.md
```

---

## Data

Monte Carlo simulation samples generated with the Belle II software framework (basf2) are used. The samples include:

- **Signal**: B → D(*) τ ν_τ (generic and signal-mode MC)
- **Normalization**: B → D(*) l ν_l (l = e, μ)
- **Background**: generic B⁺B⁻ and B⁰B̄⁰ MC, continuum (qq̄) MC

Access to the samples on the Athena cluster will be provided by your supervisor.

---

## Software Dependencies

| Package | Purpose |
|---|---|
| Python 3.11 | Main language |
| ROOT / uproot | Reading ROOT ntuples |
| awkward-array | Jagged array handling |
| NumPy / pandas | Numerical analysis |
| matplotlib / mplhep | Plotting |
| scikit-learn / XGBoost | BDT training |
| scipy | Statistical tools |

---

## References

- Belle II Collaboration, *The Belle II Physics Book*, [arXiv:1808.10567](https://arxiv.org/abs/1808.10567)
- Tanaka & Watanabe, *New physics in the processes B̄ → D(*)τν̄_τ*, [arXiv:1011.4950](https://arxiv.org/abs/1011.4950)
- Belle Collaboration, *Measurement of the tau lepton polarization and R(D*) in the decay B̄ → D*τν̄_τ*, [arXiv:1709.00129](https://arxiv.org/abs/1709.00129)
