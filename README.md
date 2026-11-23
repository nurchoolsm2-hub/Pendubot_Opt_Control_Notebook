# Pendubot optimal control — standalone Jupyter notebook

Open **[Pendubot_DDP_iLQR_Tutorial.ipynb](Pendubot_DDP_iLQR_Tutorial.ipynb)** for an executable explanation of Pendubot swing-up and stabilization. All model and controller code is inside the notebook. No dashboard, external Python modules, previous repository, or data downloads are needed.

The notebook covers coordinates and an illustration; energy and Euler–Lagrange derivation; the mass matrix, velocity coupling, and gravity; the continuous-time state model and RK4; the quadratic objective; discrete Hamiltonian derivatives; full DDP versus iLQR; regularized backward recursion; forward line search; convergence plots; trajectory feedback; upright LQR; and inline animation. Each part includes concise equations, code, and interpretation.

## Run on Ubuntu

Install Python 3.12 or newer, with virtual-environment support. After cloning this private repository while signed into GitHub:

```bash
git clone https://github.com/nurchoolsm2-hub/Pendubot_Opt_Control_Notebook.git
cd Pendubot_Opt_Control_Notebook
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m jupyterlab Pendubot_DDP_iLQR_Tutorial.ipynb
```

If Ubuntu reports that `venv` is unavailable, install the matching Python virtual-environment package first (for the system Python, usually `sudo apt install python3-venv`).

## Run on Windows

In PowerShell, from the repository folder:

```powershell
py -3 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m jupyterlab Pendubot_DDP_iLQR_Tutorial.ipynb
```

These commands do not require activating a PowerShell script. Use Python 3.12 or newer.

## Use the notebook

1. Select the installed Python environment as the notebook kernel.
2. Choose **Kernel → Restart Kernel and Run All Cells**. Allow a few minutes for the first JAX compilation and animation generation; no GPU is needed.
3. Edit masses, link lengths, timing, cost weights, or iteration limits in **Section 2**. Then rerun from that section onward. The notebook shows exactly where to put `replace(cfg, ...)`.

Saved outputs show an executed reference run; rerunning computes new results. GitHub renders the explanatory text and static plots, while the animation runs in Jupyter after execution. The notebook uses unwrapped angles in the objective and wrapped angle errors for physical reporting. It distinguishes optimizer convergence from reaching and holding the goal. Torque is unconstrained and joints are frictionless.

Only the teaching notebook and small setup/documentation files are included. The original dashboard project is not required.

The saved notebook was executed from a fresh kernel: all 18 code cells completed without errors. Both methods converged to approximately `J = 5.17531`, and both trajectory-feedback experiments passed the arrival and five-second hold checks. The reference environment used Python 3.14.7, JAX 0.12.0.1, NumPy 2.5.4, SciPy 1.18.1, and Matplotlib 3.11.2; results and timing may vary with versions and settings.
