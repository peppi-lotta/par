# 📊 Population Attributable Risk and Fraction Estimation
This code base provides functions to calculate populational attributinal risk. This project is done as a part of my [thesis work](https://github.com/peppi-lotta/thesis).

This R package provides functions for calculating **Population Attributable Risk (PAR)** and **Population Attributable Fraction (PAF)** from binary exposure and outcome data. It includes both point estimates and confidence intervals via Bayesian and Bootstrap methods, with optional standardization across stratified groups.

---

## Load package 

```
if (!require(par)) {
  devtools::install_github("peppi-lotta/par")
  library(par)
}
```

## 🧪 Example

```r
data <- data.frame(
  exposure = c(1, 0, 1, 0, 1, 0),
  outcome = c(1, 0, 1, 1, 0, 0),
  group = c("A", "A", "B", "B", "A", "B")
)

x <- extract_abcd(data, "exposure", "outcome")
calculate_par(x)
calculate_bayesian_ci("par", x)
calculate_standardized_bayesian_ci(
  type = "par",
  data = data,
  exposure_col = "exposure",
  outcome_col = "outcome",
  standarisation_col = "group",
  interval = 0.95,
  prior = c(1, 1, 1, 1),
  sample_count = 1000
)
```

