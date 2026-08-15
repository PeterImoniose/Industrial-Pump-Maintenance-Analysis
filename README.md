# Industrial Pump Maintenance Analysis

A statistical and machine learning investigation into whether sensor readings from a large
industrial pump dataset (temperature, vibration, pressure, flow rate, RPM, and operational
hours across multiple pumps) can predict whether maintenance is required.

## What's in this repo

- [`large_industrial_pump_analysis.ipynb`](large_industrial%20pump%20analysis.ipynb) - the full
  analysis, from data exploration through statistical testing to model comparison.
- [`Industrial_Pump_Dashboard.html`](Industrial_Pump_Dashboard.html) - a standalone, self-contained
  Chart.js dashboard summarising the dataset (open it directly in a browser, no server needed).
- [`Industrial Pump .pptx`](Industrial%20Pump%20.pptx) - a slide summary of the findings.

## Methodology

1. **Exploratory analysis** - missing-value check, class balance (maintenance vs. no
   maintenance, both overall and per pump), and a correlation heatmap across all sensor
   readings.
2. **Statistical significance testing** - independent t-tests plus Cohen's d effect size for
   every sensor feature, comparing the maintenance group against the no-maintenance group.
3. **Feature engineering** - a weighted composite Risk Score built from the standardised
   sensor readings, binned into Low/Medium/High/Critical risk categories.
4. **Lifecycle analysis** - maintenance rate broken down by operational-hours bin, to check for
   an age-related degradation pattern.
5. **Machine learning** - Logistic Regression, Random Forest, and Gradient Boosting classifiers,
   each evaluated on a held-out test split (accuracy, ROC-AUC, F1) and with 5-fold stratified
   cross-validation, plus feature importance rankings for every model.

## Finding

Every one of these methods points to the same honest conclusion: in this dataset, none of the
recorded sensor readings show a statistically or practically meaningful relationship with the
maintenance flag. Effect sizes were negligible (Cohen's d), every feature's correlation with
the maintenance flag was under 0.015, the risk-score categories all showed maintenance rates
within a few points of 50%, and all three models performed at roughly the baseline rate you'd
expect from random guessing on a balanced dataset.

Rather than force a model to "find" a pattern that isn't statistically there, the analysis
reports that negative result directly - the value of the statistical testing step is exactly
this: catching, before deployment, that a dataset doesn't support the predictive claim it might
otherwise be used to justify.

## Author

Avwerosuo Peter Imoniose
