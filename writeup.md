# Analysis Writeup

## Methodology

I started by loading the two datasets separately. The trading dataset had around 211K rows with details like trade size, PnL, leverage, and direction. The sentiment dataset had about 2,644 daily entries with the Fear & Greed Index score and its classification (Fear, Greed, Neutral, etc.).

I cleaned both datasets independently, handled missing values, removed duplicates, and normalized the timestamps to daily level. Then I merged them using an inner join on the date column, which gave me around 184K matched trade records.

From there, I engineered several features at the daily trader level: total PnL, win rate, average trade size, average leverage, number of trades, and the ratio of long to short positions. I also simplified the sentiment labels into three buckets: Fear, Neutral, and Greed.

## Key Insights

The first thing that stood out was that traders earn significantly more on Fear days compared to Greed days. The average daily PnL on Fear days was around $125K versus $51K on Greed days, and this difference was statistically significant (Mann Whitney U test, p = 0.0009). This was counterintuitive because you'd expect fear to hurt performance, but it seems like fearful markets create better opportunities for crypto traders.

When I looked at behavior changes, I noticed that traders tend to use higher leverage on Fear days (114x vs 78x) but with smaller position sizes. They also lean slightly more towards short positions during Fear, which makes sense given the bearish sentiment.

The segmentation analysis revealed that frequent traders benefit the most from Fear days, earning $195K compared to $88K on Greed days. Consistent traders, on the other hand, showed stable performance regardless of sentiment, which suggests their edge is not tied to market mood.

I also ran K-Means clustering on trader level features and found three natural groups. The first group (9 traders) uses low leverage with large positions and has the highest win rate at 49%. The second group (20 traders) uses very high leverage with small positions but earns the least. The third group (3 traders) trades extremely frequently and generates the highest total PnL despite moderate win rates.

The predictive model (Random Forest) achieved 92% accuracy in predicting daily profitability. The most important features were win rate and trade frequency, while the sentiment score itself contributed only about 4%. This tells us that what a trader does matters far more than what the market feels.

## Strategy Recommendations

First, frequent traders should increase their activity during Fear periods. The data clearly shows that active traders capture more alpha when the market is fearful. They should maintain moderate position sizes and stay disciplined, but not shy away from trading more often during these windows.

Second, consistent traders should stick to their existing strategy regardless of sentiment. Their performance barely changes between Fear and Greed days, which means their edge is structural rather than sentiment driven. Changing behavior based on market mood would likely do more harm than good for this group.

As a general rule, traders should be cautious about using excessive leverage on Greed days. Despite the optimistic mood, Greed days consistently show lower PnL across all segments. Capping leverage during these periods could help protect against overconfidence driven losses.