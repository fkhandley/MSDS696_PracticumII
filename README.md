# MSDS696_PracticumII: Price Elasticity Analysis Tool

## Overview
This project offers a comprehensive analytics tool for retail price optimization through elasticity analysis. By analyzing the relationship between price changes and sales volumes across multiple dimensions (product categories, locations, time periods, etc.), the tool identifies opportunities for strategic price adjustments to maximize revenue.

## Background
In retail environments, understanding customer's response to price changes is crucial for maximizing revenue. This tool uses historical sales data to calculate price elasticity across various dimensions, enabling targeted price strategies that can increase profitability while minimizing negative impacts on customer satisfaction.  Product discounts over the trailing 365 days is used to represent price points.  Through simple regression, we are able to estimate changes in volume relative to changes in price.

## Features
- **Multi-dimensional elasticity analysis**: Calculate price elasticity across product categories, subcategories, locations, time periods, brands, and more
- **Dynamic price clustering**: Group products into price tiers for more meaningful elasticity analysis
- **Interactive visualizations**: Heat maps showing elasticity interactions between dimensions
- **Comprehensive metrics**: Statistics including R-squared values, p-values, and sales volume for each elasticity calculation
- **Flexible data grouping**: Configurable data aggregation to suit different analysis needs

## Requirements
- Python 3.7+
- Required packages:
  - pandas
  - numpy
  - seaborn
  - matplotlib
  - scikit-learn
  - scipy
  - statsmodels

## Data Requirements
The tool expects sales data with the following fields:
- Transaction ID
- Datetime
- Product identifier (barcode)
- Product name, category, and subcategory
- Brand
- Location/store identifier
- Sales quantity
- Unit price
- Unit discount
- Price JSON (for extracting pricing details)

## Core Functions

### `extract_price(text)`
Extracts pricing information from JSON strings, handling both single unit and bulk pricing structures.

### `add_category_brand_column(df)`
Creates a 'top_brand' feature that identifies the top 5 brands by unit sales for each product subcategory and labels the rest as 'Other'.

### `price_cluster(df, cluster_dim, min_clusters, max_clusters)`
Groups products into price clusters within specified dimensions, allowing for elasticity analysis at different price points.

### `group_data(df, dimension)`
Aggregates data based on selected dimensions for elasticity calculation.

### `calculate_elasticity(df, dimension, min_observations)`
Calculates price elasticity for a given dimension using regression on log-transformed price and quantity data.

### `run_analysis(df)`
Performs elasticity analysis across all specified dimensions and returns combined results.

### `elasticity_interactions_visualization(df, primary_dim, secondary_dim, min_observations)`
Creates heatmap visualizations showing elasticity interactions between two dimensions.

## Example Results
The tool provides a comprehensive DataFrame with elasticity calculations for each dimension value, including:
- Elasticity coefficient
- Count of observations
- Average price
- Mode price
- Average discount
- Average units sold
- Total net sales
- Total units
- R-squared (model fit)
- P-value (statistical significance)
- Net sales share (percentage)

## Applications
- **Price Optimization**: Identify products with inelastic demand for potential price increases
- **Promotional Strategy**: Target elastic customer segments with promotions to counteract price increases
- **Inventory Management**: Understand demand sensitivity across product categories
- **Store-level Pricing**: Implement location-specific pricing strategies
- **Time-based Pricing**: Optimize prices based on hour or day of week elasticity patterns

## Author
Trey Handley - [fkhandley@gmail.com](mailto:fkhandley@gmail.com)

This project was completed as part of the MSDS696 Practicum II course at Regis University, Spring 2025.
