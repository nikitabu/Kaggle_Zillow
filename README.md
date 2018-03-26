# Kaggle: Zillows's Southern California Housing Price Prediction Competition

This was the second Kaggle competition I participated in, following up on my experience with prediction Moscow housing prices in the Sberbank competition.

Instead of predicting the house valuations themselves, we are now tasked with predicting the log-error between Zillow's price estimate and the actual sale price. Therefore, the features most useful for predicting overall value, may not be the most useful variables for predicting the overall error. The provided data set consists of about 90,000 transactions in the Southern California housing market, with 58 features (e.g. square footage, number of floors, build year, and so on) 

An exploratory data analysis revealed numerous pieces of important information:

Inspection of the correlation matrix showed that the variables with the largest correlation with log-error are the basement area, shed area, and finished living area. As many So-Cal residents know, most homes in California don't have basements, which may explain why this variable may contributed to variability. Likewise, the presence and size of a shed is typically not a home-buyer's primary concern. Finished living-area alone may not be a useful data point, since it may be the that the percentage matters more, and that the value may go into a repair cost upon purchasing.
Heteroskedastic features (errors varying with feature values) are of particular interest for this competition. Homes with high or low values of certain variables for example, may contribute to the error in differing degrees.
There are numerous features that naively appear to be ordinal (e.g. filled in with Integers 1-30) but aren't, and should be hot-encoded into multiple columns.
And there are sometimes significant differences between train and test distributions, which may cause substantial differences between local cross-validation and leaderboard performance.
To fill in missing data, I tried using the MICE (Multiple Imputation by Chained Equations) algorithm, which is particularly useful for complex datasets where simple imputation approaches are not sufficient.

In the end, I managed to make it into the Top 15%! 

These price and price variability lessons I learned in this and the Sberbank competition have wide applicability in data science. They can be used anytime we have to predict the price of a complex object like a vehicle, office building, more general real estate, or fine art for example.
