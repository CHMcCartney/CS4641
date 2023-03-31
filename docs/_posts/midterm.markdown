
# Introduction / Background

New York City (NYC) is one of the largest and most populous urban cities in the United States, known for its high population density, frequent traffic congestion, and relatively expensive travel costs (1). As a cultural and economic powerhouse, NYC is well known for its particular yellow-cabs which serve as a primary mode of transportation for millions of residents and tourists every year. Over the years, the fares for NYC yellow cabs have evolved to keep up with the changing times and the city's transportation needs, and the New York City Taxi and Limousine Commission (TLC) continues to monitor and adjust the fare structure as needed to ensure that it remains fair and equitable for all involved. Thus, there has been a growing interest in using machine learning algorithms to predict taxi fares, which can provide valuable insights for both passengers and taxi drivers (2). The ability to accurately predict taxi fares can help passengers plan their trips more effectively, while also helping taxi drivers optimize their routes and pricing strategies. This has led to a growing body of research focused on developing models that can accurately predict taxi fares in New York City. In this context, machine learning techniques have proven to be effective in providing accurate predictions, and are being widely used by researchers and industry practitioners to solve this problem

# Problem Definition

This model will seek to address existing datasets to produce a comparatively more accurate predictive model for taxi trip fares in New York City. The current taxi fare system in New York City is based on a meter that calculates the fare based on time and distance and any additional charges such as tolls and surcharges that may be implied during the peak travel times (3).  However, customers often complain about the unpredictability of taxi fares due to traffic conditions and other factors (4). Our goal is to develop a machine learning model that can handle all the relevant factors that go into predicting accurate fares for different routes, traffic conditions and times of the day. 


# Dataset:

We will be using [NYC's TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) to gather all necessary data. Records include fields capturing pick-up and drop-off dates/times, pick-up and drop-off locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts Since the data given on the website is using format .parquet, we will need to parse the data into an .csv file for further use. To achieve this, we can use pandas library in python and modify the .csv file to reflect changes.

We will be able to use Google Cloud AI Platform to estimate the taxi fare. We can use APIs like BigQuery API to import the dataset and train the model to calculate predictions and losses among other useful items.

This will allow us to compete with other submissions on kaggle since the previous submissions used old data (around 2015). The new data from NYC’s website will be more accurate and relevant to post-COVID time and will factor in inflated prices and make prediction based on it. However, the data existing before covid-19 has already been prepared below and will be merged into the new dataset from the NYC TLC website.

Dataset - (https://drive.google.com/file/d/1-CmijbmmmASVIQLBPF2FGCCz2avQqRni/view?usp=share_link)

# Methods

We are planning on using NYC taxi trip data to predict the fare amount for a taxi drive. This would involve training a model on the data using various supervised learning algorithms such as random forest or KNN and using existing packages and libraries such as scikit-learn. The given labels would be a few categories for how the fare changes based on the data. Parameters that may be analyzed in our model include trip distance, pick-up and drop-off locations, passenger count, and time.
Thus far, we have proceeded with data cleaning and dimension reduction using backward feature selection. The entries of the dataset have been converted into processable datatypes to allow for comparisons and further operations. We have also implemented a supervised linear regression model which operates with the most relevant variables to predict fare amounts. 

# Results and Discussion

Before attempting to apply predictive models paired with this data, the dataset was first cleaned and reduced to provide a solid foundation with which to obtain valid results. Beginning with the raw dataset, all null values were replaced with 0, and all columns were converted to the correct respective datatypes for further manipulation. Additionally, steps were implemented to remove all nonsensical data, including fare amounts less than $3.00 in value as well as unreasonably large entries for fare amounts exceeding hundreds and/or thousands of dollars. With MTA tax starting at $0.50 and improvement surcharges starting at $0.30, smaller values for each of these dimensions were also removed. Lastly, entries for passenger count exceeding 6 were removed, as New York City statutes indicate six as the legal maximum for passengers in yellow taxis (7). Following these steps, potentially useful features were extracted such as values for fare per mile, as well as individual features for time, including year, month, day of the week, etc. The larger parameter for date_time was removed since its features had been fully extracted. For dimension reduction, backward feature selection was implemented to select for the highest scoring features with comparatively low change in error. Although the team replaced missing values with 0 entries, it may have been more practical to replace such values with the statistical mean of that column, or some other applicable measure of central tendency.

In the case of predicting NYC taxi fares, we can use linear regression to model the relationship between the fare amount and the variables that may influence it. We built a linear regression model using the selected independent variables (trip_distance, passenger_count, tpep_pickup_datetime, tpep_dropoff_datetime) and the fare amount as the dependent variable. The model will estimate the relationship between the independent variables and the fare amount, and produce a set of coefficients that represent the strength and direction of the relationship. After model training, we evaluated the performance of the model using various metrics such as the mean squared error, R-squared, and root mean squared error. This will help us determine if the model is accurately predicting the fare amount based on the independent variables.

# Conclusion
Given the relatively large size of our raw dataset, performing dimension reduction and other cleaning methods presented signifcant difficulties. Despite this, we successfully applied common techniques to clean the dataset and obtain some degree of validity in our results. 

# Work Distribution Chart

| Group Members | Responsibilities |
| --- | ----------- |
| Pratham Patel | Introduction/Background + 1 Reference |
| Alan Huynh  | Methods/Algorithms + GitHub Page + 1 Reference |
| Charles McCartney | Methods + Results and Discussion + Conclusion + 1 Reference |
| Maharshi Patel | Proposed Timeline + Dataset + 1 Reference |
| Vedant Amin | Problem Definition + 1 Reference |

# References

1. [Exploring the Impact of COVID-19 on Taxi Demand in New York City Using Machine Learning](https://www.proquest.com/docview/2672015744?pq-origsite=primo)
2. [New York City Taxi Trip Duration using MLP and XGBoost](https://link.springer.com/article/10.1007/s13198-021-01130-x)
3. [Yellow Cabs Are Struggling. Congestion Pricing Could Deal a New Blow](https://www.nytimes.com/2022/10/11/nyregion/nyc-traffic-yellow-cab-tolls.html)
4. [Everything You Need To Know About NYC's Taxis](https://www.thetravel.com/what-to-know-about-taxi-cabs-in-nyc-costs/)
5. [Predicting Taxi Tip Rates in NYC](https://cseweb.ucsd.edu//classes/sp15/cse190-c/reports/sp15/050.pdf)
6. [City Commission Raises Rates for Yellow Cabs, App-Based Rideshares](https://www.ny1.com/nyc/all-boroughs/news/2022/11/15/city-raises-rates-for-yellow-cabs-app-based-rideshares)
7. [Driver Rule 54-15(g) Chapter 54 - Drivers of Taxicabs and Street Hail Liveries](https://www.nyc.gov/assets/tlc/downloads/pdf/rule_book_current_chapter_54.pdf) 
