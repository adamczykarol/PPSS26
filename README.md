# PPSS26

Feasibility study to measure transverse tau polarization in semitauonic B decays at the Belle II experiment.  
Developed for the **IFJ PAN Particle Physics Summer Student (PPSS) Programme 2026**.

---

## Repository Structure

```
PPSS26/
├── docs/
│   ├── project_description.md    ← detailed physics and analysis description
│   └── jupyter_at_athena.md      ← how to run Jupyter on the Athena cluster
├── notebooks/
│   ├── 01_eda.ipynb              ← Exploratory Data Analysis
│   ├── 02_bkg_studies.ipynb      ← Background Studies
│   ├── 03_bdt.ipynb              ← BDT training for background suppression
│   └── 04_sensitivity.ipynb      ← Sensitivity Studies
└── README.md
```

## Getting Started

1. Read the [project description](docs/project_description.md) to understand the physics goals and analysis strategy.
2. Follow the [Jupyter at Athena](docs/jupyter_at_athena.md) guide to set up your computing environment.
3. Work through the notebooks in order:
   - **01_eda.ipynb** – explore kinematic distributions and identify discriminating variables
   - **02_bkg_studies.ipynb** – characterise background contributions
   - **03_bdt.ipynb** – train a BDT classifier to suppress background
   - **04_sensitivity.ipynb** – estimate the expected sensitivity to P_T(τ)
