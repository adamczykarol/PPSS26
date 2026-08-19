# How to Use Jupyter at Athena

**Athena** is the computing cluster at IFJ PAN. Below are step-by-step instructions for launching and using Jupyter notebooks on Athena.

---

## 1. Connect to Athena

Connect via SSH (replace `username` with your Athena login):

```bash
ssh username@athena.ifj.edu.pl
```

If you are connecting from outside the IFJ network, you may need to use the VPN or a jump host — ask your supervisor for details.

---

## 2. Set Up the Environment

Load the required software module or activate the conda/virtualenv environment that contains the analysis dependencies (ROOT, uproot, scikit-learn, etc.):

```bash
# Option A – module system
module load python/3.11
module load root/6.30

# Option B – conda
source /path/to/miniconda3/etc/profile.d/conda.sh
conda activate ppss26
```

If the `ppss26` environment does not yet exist, create it once:

```bash
conda create -n ppss26 python=3.11
conda activate ppss26
pip install jupyterlab uproot awkward numpy pandas matplotlib scikit-learn xgboost scipy
```

---

## 3. Start a Jupyter Server on Athena (no browser on the cluster)

Launch the server **without opening a browser** and bind to a free port (e.g. 8888):

```bash
jupyter lab --no-browser --port=8888 --ip=127.0.0.1
```

Jupyter will print a URL like:

```
http://127.0.0.1:8888/lab?token=<your_token>
```

Copy the token — you will need it in the next step.

---

## 4. Forward the Port to Your Local Machine

Open a **new terminal on your local machine** and create an SSH tunnel:

```bash
ssh -N -L 8888:127.0.0.1:8888 username@athena.ifj.edu.pl
```

---

## 5. Open the Notebook in Your Local Browser

Navigate to the URL printed by Jupyter (Step 3) in your local browser:

```
http://127.0.0.1:8888/lab?token=<your_token>
```

You should see the JupyterLab interface with access to all files on Athena.

---

## 6. Running Long Jobs with tmux / screen

If you plan to run a long training or processing job, start Jupyter inside a `tmux` session so it survives SSH disconnection:

```bash
tmux new -s jupyter
# inside the tmux session:
conda activate ppss26
jupyter lab --no-browser --port=8888 --ip=127.0.0.1
# detach with Ctrl-b d
```

---

## 7. Useful Tips

| Task | Command |
|---|---|
| List running Jupyter servers | `jupyter server list` |
| Stop a server | `jupyter server stop 8888` |
| Check GPU availability | `nvidia-smi` |
| Monitor resource usage | `htop` |

---

## 8. Accessing the Analysis Notebooks

All analysis notebooks for this project live in the `notebooks/` directory of this repository.
After cloning the repository on Athena, open the notebooks from the JupyterLab file browser.

```
PPSS26/
├── docs/                    ← instructions and project description
├── notebooks/
│   ├── 01_eda.ipynb         ← Exploratory Data Analysis
│   ├── 02_bkg_studies.ipynb ← Background Studies
│   ├── 03_bdt.ipynb         ← BDT training to suppress background
│   └── 04_sensitivity.ipynb ← Sensitivity Studies
└── README.md
```
