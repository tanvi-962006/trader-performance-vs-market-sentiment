# Trading Behavior & Market Sentiment Analysis

This project explores how crypto traders behave during different market sentiment conditions (Fear vs Greed). I used two datasets: one containing historical trades from a crypto exchange, and the other containing daily Fear & Greed Index scores. The goal was to find patterns in trader performance and behavior that change depending on market mood.

## What this project does

I cleaned and merged both datasets on a daily level, then analyzed whether traders perform differently on Fear days compared to Greed days. I also segmented traders into groups (by leverage usage, trading frequency, and consistency) and checked how each group responds to sentiment shifts. On top of that, I built a Random Forest model to predict daily profitability and used K-Means clustering to identify natural trader archetypes.

## How to set it up

Make sure you have Python 3.8 or above installed. Then install the required packages:

``` pip install -r requirements.txt ```


## How to run

Open the notebook file in Jupyter or VS Code and run all cells from top to bottom. The notebook is structured in sections:

1. Data loading and cleaning
2. Feature engineering and merging
3. Fear vs Greed performance analysis
4. Behavior analysis by sentiment
5. Trader segmentation and cross analysis
6. Strategy recommendations
7. Predictive model and clustering (bonus)

All charts will be saved automatically in the `output/` folder.


## Quick summary of findings

Traders actually make more money on Fear days than Greed days, which was surprising. Frequent traders benefit the most from Fear periods. I also found that high leverage doesn't necessarily lead to better returns. The clustering revealed three distinct trader types: cautious big position traders who win often, high leverage gamblers who underperform, and hyperactive power traders who make the most overall. More details in the writeup.