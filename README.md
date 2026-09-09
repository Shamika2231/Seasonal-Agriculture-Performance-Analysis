**🌾 Seasonal Agriculture Performance Analysis**

A data analytics project investigating how agricultural performance — yield, profit, resource use, and risk — varies across India's three growing seasons: Kharif, Rabi, and Zaid.

Note: This is a pure data analytics project. No machine learning model or dashboard is built — every conclusion is derived through exploration, statistics, and visualization.

📌 Problem Statement

Agricultural activities are shaped by seasonal shifts in environmental conditions, farming practices, resource availability, and market conditions, so performance is unlikely to look the same in every season. On its own, raw data doesn't explain how performance shifts across seasons or what drives that shift. This project analyzes a seasonal agriculture dataset to surface those patterns with evidence rather than assumption.

🎯 Objectives
Understand the structure and quality of the dataset before drawing conclusions.
Clean and prepare the data so seasonal comparisons aren't distorted by missing or bad values.
Explore how environmental, resource, yield, economic, and risk variables differ across seasons.
Move from univariate → bivariate → multivariate analysis.
Quantify relationships between variables using correlation analysis.
Statistically test whether observed seasonal differences are real or just noise.
Turn findings into concrete, evidence-based recommendations.
📂 Dataset

File: seasonal_agriculture_performance_dataset.csv

Farm-level agricultural records spanning multiple seasons, states, and crops — covering environmental conditions, farming inputs, yield, production, and financial outcomes for each farm.

🛠️ Tools & Libraries
Python
Pandas, NumPy
Matplotlib, Seaborn
SciPy (statistical tests)

🧭 Analysis Workflow
Loading & First Look — shape, head/tail, random sample, column overview
Data Types & Structure — df.info(), categorical value inspection
Missing Value Treatment — imputed using the median within each (Season, Crop) subgroup rather than a single global median, to avoid flattening real seasonal differences in rainfall, soil moisture, and yield
Duplicate Records — checked for full-row and Farm_ID duplicates
Statistical Analysis — descriptive stats (including range & IQR) overall and by season
Outlier Analysis — IQR rule used to flag (not blindly remove) extreme values; each flagged column reasoned about individually (e.g. right-skewed profit/production treated as legitimate, Soil_pH checked against physically plausible bounds)
Univariate Analysis — pie chart, count plot, histograms with KDE
Bivariate Analysis — box, violin, scatter, bar, and point plots relating season to key outcomes
Multivariate Analysis — pair plot across environmental and performance metrics, colored by season
Correlation Analysis — heatmap of numeric variables, ranked correlations with yield
Seasonal Comparison Summary — consolidated season-level averages table
Custom Analyses:
One-way ANOVA across key metrics to separate statistically real seasonal differences from visual noise, followed by Tukey HSD pairwise comparison on profit
Water efficiency by irrigation method within each season
Disease/pest risk by state × season (regional vs. seasonal effect)
Key Insights, Limitations, and Conclusion & Recommendations
🔑 Key Insights
Kharif has the highest observed average yield (5.63 t/ha) and Zaid the lowest (4.64 t/ha), but this gap is not statistically significant (ANOVA p = 0.23) — within-season variability outweighs the seasonal gap.
Profit differs significantly across every season pair (Tukey HSD, p < 0.001): Kharif ≈ ₹178,915, Rabi ≈ ₹87,689, Zaid averages a loss of ₹−24,805.
Since yield isn't significantly seasonal but profit is, Zaid's losses are an economics problem, not a productivity problem.
Rainfall, temperature, humidity, and disease/pest risk are all statistically significant across seasons (p < 0.001) — these are what actually define "seasonality" here.
Kharif carries the highest average disease/pest risk, consistent with being the wettest, most humid season.
Profit shows the strongest correlation with yield (r ≈ 0.49) of any variable tested.
Flood irrigation is the most common method, but the most water-efficient method varies by season — a single blanket irrigation recommendation wouldn't hold.
Punjab has the highest average yield (6.12 t/ha); Andhra Pradesh the lowest (4.63 t/ha) — a regional gap larger than any seasonal one.
Outliers concentrate in profit, production, and water-efficiency columns, consistent with a small number of very large/efficient farms rather than data errors.
No missing values or duplicates remained after cleaning, so conclusions aren't distorted by incomplete records.
✅ Conclusion

Season is a statistically confirmed driver of some aspects of agricultural performance — but not all of them, and that distinction is the central finding. Environmental conditions, disease/pest risk, and profit all shift significantly across Kharif, Rabi, and Zaid. Yield does not — the seasonal yield gap is smaller than natural within-season variability. This means Zaid's poor profitability is best explained by market price and cost conditions, not lower production.

💡 Recommendations
Treat Zaid's low profitability as a market/cost problem, not a yield problem — target pricing, market access, and input costs.
Time disease/pest advisories ahead of Kharif, which carries the highest confirmed seasonal risk.
Avoid a single blanket irrigation recommendation — water efficiency by method is season-dependent.
Prioritize agronomic and market support for consistently lower-yielding states (e.g. Andhra Pradesh) over blanket seasonal interventions.
Extend the study with multi-year data before treating the non-significant yield result as final.

Author: Shamika 
