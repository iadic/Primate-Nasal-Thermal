# Instructions to Replicate the Virtual Environment

## Option 1: Using `.yml` file (Conda environment)

1. Open the project folder in VS Code (Visual studio Code).
2. Open a new terminal in VS Code.
3. Create a new environment from the `.yml` file:

```bash
conda env create -f environment.yml -n newenv_test
```

- `-f environment.yml` → specifies the environment file.  
- `-n newenv_test` → sets the name of the new environment (you can choose any name).

4. Activate the environment:

```bash
conda activate newenv_test
```

5. Select the environment in VS Code:
   - Click the kernel selector in the top-right corner of your notebook or Python file.
   - Choose `Python (newenv_test)`.

6. If the environment doesn’t appear in the kernel list, register it with Jupyter:

```bash
conda install ipykernel -c conda-forge
python -m ipykernel install --user --name=newenv_test --display-name "Python (newenv_test)"
```

- This adds the environment to VS Code and Jupyter kernels.

7. Run the code cells 

---

## Option 2: Using `requirements.txt` (pip environment, only Python packages)

1. Open the project folder in VS Code.
2. Open a new terminal in VS Code.
3. Create a new virtual environment:

```bash
python3 -m venv newenv_test
```

4. Activate the environment:

```bash
source newenv_test/bin/activate
```

5. Install dependencies from `requirements.txt`:

```bash
pip install -r requirements.txt
```

6. Select the environment in VS Code:
   - Click the kernel selector and choose the Python interpreter from `newenv_test`.

7. Run the code cells.

---

## Notes

- Use **Option 1** if you need full reproducibility, including Python version and non-Python dependencies.  
- Use **Option 2** if you only need Python packages.  
- The terminal commands written are for macOS and may differ for other operating systems