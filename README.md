# Ames Housing Price Prediction
![Ames Housing Overview](images/ames_overview.png)

## Overview

This project is based on [a well known kaggle competition](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) and focuses on predicting housing sale prices in Ames, Iowa using various regression techniques (XGBRegressor, GradientBoostingRegressor, RandomForestRegressor, AdaBoostRegressor, and ExtraTreesRegressor). With a RMSLE of.1266 on unseen data the [Extreme Gradient Boosting Regressor](https://github.com/dmlc/xgboost/tree/master) was the best model I made.


## Dataset

The dataset used in this project over 81 columns describing 2051 sales of residential properties in Ames, Iowa. The original dataset has been augmented through feature engineering, with additional features created or transformed to improve the predictive power of the models.

**Features**:

| Feature         | Description                                               |
|-----------------|-----------------------------------------------------------|
| SalePrice       | The property's sale price in dollars. This is the target variable that you're trying to predict. |
| MSSubClass      | The building class                                       |
| MSZoning        | The general zoning classification                         |
| LotFrontage     | Linear feet of street connected to the property           |
| LotArea         | Lot size in square feet                                   |
| Street          | Type of road access                                       |
| Alley           | Type of alley access                                       |
| LotShape        | General shape of property                                  |
| LandContour     | Flatness of the property                                   |
| Utilities       | Type of utilities available                                |
| ... (truncated for brevity) | ...                                                       |
| MoSold          | Month Sold                                                |
| YrSold          | Year Sold                                                 |
| SaleType        | Type of sale                                              |
| SaleCondition   | Condition of sale                                         |

## New Columns Created by `quality_multiplication` Function
#### Abridged slightly - for garages I made columns the same way for condition as I did with quality
| New Column Name | Columns Used | Description |
| --- | --- | --- |
| lot_area_frontage | lot_area, lot_frontage | Represents the product of lot area and frontage. |
| garage_area_type_Attchd_qual | garage_area, garage_type_Attchd, garage_qual | Represents the product of garage area and garage quality for attached garages. |
| garage_area_type_Basment_qual | garage_area, garage_type_Basment, garage_qual | Represents the product of garage area and garage quality for basement garages. |
| garage_area_type_BuiltIn_qual | garage_area, garage_type_BuiltIn, garage_qual | Represents the product of garage area and garage quality for built-in garages. |
| garage_area_type_CarPort_qual | garage_area, garage_type_CarPort, garage_qual | Represents the product of garage area and garage quality for carport garages. |
| garage_area_type_Detchd_qual | garage_area, garage_type_Detchd, garage_qual | Represents the product of garage area and garage quality for detached garages. |
| garage_area_qual | garage_area, garage_qual | Represents the product of garage area and garage quality, irrespective of garage type. |
| garage_area_cond | garage_area, garage_cond | Represents the product of garage area and garage condition. |
| garage_area_finish | garage_area, garage_finish | Represents the product of garage area and garage finish. |
| fireplace_qu_val | fireplace_qu, fireplaces | Represents the product of fireplace quality and the number of fireplaces. |
| pool_qc_area | pool_qc, pool_area | Represents the product of pool quality and pool area. |
| bsmt_sf_qual_type_1 | bsmtfin_sf_1, bsmtfin_type_1 | Represents the product of finished basement area and basement finish type 1. |
| bsmt_total_sf_cond | total_bsmt_sf, bsmt_cond | Represents the product of total basement area and basement condition. |
| bsmt_total_sf_qual | total_bsmt_sf, bsmt_qual | Represents the product of total basement area and basement quality. |
| misc_feature_Gar2_val | misc_feature_Gar2, misc_val | Represents the product of miscellaneous feature "Gar2" and its value. |
| misc_feature_Othr_val | misc_feature_Othr, misc_val | Represents the product of miscellaneous feature "Othr" and its value. |
| misc_feature_Shed_val | misc_feature_Shed, misc_val | Represents the product of miscellaneous feature "Shed" and its value. |
| misc_feature_TenC_val | misc_feature_TenC, misc_val | Represents the product of miscellaneous feature "Tennis Court" and its value. |




**Target Variable**:
- Sale Price: The target variable to be predicted.

## Feature Engineering

The problem with using this data for predicting sale price is that each column affects the sale price differently. Some remark on the presence of a feature and some describe the quality of that specific feature. I attempted to resolve it by using my map_home() function to map the 'quality' columns to make them ordinal, which are then used to add a quality multiplier to the various types of amenities described in the data. An example of why I did this: A garage should increase your house's value if it is in good condition, if it is in disrepair it is a burden and its presence should decrease the sale price. I used my discretion when creating the maps as there were several different patterns for describing quality

## Regression Techniques Explored

Various regression techniques have been implemented and analyzed to predict housing sale prices. The regression models explored in this project include:
1. **Linear Regression**
2. **Random Forest Regressor**
3. **Gradient Boosting Regressor**
4. **AdaBoost Regressor**
5. **Extra Trees Regressor**
6. **XGB Regressor**


## Project Structure

The project is organized as follows:

- `datasets/`: Contains the dataset files.
- `code/`: Jupyter Notebook for this project and python file to automate preparation of this type of data for modeling
- 
- `images/`: images created in jupyter notebook

