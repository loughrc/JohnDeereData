## John Deere - Used Tractor Price Estimator (In Progress)

### Introduction:
This project is focused on data collection and creating an ML model using this data. This will be a regression model that predicts the price of an item based on other continuous features.

### The Data:
The data is being retrieved on an ongoing basis and it contains features of John Deere tractors that are on sale in the second hand market in the United Kingdom. It contains features with information about specific tractors that appear in ads on the second hand market that are likely to influence the cost of the machine to the buyer. These features range from static attributes that pertain to a specific model of tractor (such as Horsepower and Weight) to attributes that are specific to a certain instance of that model (i.e. numerous models with the same Horsepower and Weight can have different figures for Year of Production, or the number of Hours work the tractor has done). Both the static elements and elements that change depending on the instance can impact the price at which a used tractor is sold.

### Project Overview:
The original data file was created in Microsoft Excel to be loaded into pandas as a single dataframe. An adaboost regressor was trained to make predictions on unlabelled instances using the small amount of data that has been collected so far. The model outlined in the notebook achieved an r-squared score of 0.62, but this figure can vary and normally turns out slightly lower, between 0.55 and 0.6. These figures are low because we are training with a very small number of instances; when more data is collected for training we will achieve more accurate scores, after which we can begin more specific data manipulation and algorithm tuning tasks to increase prediction accuracy.

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
- Trained a Random Forest Regressor to predict the cost of tractors based on a number of features
- More data is to be collected in order to make more accurate predictions: this is still a work in progress
- Future plans include data manipulation and model tuning to increase accuracy once more data is collected, as well as a more comprehensive exploration using MySQL and data visualisation in Tableau. 
