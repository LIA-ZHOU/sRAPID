# sRAPID Prognostic Calculator for Pleural Infection

A mobile-friendly research calculator that estimates 3-month mortality and survival probabilities in patients with pleural infection using the sRAPID Cox proportional hazards model described in the accompanying manuscript.

## Online calculator

**https://lia-zhou.github.io/sRAPID/**

## Predictors

The model uses four clinical variables:

- Age (years)
- Blood urea (mmol/L)
- Serum albumin (g/L)
- Infection source: community-acquired or hospital-acquired

Hospital-acquired infection is coded as 1 and community-acquired infection as 0.

## Prediction model

The linear predictor is:

```text
LP = 0.0589289 × Age
   + 0.0405959 × Urea
   − 0.0494406 × Albumin
   + 0.6713133 × Hospital-acquired infection
```

The estimated 3-month survival probability is:

```text
S(3 months | X) = 0.98828133 ^ exp(LP)
```

The estimated 3-month mortality probability is:

```text
Mortality(3 months | X) = 1 − S(3 months | X)
```

The calculator reports estimated 3-month mortality and survival as percentages. It also displays the contribution of each predictor and the total model points.

## Study cohort and model performance

- Patients with complete 3-month follow-up: 1,344
- Deaths within 3 months: 153 (11.4%)
- sRAPID C-statistic: 0.87 (95% CI, 0.84–0.90)
- Internal validation: 1,000 bootstrap resamples
- Bootstrap-corrected C-statistic: 0.87

These values follow the accompanying manuscript and its supplementary material.

## Intended use

The sRAPID model is exploratory and requires independent external validation. This calculator is intended for research and educational evaluation and should not be used as the sole basis for clinical decision-making.
