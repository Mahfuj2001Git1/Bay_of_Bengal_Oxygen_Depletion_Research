# Bay of Bengal Oxygen Depletion Research

Code and results from my research on dissolved-oxygen variability and deoxygenation in the Bay of
Bengal oxygen minimum zone (OMZ), 2005–2022, built from two independent gridded oxygen products
(G4D-DOC and GEOXYGEN), validated against BGC-Argo float profiles, and analyzed with a range of
time-series, spatial-statistics, and machine-learning methods.

## What's here

- **`Bay_of_Bengal_Oxygen_Depletion_Research.ipynb`** — the master notebook. Everything runs from
  here: the grid/ensemble pipeline, the 14-analysis deoxygenation study, the yearly-map and
  oxygen-zone-volume outputs, and the driver-attribution modelling. Start with the overview cell at
  the top of the notebook for how it's organised into parts.
- **`bob_local_pipeline/`** — the Python package the pipeline sections of the notebook import
  (config, boundary clipping, regridding, ensembling, the run driver). Also written out inline by
  the notebook's setup cells, so the notebook is self-contained either way.
- **`data/`** — the small inputs the code needs directly (the study-area shapefile, the ONI/DMI
  climate-index CSVs). See `data/README.md` for the large raw products (G4D-DOC, GEOXYGEN,
  GLODAPv3, Argo profiles) this project depends on but doesn't check in.
- **`results/`** — every figure and table the notebook produces, already generated, with
  `results/README.md` mapping each one back to the section that made it.
- **`docs/`** — `BoB_Oxygen_Analysis_Manual.md` (plain-language walkthrough of all 14 core
  analyses), plus standalone write-ups of the Argo validation, the driver dataset, the external
  climate indices, and the 2030/2040/2050 OMZ-core projection.

## Study area and data

The domain is the Bay of Bengal (roughly 5.5–24.5°N), on a 1°×1° grid with 26 depth levels from 10
to 1995 m. The oxygen field is an ensemble of two independent gridded products (G4D-DOC and
GEOXYGEN), simple-averaged after both are clipped to the real coastline polygon (not a bounding
box) and regridded onto the same depth axis. Validated against 322,922 independent BGC-Argo oxygen
readings from 15 floats (2012–2022): **r = 0.958–0.959**, with the tightest agreement precisely in
the 150–900 m OMZ core this project focuses on — full breakdown in
`docs/Ensemble_Argo_Validation_Report.md`.

## Headline results

- The OMZ's basin-wide vertical/seasonal/spatial structure is stable across 2005–2022 — no
  significant trend in basin-wide OMZ volume, area, or thickness.
- That basin-wide average hides a real regional signal: the **Middle Bay of Bengal** sub-region
  shows a statistically significant oxygen decline (Mann-Kendall p = 0.020), projected to reach
  roughly a quarter below its historical mean by 2050 under a Gaussian Process extrapolation — see
  `docs/OMZ_Core_O2_Prediction_Report.md`.
- Depth is overwhelmingly the dominant point-scale control on oxygen (consistent across 7
  independent importance measures: CatBoost/LightGBM/XGBoost + TreeSHAP, Random Forest +
  permutation importance, GAM), followed by temperature; among the climate modes, the Indian Ocean
  Dipole is a materially stronger and more spatially coherent influence than ENSO.
- A cross-product QC check flags growing divergence between the two source oxygen products in the
  final years of the record — a data-quality caveat worth keeping in mind for anyone extending this
  work past 2022.

## Getting started

```
pip install -r requirements.txt
jupyter lab Bay_of_Bengal_Oxygen_Depletion_Research.ipynb
```

Parts A, B, and D need raw data that isn't in this repository (see `data/README.md`) to actually
re-execute — every output they produce is already saved under `results/`, so the full analysis is
reviewable without re-running anything. Part C (the 14-analysis study) runs against the ensemble
product built in Part A.

## License

MIT — see `LICENSE`.
