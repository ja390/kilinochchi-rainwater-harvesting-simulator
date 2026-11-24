# Data inventory and credits

## Source

Rainfall input is obtained from the [NASA POWER Daily API](https://power.larc.nasa.gov/docs/services/api/temporal/daily/) using precipitation parameter `PRECTOTCORR` for 9.38° N, 80.40° E, over 2015–2024. NASA POWER provides gridded estimates rather than household gauge observations. The notebook records the query and can retrieve the source data when run online.

## Files in this directory

- `kilinochchi_rainfall_calibration.csv` — monthly production-fit occurrence and shifted-gamma parameters.
- `rainfall_validation_heldout.csv` — held-out rainfall validation summary.
- `calibrated_capacity_results.csv` — capacity sweep with mean reliability and confidence interval.
- `sensitivity_calibrated.csv` and `combined_scenarios.csv` — scenario experiment summaries.
- `mc_error_scaling.csv` — empirical standard-error scaling results.
- `web_demo_reference_result.csv` — fixed water-balance benchmark values used by the browser check.

These are generated project outputs, not raw NASA daily observations. Re-run the notebook to regenerate them before relying on the values. Cite NASA POWER when reusing rainfall-derived results, and consult NASA's current data-use guidance before redistributing any downloaded source data.
