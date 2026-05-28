# Orbital Displacement Forecasting: InSAR & Bayesian Time-Series

### 🚨 Mission Objective
To extract millimeter-scale ground deformation signals from satellite radar and use Bayesian time-series modeling to forecast infrastructure pre-failure acceleration.

### 📉 The "Velocity Posterior"
(physics+bayes graph showing the displacement forecast)

### 🛠️ Tech Stack
*   **Engine:** Python 3.10
*   **Data Processing:** Pandas, NumPy
*   **Geodesy:** MintPy, ASF HyP3 SDK (`asf_search`)
*   **Modeling:** PyMC (Bayesian Gaussian Random Walk), ArviZ
*   **Visualization:** Matplotlib

### ⚙️ Engineering Logic
1.  **Geodetic Ingestion:** Queried and submitted 30+ Sentinel-1 SLC radar images to NASA's ASF HyP3 cloud (GAMMA processor) for sub-pixel coregistration and SNAPHU unwrapping.
2.  **Signal Extraction:** Inverted the temporal network (SBAS) via MintPy and sliced the 3D HDF5 data cube to extract 1D displacement time-series (CSV) for highly specific infrastructure targets (e.g., dam abutments).
3.  **Bayesian Forecasting:** Ingested the displacement CSV into a PyMC Gaussian Random Walk model with drift. Extracted posterior predictive distributions to quantify the exact probability of slope acceleration over time.

### 📂 Data Provenance
*   **Primary Source:** ESA Copernicus via NASA Alaska Satellite Facility (ASF)
*   **Region:** Nepal Himalayas (Specific Asset Targets)
*   **Remote Sensing Parameters:** Sentinel-1 Interferometric Wide (IW) Single Look Complex (SLC)
*   **Auxiliary Data:** Copernicus DEM 30m, ERA5 Tropospheric Weather Models
