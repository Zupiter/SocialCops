
# SocialCops Technical Challenge

# Aim

 Your team is working on building a variety of insight packs to measure key trends in the Agriculture sector in India. You are presented with a data set around Agriculture and your aim is to understand trends in APMC (Agricultural produce market committee)/mandi price & quantity arrival data for different commodities in Maharashtra.

# Objective

Test and filter outliers.

Understand price fluctuations accounting the seasonal effect

Detect seasonality type (multiplicative or additive) for each cluster of APMC and commodities

De-seasonalise prices for each commodity and APMC according to the detected seasonality type

Compare prices in APMC/Mandi with MSP(Minimum Support Price)- raw and deseasonalised

Flag set of APMC/mandis and commodities with highest price fluctuation across different commodities in each relevant season, and year.


# Variable description


• msprice- Minimum Support Price • arrivals_in_qtl- Quantity arrival in market (in quintal) • min_price- Minimum price charged per quintal • max_price- Maximum price charged per quintal • modal_price- Mode (Average) price charged per quintal
Methodology

# Task 1

The methodology followed for this assignment was to first check for missing values in the data, followed by identifying the outliers using a box plot for the target variable modal_price.

The box plot showed a large number of data points above the upper whisker, the outliers. The next step was to calculate the interquartile range (IQR), and then removing data points that were below Quartile1 - 1.5 * IQR and Quartile3 + 1.5 * IQR

Then 2 data tables given were combined to yield one. Then all missing values were filled.

# Task 2:

The data set had to be convereted to a time series, so as to plot the seasonal plots of the modal_price.

Now we query for each APMC and using seasonal_decompose we break into its residual, seasonal and trend parts. This process is repeated twice for each model, additive and multiplicative.
Now deseasonal component is finded out by removing seasonal part, i.e. we either subtract it if we use additive model or we divide observed by it otherwise.

The movement of prices from April 2014 till December 2016 have 2 identical cycles of drops and rises, whcih can be accounted for the type of crop the commodity is; that is; rabi or kharif crop.

The trends in deasonalised plots of the commoditites depict movement of the prices that is distinct for each commodity.


# Task 3:

We plot deseasonalized prices and msprice and observed price for each APMC. First we do for ith APMC and then loop over all.

# Task 4 

We group data by year, APMC, commodity and sort by  'fluc' or 'percentfluc'.

# Final results

The price differences in the minimum price set by the Government and the actual price that the commoditites are sold for may be due to a few reasons, one of which can be that the transportation cost involved may be too high for select commoditites. Since this is an aggregation on the APMC, Commodity and Year level, it may not be the exact clear picture on the miniscule level, but it brings to light the price differences between the decided prices and the real prices.
