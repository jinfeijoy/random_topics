# Outliers 

* Z-Score Method: The Z-score method identifies outliers by measuring how many standard deviations a data point is from the mean. This method is most effective when the data is normally distributed.
* Interquartile Range (IQR) Method: This is one of the simplest and most widely used methods to identify outliers in a dataset. The IQR method identifies outliers by looking at the spread of the middle 50% of the data.
* Isolation Forest: Isolation Forest is an algorithm specifically designed to detect outliers.
* DBSCAN (Density-Based Spatial Clustering of Applications with Noise): This method can reveal clusters of arbitrary shape and identify outliers as points that do not belong to any cluster ([See this research article]). This method is efficient in handling noise in the dataset.
* Outlier detection for time-series dataset
    * Rolling Statistics: This method calculates rolling statistics (e.g., rolling mean and standard deviation) and identifies outliers based on deviations from these statistics.
    * Seasonal Decomposition: Using seasonal decomposition, we break down the time series into trend, seasonality, and residual components. Outliers are often visible in the residual component.
    * Prophet: Prophet is an open-source time series forecasting tool developed by Facebook ([See this GitHub page]). It’s designed to handle data with strong seasonal patterns and multiple seasons of historical data. It is a powerful tool that models seasonality and trend, and can be used for anomaly detection by comparing actual values against predicted values ([Reference article]).
    * Isolation Forest: Isolation Forest is an unsupervised machine learning (scikit-learn documentation page) algorithm that’s particularly effective for anomaly detection, including in time series data. The algorithm works by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature. The logic behind it is that outliers are more likely to be isolated earlier in the random partitioning process than normal points ([See this research article]) .
    * ARIMA: ARIMA (AutoRegressive Integrated Moving Average) is a widely used statistical method for time series forecasting, and it can be used to detect and remove outliers by analyzing the residuals (the difference between the actual values and the predicted values).

### Reference
* https://medium.com/@nivedita.home/outlier-detection-and-removal-in-python-ad1f63ccb662
