# Analysis of Online Store Sales

An exploratory e-commerce analytics project using Python to examine sales patterns across product categories, countries and continents, devices, traffic channels, and customer/session attributes. The analysis combines descriptive statistics, visual exploration, correlations, and selected statistical tests. An interactive dashboard is published on Tableau Public.

## Interactive dashboard

[**View the dashboard on Tableau Public**](https://public.tableau.com/app/profile/maciej.klysiak/viz/portfolio1_17858847075260/Dashboard1?publish=yes)

## Objectives

The project explores questions such as:

- Which countries, continents, and product categories contribute most to recorded sales value?
- How does sales value vary over time?
- How are sales distributed across devices and traffic channels?
- How do sales-related metrics differ between selected user/session groups, such as newsletter or email-verification status?
- What relationships are visible between daily session volume and daily sales?

These are exploratory questions. Observational patterns and statistical associations should not be interpreted as proof of causation.

## Tools and methods

- **Python** — analysis workflow
- **Pandas and NumPy** — data preparation, grouping, and calculations
- **Matplotlib and Seaborn** — static visualisations
- **Plotly Express** — interactive charts in the notebook
- **SciPy** — selected statistical tests and correlation calculations
- **Tableau Public** — interactive dashboard presentation

## Analysis overview

The notebook includes analysis of:

- Sales value by geography and product category
- Sales mix by device type and traffic channel
- Weekly and daily sales trends
- Differences across selected user/session attributes
- Relationships between sales and session activity
- Exploratory statistical tests for selected categorical and numeric comparisons

## Repository contents

- `Analysis of Online Store Sales.ipynb` — analysis notebook
- The dashboard is available via the Tableau Public link above.

## Dataset and reproducibility

The raw CSV dataset is **not included** in this repository. The notebook currently loads the file from a Google Drive location in a Google Colab-specific cell, so a fresh download of this repository will not run end-to-end until the data file is made available and the input path is configured.

The notebook expects fields including `order_date`, `session_id`, `price`, `continent`, `country`, `device`, `traffic_channel`, `product_category`, `browser`, `registered_user_id`, `is_email_confirmed`, and `is_newsletter_subscribed`.

To reproduce the analysis:

1. Obtain the source CSV and confirm that its licence permits your intended use.
2. Make the CSV available in Google Colab or change the loading cell to a path that works in your environment.
3. Install the notebook's dependencies: `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`, and `scipy`.
4. Run the notebook from top to bottom and check that the outputs are regenerated successfully.
5. If you export cleaned data for Tableau, verify the output path and ensure that the exported data uses the same metric definitions as the notebook.

## Important metric and interpretation notes

- **Confirm the data grain before counting orders.** Some aggregations count non-null `price` rows, while others use `session_id`. A row, a session, and an order are not necessarily the same thing. Validate the available identifiers before labelling a count as “number of orders” or calculating average order value.
- **Define conversion at the session level.** A row-level flag based on whether `price` is non-null may not accurately represent whether a session converted. Define conversion using a verified purchase/order signal and aggregate consistently at the session level.
- **Use a consistent currency.** Confirm the currency represented by `price` and use it consistently across chart labels and narrative text. Do not infer currency from a column name or a chart label.
- **Avoid causal claims from correlation.** A correlation between traffic and sales indicates association, not a guarantee that increasing traffic or advertising spend will increase revenue or return on investment.
- **Treat statistical tests as evidence, not proof.** Report group sizes and useful effect-size summaries alongside p-values, check test assumptions, and avoid interpreting a non-significant result as proof that groups are identical.
- **Validate time-based comparisons.** Grouping by day of month can combine different months and hide differences in month length. Check missing dates and consider weekday, month, and seasonality effects before making recommendations.

## Suggested next steps

- Make the data-loading step portable and document the source and licence.
- Audit row-level, session-level, and order-level definitions before recalculating KPIs.
- Re-run every notebook cell after the metric changes and update the Tableau dashboard if the results change.
- Replace causal wording with evidence-based conclusions and clearly labelled hypotheses.
- Add a short executive summary describing the strongest validated findings and their business implications.

## Author

Created as a data analytics portfolio project by [MaciejK-ops](https://github.com/MaciejK-ops).
