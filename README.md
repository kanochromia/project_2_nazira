# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2: Ames Housing Data

## Table of Contents
* Problem Statement
* Data Set and Data Dictionaries
* Data Cleaning
* Exploratory Data Analysis (EDA)
* Pre-Processing and Modelling
* Conclusion and Analysis
* Recommendations
* References

## Overview

We are tasked with creating a regression model based on the Ames Housing Dataset. This model will predict the price of a house at sale.

The Ames Housing Dataset is an exceptionally detailed and robust dataset with over 70 columns of different features relating to houses. There are 2051 houses, and 80 features to be exact.

## Problem Statement

In this scenario, we want to predict the price of a house at sale to provide insights for potential homebuyers and existing homeowners.

We want to create a regression model to predict the sale price using the 70 over columns of different features.

We want to identify the features that affect the sale price of the house the most, both negatively and positively.

Ultimately, model can be used to assist homeowners to know how to increase house prices through home improvements so that their property can remain competitive, and potential homebuyers know what to look out for.

After Data Cleaning, Pre-Processing and Modelling, we will analyse the RMSE and  𝑅2  scores using RidgeCV, LassoCV and ElasticNetCV models.

## Data Set and Data Dictionaries

The dataset is retrieved from [here](https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data). Similarly, the raw data dictionary can be parsed from [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).

## Data Cleaning

The data is cleaned by using these steps:

<li>Dropping columns which have more than 60% of missing data.
<li>Replace missing values with NA in 12 columns.
<li>Drop 1 row which has a null value for Masonry Veneer Type.
<li>Rename all the feature columns to lowercase and remove the spaces.
<li>Creating an ordinal dictionary for features that have a likert scale and mapping them onto relevant columns.
<li>Mapping mean values for null values in lot frontage cells.
<li>Drop multicollinear columns such as basement full bath and basement half bath columns.
<li>Drop columns which are secondary features.

## Exploratory Data Analysis (EDA)

These are the visualisations that were plotted:

1) Correlation Matrix against All the features
2) Distribution of Individual features
3) Scatterplot of Features having a strong correlation against Sale Price (>|0.5|) - Overall Quality, Year Built, Year Remodelled/Added, Masonry Veneer Type, Total Basement Square Footage, 1st floor square footage, Above ground living area square footage, full bath, total number of rooms above ground, garage cars, garage area.
4) Bar graph of the count of the number of houses according to neighborhoods
5) Boxplots of the sale prices of houses according to neighborhoods

## Pre-Processing and Modelling

1) Afterwards, we dummify the categorical variables, as computers cannot analyse strings.
2) Created a baseline model using Linear Regression.
3) Created RidgeCV, LassoCV and ElasticNetCV regression models.

## Conclusions and Analysis

It is important to investigate why the house features are affecting sale price, especially for homeowners and homebuyers. For homeowners, they need to know whether their property still has the "selling qualities" to remain competitive in the market, but they will need to know what to improve on the most during renovation works. For homeowners, they would want the best bang for their buck when purchasing a home.

This model is only applicable to Ames, Iowa. It is a university town, so the population is undoubtedly younger. Iowa, as a state, focuses on agriculture, so this model may not be applicable in another town in Iowa or another state altogether.

To evaluate the success of this model, we will need to see what are the features that will greatly affect the Sale Price positively/negatively.

In this model, ElasticNetCV performs the best with the lowest RMSE score of $24562 to the average.

### Selecting ElasticNetCV - Why?

|Model|Linear Regression|Ridge Regression|Lasso Regression|ElasticNet Regression|
|---|---|---|---|---|
|R² - Train|0.8689122980728214|0.8688971800882028|0.8689043229426068|0.858050127344571|
|R² - Valid|-2.0105747201971294e+19|0.891960308611282|0.8920815454781326|0.8952323861356212|
|RMSE|-|24979.488670106817|24965.4693547495|24598.31751109648|

Lasso assigns a penalty to the coefficients in the linear model, eliminating variables with coefficients that zero. It doesn't perform well when there is multicollinearity in the features. By glancing at the features, some of them are greatly related to each other. As for Ridge, it reduces the penalty closer to 0, but it might not be enough as there are too many features compared to the number of observations.

In this situation, ElasticNet performs the best.

ElasticNet reduces the impact of different features while not eliminating all of the features. It combines both Lasso and Ridge features, but not completely removing any feature.

### Understanding Coefficients

By viewing the top 5 that positively affect Sale Prices and bottom 5 features that negatively affect Sale Prices, homebuyers should consider these factors when purchasing a home in Ames, Iowa and what homeowners should consider to put their property in a competitive position in the housing market:


Purchasing a house situated on a lot that has irregular shape will affect the Sale Price negatively by $3682.90 for every unit increase. It affects the sale price the most. This means that irregular shaped lots are priced lower in the market. Homeowners can't really change much about this aspect, hence they should focus more on the features of the house.

The exterior covering of the house matters - if it is made out of Stucco, the house is more likely to be priced lower as well. For every unit increase, the price will decrease by $2418.78. Same goes for having a Mansard roofstyle, which decreases the sale price by $1907.95 for every unit increase. We do not have the domain knowledge to understand if a Stucco material is high or low quality, hence both homeowners and homebuyers should consider if the material is what they want. For a Mansard roofstyle, it may not suit the current trend if the houses are old, hence the price may be lower. Homeowners may consider to renovate to other roofstyles to boost their sale prices.

Potential homebuyers should also consider purchasing Townhouses as they are cheaper on the market compared to Single-family Detached, two-family conversion houses and duplexes.

As for the features that positively affect the Sale Price, an increase in the overall quality of the house will undoubtedly improve Sale Prices per unit increase by $10901.95. Similarly, the exterior matters a lot, which improve sale prices by $6914.73 per unit increase. Same goes for kitchen quality as well, increasing at a rate of $6775.88 as the quality increases.

As for the general living area, the greater the square footage, the sale price increases by $8259.67 per unit increase. This also affects the 1st floor square footage, which increases by $6237.36 per unit increase.

## Recommendations

At the end of the day, this model is only applicable to Ames, Iowa. Below are the suggested improvements and special sidenotes to this model:

Collect more data that is up-to-date.
Remove features that are too specific or combine subfeatures.
Add features that are beyond just the house features such as distance to schools or public transportation hubs.
Consider socio-economic factors such as crime rates or quality of schools.

Ames is a university town, hence this model after improvement may be used in similar university towns. However, the whole state of Iowa is known to focus on agriculture, hence the model (as good as it may be after improvement), might not be the best to use on towns that do not specialise in agriculture or are on flat land (e.g. Florida).

### Citations and References

1. https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/overview
---
