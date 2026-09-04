# Results

Everything here is a saved output of the master notebook — nothing in this folder was produced by
hand. Regenerating any of it means re-running the corresponding section of
`Bay_of_Bengal_Oxygen_Depletion_Research.ipynb` against the pipeline outputs described in
`../data/README.md`.

## figures/

| File | From |
|---|---|
| `01_longterm_moving_average.png` – `13_ml_cross_product_qc.png` | Analyses 1–13, 14-analysis deoxygenation study |
| `Fig_Seasonal_Vertical_O2_Profiles.png` | Yearly-maps notebook, section 17 |
| `Map1_Surface_Layer_Monthly.png` – `Map6_Layer6_Average.png` | Grid/ensemble notebook, section 11 |
| `Map7_UpperThreeLayers_Yearly.png`, `Map8_LowerThreeLayers_Yearly.png` | Yearly-maps notebook, section 15 |
| `Study_Area_Map_BayOfBengal.png` | Study-area context map |
| `BoB_Oxygen_Research_Design.PNG` | Project research-design diagram |
| `driver_importance_comparison.png` | Driver-attribution notebook |
| `ensemble_argo_validation.png` | See `../docs/Ensemble_Argo_Validation_Report.md` |
| `omz_gp_prediction.png` | See `../docs/OMZ_Core_O2_Prediction_Report.md` |

## tables/

| File | Contents |
|---|---|
| `BoB_Oxygen_Zone_Volumes_Yearly.xlsx` | Yearly oxic/hypoxic/severe-hypoxic/suboxic water-volume breakdown, 2005–2022 (yearly-maps notebook, section 16) |
| `importance_table_normalized.csv`, `spearman_correlation_methods.csv`, `model_fit_summary.csv` | Driver-attribution model outputs (7-method consensus importance ranking) |
| `omz_prediction_summary.csv` | Full basin-wide + 3-region GP projection table behind `OMZ_Core_O2_Prediction_Report.md` |
| `BoB_Argo_Driver_Dataset_v2.parquet` | Argo-derived driver dataset (temperature, salinity, chlorophyll, backscatter matched to ensemble O2) behind the driver-attribution notebook — see `../docs/driver_dataset_notes.md` |
