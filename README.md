# Machine-Learning-Final-Project----Buschkopf-Alasia
Final Project for CMPSCI 4200 Python for Data Science

I am using the House Sales in King County, USA dataset from kaggle.com available here: https://www.kaggle.com/datasets/harlfoxem/housesalesprediction

The columns included in this dataset are:
id - Unique ID for each home sold
date - Date of the home sale
price - Price of each home sold
bedrooms - Number of bedrooms
bathrooms - Number of bathrooms, where .5 accounts for a room with a toilet but no shower
sqft_living - Square footage of the apartments interior living space
sqft_lot - Square footage of the land space
floors - Number of floors
waterfront - A dummy variable for whether the apartment was overlooking the waterfront or not
view - An index from 0 to 4 of how good the view of the property was
condition - An index from 1 to 5 on the condition of the apartment,
grade - An index from 1 to 13, where 1-3 falls short of building construction and design, 7 has an average level of construction and design, and 11-13 have a high quality level of construction and design.
sqft_above - The square footage of the interior housing space that is above ground level
sqft_basement - The square footage of the interior housing space that is below ground level
yr_built - The year the house was initially built
yr_renovated - The year of the house’s last renovation
zipcode - What zipcode area the house is in
lat - Lattitude
long - Longitude
sqft_living15 - The square footage of interior housing living space for the nearest 15 neighbors
sqft_lot15 - The square footage of the land lots of the nearest 15 neighbors

The target column that I would like to predict is the price of a house. I think the important columns to explore through further analysis include the sqft of living space, number of bathrooms, building grade, and the sqft of surrounding homes which will indicate the size of homes in the neighborhood. Based on this heatmap, it seems these are all likely strong indicators.
![price heatmap](https://user-images.githubusercontent.com/82225286/165663070-20fbef7f-e3a2-4891-b6b4-71d05db93ad2.png)

This plot shows the distribution of target values (price) in my dataset:
![histogram price](https://user-images.githubusercontent.com/82225286/165817872-555c883f-5c58-4521-ae9a-dd07c0d9e0c4.png)

After splitting the date out into months and aggregating the price to an average price per sq foot, it seems that seasons/months where the weather is subjectively "nice" (spring and fall) such as March/April, and September/October have slightly higher average price per sq foot, so this may be another connection to look into.
![month](https://user-images.githubusercontent.com/82225286/165663010-54d14d49-e468-4395-af88-70e556e82814.png)

This plot shows a relationship between price and sq ft of living space that is also somewhat related to the building grade.
![grade](https://user-images.githubusercontent.com/82225286/165664848-9d7f2ecc-bef0-4588-ad73-dbf6ecc61987.png)

Number of bathrooms also shows a general relationship with the price.
![bathrooms](https://user-images.githubusercontent.com/82225286/165665239-9cfe2e64-f8c8-409e-873e-cb9470bd4938.png)

For my prediction plan, I will aggregate things a bit more - perhaps create 3 building grades (falls short = 1, average = 2, and high quality = 3). Then I will split the data into a test and train set and try to find a regression model that fits the data to accurately predict house price based on season it sold, grade, view, sqft living space, etc.

