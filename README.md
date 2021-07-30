## John Deere - Used Tractor Price Estimator (In Progress)

### Introduction:
This project is focused on data collection and creating an ML model using this data. This will be a regression model that predicts the price of an item based on other continuous features.

### The Data:
The data is being retrieved on an ongoing basis and it contains features of John Deere tractors that are on sale in the second hand market in the United Kingdom. It contains features with information about specific tractors that appear in ads on the second hand market that are likely to influence the cost of the machine to the buyer. These features range from static attributes that pertain to a specific model of tractor (such as Horsepower and Weight) to attributes that are specific to a certain instance of that model (i.e. numerous models with the same Horsepower and Weight can have different figures for Year of Production, or the number of Hours work the tractor has done). Both the static elements and elements that change depending on the instance can impact the price at which a used tractor is sold.

### Features of the Dataset:

**Make:** The brand the machine is made by. In this particular dataset the make for all tractors is John Deere

**Model:** This is an identifier for each model (the identifiers are named by John Deere themselves) that helps us differentiate from each model of tractor. In some instances, especially of many models built since 2010, we can identify different features of the tractor through the model name:
1) the first number in many of the models identifies the size of the tractor (i.e. a 6125R tractor is a size larger than a 5125R).
2) The last three digits tell us how much horsepower the tractor has (i.e. a 6155M has 155 horsepower).
3) The letter at the end of tells us the spec of the tractor (i.e. a 6155M is an ordinary spec tractor, whereas a 6155R is a higher spec tractor which will be more expensive).
For older tractors it is more difficult to identify the size and horsepower of a tractor based on the model name itself, which is why there are separate columns containing the horsepower and weight figures for each tractor (which are used to make the predicions instead of the model name).

**Hours:** This column tells us how many hours the tractor has been used for. Tractors that have been used for fewer hours will cost more, as they are in most cases capable of doing more hours of work over their expected lifetime. The expected lifetime of most tractors is around 12,000-13,000 hours, after which they can become more expensive to maintain and therefore become much less valuable.

**Year:** This column tells us the year the tractor was originally sold to its first buyer. Newer tractors generally cost more, even if they have been worked for a large number of hours.

**HP:** This tells us how many horsepower a tractor has.

**Weight in Kg:** This tells us the weight of the tractor in kg without including extra attachments.

**Price ex VAT:** The price the tractor is currently for sale on the Farmers Weekly website, excluding VAT.

**ID:** This is a simple identifier used to uniquely identify each tractor in the dataset.

**Front Loader:** This tells us whether a tractor is fitted with a front loader. This is an optional extra on most tractors and generally costs a few thousand euro/pounds extra along with the tractor itself, and therefore will add a few thousand euros/pounds of value to a second hand tractor for sale on the market.


### Project Overview:
The original data file was created in Microsoft Excel to be loaded into pandas as a single dataframe. An adaboost regressor was trained to make predictions on unlabelled instances using the small amount of data that has been collected so far. The model outlined in the original notebook achieved an r-squared score of 0.62, but this figure can vary and normally turns out slightly lower, between 0.55 and 0.6. These figures are low because we are training with a very small number of instances; when more data is collected for training we will achieve more accurate scores, after which we can begin more specific data manipulation and algorithm tuning tasks to increase prediction accuracy. The second version of the notebook consists of a model trained with more data; this resulted in a large increase in the r-squared score to 0.81, though the MAE and RMSE scores remained largely the same, with only minor improvements. The next development will expand the dataset further and employ data cleaning techniques such as outlier removal and feature engineering in an attempt to improve the MAE and RMSE scores.

The file was also split into two separate csv files, and each was loaded into MySQL as separate tables; one contains features related to tractor models, and the other contains features related to specific instances of that model appearing on the second hand market. These tables are relational (the Model ID feature in the Instances table is a foreign key of the Model ID feature in the Models table), which gives a good opportunity for exploration with MySQL. There is also a plan to make some visualisations of this data in Tableau once more data has been collected.

### Motivation:
The motivation for this task was to collect my own data in order to build a unique project that focuses on a specific area of second hand goods pricing. Many datasets exist that price houses, second hand cars etc., but datasets relating to agricultural machines are much less common. I am also motivated to find out if this data could result in a model that can make accurate predictions, which will not be found out until more data is collected.

A personal motivation for this project is that I wanted to use some of my own domain experience in a data analytics project. I come from a farming background and have experience operating John Deere tractors. For this reason data collection at this moment in time is limited to John Deere machines as I am knowledgeable about the different characteristics of different tractor models through both research and actual experience working with these machines. This will allow me to collect data at a quicker pace than if I were to choose a brand other than John Deere, or have no limitation to the number of tractor brands used.

### What Problem Does This Solve?
The used machinery markets in both the UK and Ireland are awash with ads for agricultural vehicles that have all the information you need about a tractor's condition, but many of these ads have no price tag attached to the machine. Normally in cases like these you have to contact the owner of the advert expressing interest in the ad to find out the price of the tractor, but this can be inconvenient, especially in Ireland where the vast majority of ads have no price included. This project aims to address this problem by training a model based on information from ads that **do** contain a price tag, in order to predict the price of tractors in ads that **do not** have one included. Data from the UK is being used in this project as there are more ads with price tags in the second hand market compared to Ireland.

Right now, the model makes predictions based on continuous features of the tractor, and not the name of the model of tractor itself. This is because we are using real data for the model, and not all models of John Deere are on sale at the minute on the second hand market. This is why data needs to be collected over time, so we can collect data for as many models as possible. At one stage I hope the model will be able to make predictions based simply on the model of tractor, year of production, and number of hours worked.


### Technologies Used:
Microsoft Office Excel, Python (pandas, numpy, sci-kit learn), MySQL, Tableau Public.

### Summary:

- Collected data relating to the pricing of John Deere tractors on the second hand market for model training 
- Trained an AdaBoost regressor to predict the cost of tractors based on a number of features
- More data is to be collected in order to make more accurate predictions: this is still a work in progress
- Future plans include data manipulation and model tuning to increase accuracy once more data is collected, as well as a more comprehensive exploration using MySQL and data visualisation in Tableau. 
