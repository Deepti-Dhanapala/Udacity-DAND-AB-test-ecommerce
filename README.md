# E-commerce Landing Page A/B Test – My Analysis

This project analyzes a public e-commerce A/B test where a company tested a new landing page against the old one.  
The goal is to understand whether the new page improves conversion and how confident we can be in that conclusion.

## What I did

- Loaded the experiment data (`ab_data.csv`) into Python using pandas.
- Cleaned the dataset to keep only valid assignments:
  - control users on the `old_page`
  - treatment users on the `new_page`
- Defined conversion as a 0/1 flag (`converted`) and computed:
  - conversion rate for the control group
  - conversion rate for the treatment group
  - the lift (difference in conversion rates)
- Ran a two-sample proportion z-test using `statsmodels` to check if the difference is statistically significant.
- Interpreted the p-value (~0.19) in plain English:
  - If there were truly no difference between pages, there is about a 19% chance of seeing a difference this large just due to random variation.
- Concluded that the new page does **not** show a statistically significant improvement in conversion and would **not** recommend rolling it out as a clear upgrade based on this test alone.
- Added a simple bar chart of conversion by group to visualize how similar the two conversion rates are.

## Causal Interpretation

Because this was designed as a randomized A/B test, assignment to control and treatment is intended to be random.  
This strongly reduces selection bias and makes the two groups comparable on average. Under these assumptions, the difference in conversion rates can be interpreted as a causal effect of the new page.  
Given that the estimated lift is very small and not statistically significant, we do not have strong evidence that the new page causally improves conversion.

## Files in this repository

- `ab_data.csv` – public A/B test dataset provided by Udacity.
- `my_analysis.ipynb` – my notebook with data cleaning, analysis, statistical test, plots, and conclusions.
- (Optional) Other original Udacity files are kept for reference in their own folder.

## Tech stack

- **Language:** Python 3  
- **Libraries:** pandas, matplotlib, statsmodels

