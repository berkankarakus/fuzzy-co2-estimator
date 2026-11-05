# Fuzzy CO₂ Estimation System

A small, visual introduction to **fuzzy inference** with Python. The included
Jupyter notebook estimates a CO₂ percentage from temperature and pressure using
interpretable membership functions and a rule-based model.

> This is an educational example intended to demonstrate fuzzy-logic concepts;
> it is not calibrated for real-world environmental control or safety-critical
> decisions.

## What it demonstrates

- Fuzzification of temperature and pressure inputs
- Triangular membership functions
- A 25-rule fuzzy rule base
- Aggregation of output membership functions
- Bisector defuzzification to produce a crisp CO₂ estimate
- Plots for the input, output, and final defuzzified result

## Model overview

| Variable | Range | Linguistic labels |
| --- | --- | --- |
| Temperature | 7–16 | Very Cold, Cold, Normal, High, Very High |
| Pressure | 1.75–4.00 | Very Low, Low, Normal, Good, Very Good |
| CO₂ output | 2–6 | Very Bad, Bad, Normal, Good, Very Good |

The notebook draws a temperature and a pressure value, calculates their degree
of membership in each fuzzy set, evaluates the rule base, and converts the
aggregated output set into one CO₂ percentage.

## Getting started

### Prerequisites

- Python 3.8 or later
- Jupyter Notebook or JupyterLab

### Install dependencies

```bash
python -m pip install --upgrade scikit-fuzzy numpy matplotlib jupyter
```

### Run the notebook

```bash
jupyter notebook fuzzy_co2_estimation.ipynb
```

Run the cells in order. The notebook prints the sampled input values and the
defuzzified CO₂ estimate, while also rendering the membership and result plots.

## Repository structure

```text
.
├── fuzzy_co2_estimation.ipynb  # Model, rule base, visualizations, and result
└── README.md                 # Project documentation
```

## How the inference works

1. **Fuzzify** the temperature and pressure values with triangular membership
   functions.
2. **Evaluate** each rule with the minimum (`AND`) operator.
3. **Apply** the rule strengths to the corresponding CO₂ output sets.
4. **Aggregate** the activated output sets with the maximum (`OR`) operator.
5. **Defuzzify** the combined set with the bisector method to obtain one crisp
   CO₂ estimate.

## Inspiration

The notebook adapts the ideas from scikit-fuzzy’s
[tipping-problem example](https://pythonhosted.org/scikit-fuzzy/auto_examples/plot_tipping_problem.html).
