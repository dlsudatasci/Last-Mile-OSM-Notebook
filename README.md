Environment Setup
1. Create a Python environment.

Using Conda:

conda create -n manila_osm python=3.12
conda activate manila_osm

Or using venv:

python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS/Linux
source .venv/bin/activate

2. Install the required packages.

pip install -r requirements.txt

3. Select the environment as the Jupyter kernel in VS Code before running the notebooks.