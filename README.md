# Jinnah Barrage Hybrid Flood Prediction System

A basin-aware, multi-source flood prediction and decision-support system for **Jinnah Barrage**, Indus River — built for the AIEF AI Championship.

> Aiming to provide ~20–25 days of early-warning capability by combining hydrological sensors, weather forecasts, satellite remote sensing (Sentinel-1 SAR), and machine learning across the **Upper Indus contributing basin**.

---

## 📍 Study Area

The Area of Interest (AOI) is **not** an arbitrary radius around the barrage — it is the hydrologically correct **upstream contributing basin**, derived via graph traversal:

- Outlet: Jinnah Barrage (`HYBAS_ID 4060685660`)
- Method: Breadth-First Search (BFS) upstream traversal over HydroBASINS `NEXT_DOWN` connectivity
- Result: **41 Level-6 sub-basins** (Level-7 / Level-8 refinements also delineated)
- Verified hydrologically complete via a HydroRIVERS network diagnostic (18,823 segments, 0 truncated)

## 🧩 Module Status

| Module | Description | Status |
|---|---|---|
| 1B | Upstream AOI delineation (BFS over HydroBASINS) | ✅ Complete |
| 2D | Named-river classification via verified confluence coordinates | ✅ Complete |
| 2E | Sentinel-1 SAR (VV/VH) backscatter extraction per river, 2015–2025 | ✅ Complete |
| 3A | HydroRIVERS network diagnostic / completeness check | ✅ Complete |
| 3B | Named-river anchor point identification | 🔄 In progress |
| — | Basin-wise IMERG rainfall + SMAP soil moisture extraction | 🔜 Next |
| — | Unified multi-source training dataset | 🔜 Planned |
| — | Model training (baselines → sequence models → fusion) | 🔜 Planned |
| — | GIS decision-support dashboard | 🔜 Planned |

## 🛰️ Data Sources

- **HydroSHEDS / HydroBASINS / HydroRIVERS** — basin polygons & river network topology
- **Sentinel-1 GRD (SAR)** — cloud-independent surface water / flood signal
- **GPM IMERG** — satellite rainfall
- **SMAP** — soil moisture
- **OSM waterways** — named-river attribution (cross-check)
- **WAPDA / IRSA** — hydrological gauge records (requested)

## 📁 Repository Structure

```
gee-scripts/     GEE JavaScript code, one file per module
notebooks/       Python notebooks (data processing, EDA, modeling)
data/sample/     Small CSV samples (full datasets hosted externally)
docs/images/     Maps, plots, and screenshots proving current progress
docs/            Methodology notes
```

## 🧪 Current Results (Module 2E)

~150,000 daily VV/VH backscatter observations extracted across 11 river groups (2015–2025) — see `docs/images/` for sample plots and `data/sample/` for a preview of the extracted CSV.

## 🛠️ Tech Stack

Google Earth Engine · Python (GeoPandas, NetworkX, scikit-learn, XGBoost, PyTorch) · QGIS

## 👥 Team

<!-- Add team member names and roles here -->

## 📄 License

<!-- Add license, e.g. MIT -->
