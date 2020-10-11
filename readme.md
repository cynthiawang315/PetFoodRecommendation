# Predicting the Recommendation Score of Pet Food Using Chewy Data

## Context
The pet industry has been rising during these past a few years. According to the report from American Pet Products Association, pet owners spent $38.4 billion on pet food and treats in 2020. Pet food companies are booming and they are constantly introducing new pet food to attract the pet owners. Chewy, an online retailer of pet supplies, carries a wide range of pet food. When pet food companies want to work with Chewy to promote their new products, how would Chewy know if the new products would win pet owners' hearts and recommend the food? 

## Goal
This project aims to use product information such as price and nutrition data of pet food to predict consumer recommendation scores of pet food items listed on Chewy.

## Findings and Conclusions
- Consumers value the nutritional content of pet food. They give higher recommendation scores for food with high protein content.
- Consumers recommend big name brands over smaller brands.
- Pricing of pet food products also influence recommendation score. Consumers tend to recommend more affordable pet food.
- Cat food tends to receive lower recommendation scores than dog food.
- Text analysis on consumer reviews could help us better understand the recommendation scores of the products (e.g. cat food items tend to receive lower recommendation scores because cats are finicky eaters!).



# Methodology
## Data Collection
The dataset used in this project is scraped from www.chewy.com. This project focuses on dog and cat food. Important features that might influence recommendation scores are scraped from Chewy using BeautifulSoup. The links of all the food items are scraped from the main pages first, and then product features are scraped from each individual page. Results from web scrapping are organized into a dataframe. The product features that are initially collected are listed below:  
- Product Title
- Brand
- Item Number
- Product Recommendation Score
- Product Price
- Product Weight
- Food Form
- Number of Reviews
- Life Stage
- Special Diet
- Minimum Protein %
- Minimum Fat %
- Maximum Fiber %
- Maximum Moisture %

## Data Cleaning and Processing
- Remove items that are unavailable or sold out.
- Remove items with 0 reviews and no recommendation score.
- Convert columns into correct data types.
- Fill the missing values of price/lbs using the median values of the corresponding food forms.
- Fill the missing values of protein, fat, fiber and moisture content using the median values of the corresponding food forms.


## Feature Engineering
- Transform the target variable (recommendation score) by boxcox transformation.
- Calculate price per pound for each product.
- Group 242 brands into 4 brand groups according to their popularity on Chewy.
- Generate columns indicating life stages of adult, senior, and puppy/kitten. Some products are designed for multiple life stages.
- Extract food forms of all the products and created columns for treats, dry food, wet food, freeze-dried food, food topping, dehydrated food, air-dried food, and frozen food. Some products belong to multiple categories.
- After adjusting the model, remove the life stage variables and five food form variables (dehydrated, frozen, airdried, freezedried, wetfood) to reduce multicollinearity.


## Analysis and Models
- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest

# Deliverables
- Jupyter notebook for web scrapping
- Jupyter notebook for data cleaning and feature engineering
- Jupyter notebook for models with all features
- Jupyter notebook for models with reduced feature set
- Pickle files for data