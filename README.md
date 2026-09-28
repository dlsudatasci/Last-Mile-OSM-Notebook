# Last-Mile-OSM-Notebook

OSM data collection, preprocessing, and node feature engineering for the Metro Manila road network.

## Project Structure

```text
Last-Mile-OSM-Notebook/
├── notebooks/
│   ├── 01-OSM Data Collection and Preprocessing.ipynb
│   └── 02-Node Feature Engineering.ipynb
├── config/
│   ├── amenities.py
│   ├── buildings.py
│   ├── shops.py
│   └── poi_feature_map.xlsx
├── .gitignore
└── README.md
└── requirements.txt
```

### Notebooks

* `01-OSM Data Collection and Preprocessing.ipynb` — downloads and preprocesses the Metro Manila road network and points of interest (POIs).
* `02-Node Feature Engineering.ipynb` — generates semantic node features from nearby POIs for graph-based analysis.


## Environment Setup

Create and activate a Python virtual environment.

### Windows

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Install the required packages:

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Register the environment as a Jupyter kernel:

```powershell
python -m ipykernel install --user --name last-mile-osm --display-name "Python (Last-Mile OSM)"
```

In VS Code, select the `Python (Last-Mile OSM)` kernel before running the notebooks.

## Workflow

Run the notebooks in order.

### 1. Data Collection and Preprocessing

Open:

```text
notebooks/01-OSM Data Collection and Preprocessing.ipynb
```

This notebook:

* Downloads the Metro Manila road network from OpenStreetMap.
* Downloads amenities, buildings, and shops.
* Removes duplicate OSM features.
* Simplifies and consolidates the road network.
* Converts datasets to a common projected CRS.
* Exports the processed datasets.

Generated files are saved under:

```text
data/osm/graphs/
data/osm/geojson/
```

### 2. Node Feature Engineering

After Notebook 1 completes, open:

```text
notebooks/02-Node Feature Engineering.ipynb
```

This notebook:

* Loads the processed road nodes and POIs.
* Applies the mappings in `config/poi_feature_map.xlsx`.
* Converts polygon POIs to centroid points.
* Counts nearby POIs within a 100-meter radius.
* Creates semantic node features.

Generated files are saved under:

```text
data/features/
```

Expected outputs include:

```text
data/features/road_nodes_with_features.geojson
data/features/road_node_features.csv
```

## Configuration

The notebooks use:

```python
PROJECT_ROOT = Path.cwd().parent
```

This assumes the notebooks are run with the `notebooks` directory as the working directory.

Study area and OSM categories can be modified through:

```text
config/amenities.py
config/buildings.py
config/shops.py
config/poi_feature_map.xlsx
```

## Data

Raw and generated datasets are excluded from Git because they can be large and can be reproduced by running the notebooks.

The following directories are generated locally:

```text
data/osm/
data/features/
```

## Notes

* OSM data is retrieved from OpenStreetMap and may change over time.
* Data downloads may take several minutes.
* The notebooks use EPSG:32651 for metric spatial operations.
