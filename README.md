# ToyotaCares Exploratory Data Analysis
This repository contains the data science infrastructure for Project: Mind The Gap, a strategic proposal developed for the 2026 Blue Case Competition. The project addresses the service leakage at Toyota Valenzuela, where current retention sits at ~15% against an 80% target.

The toolkit is divided into two primary modules designed to quantify the value of lifecycle-based customer retention.

### Key Modules
1. PMS Pricing Scraper (NLP & Regex)
This module derives a defensible Average Order Value (AOV) by scraping unstructured consumer data from local automotive forums. It is specifically designed to navigate the "20,000 km cliff," where customers frequently defect to independent shops due to price perception.

The "Shield" Logic: A pre-cleaning pass identifies and masks mileage markers (e.g., "20k km") to prevent the scraper from misinterpreting odometer readings as prices.

Negative Lookahead Regex: Utilizes the pattern (?!\s*(?:km|kms|pms)) to extract shorthand currency (e.g., "8k") while rejecting values followed by distance metrics.

Validated Metric: The scraper identified a Median AOV of ₱20,000, which serves as the primary revenue multiplier for the "Transition" customer segment.

2. Monte Carlo ROI Simulator
To move beyond static projections, this module runs 10,000 iterations of the ToyotaCares financial model. It stress-tests the program's viability by treating key variables as probability distributions:


Retention Rate: Modeled as a Normal Distribution (μ=65%,σ=10%), capped at the 15% baseline.

Average Order Value: Modeled as a Normal Distribution (μ=₱16,000,σ=₱3,000) to account for the mix of routine and major maintenance.

OpEx Buffer: A Uniform Distribution (10% to 30%) modeling inflationary cost overruns in CRM automation and member perks.

📊 Simulation Results
The simulation mathematically validates the "Mind The Gap" strategy, demonstrating that the downside risk is negligible compared to lifecycle value capture.

| Metric | Result |
|---|---|
| Median ROI | 940% |
| 90% Confidence Interval | [559%, 1417%] |
| Probability of Positive Return | 100.00% |

The 559% floor (5th percentile) serves as a defensive baseline, proving that even under compounded worst-case assumptions, the program remains significantly more profitable than current transactional tactics.

Installation & Usage
Prerequisites
Python 3.8+

Pandas / NumPy

Matplotlib / Seaborn

Running the Analysis
