# Machine-Learning-Final-Project----Buschkopf-Alasia

## Part 1: Data Preparation
I am using the House Sales in King County, USA dataset from kaggle.com available here: https://www.kaggle.com/datasets/harlfoxem/housesalesprediction</br>
**The columns included in this dataset are:** </br>
id - Unique ID for each home sold </br>
date - Date of the home sale</br>
price - Price of each home sold</br>
bedrooms - Number of bedrooms</br>
bathrooms - Number of bathrooms, where .5 accounts for a room with a toilet but no shower</br>
sqft_living - Square footage of the apartments interior living space</br>
sqft_lot - Square footage of the land space</br>
floors - Number of floors</br>
waterfront - A dummy variable for whether the apartment was overlooking the waterfront or not</br>
view - An index from 0 to 4 of how good the view of the property was</br>
condition - An index from 1 to 5 on the condition of the apartment</br>
grade - An index from 1 to 13, where 1-3 falls short of building construction and design, 7 has an average level of construction and design, and 11-13 have a high quality level of construction and design</br>
sqft_above - The square footage of the interior housing space that is above ground level</br>
sqft_basement - The square footage of the interior housing space that is below ground level</br>
yr_built - The year the house was initially built</br>
yr_renovated - The year of the house’s last renovation</br>
zipcode - What zipcode area the house is in</br>
lat - Lattitude</br>
long - Longitude</br>
sqft_living15 - The square footage of interior housing living space for the nearest 15 neighbors</br>
sqft_lot15 - The square footage of the land lots of the nearest 15 neighbors</br>

 **Target**</br>

The target column that I would like to predict is the price of a house. </br>

**Distribution of target values (price) in this dataset**</br>
![histogram price](https://user-images.githubusercontent.com/82225286/165817872-555c883f-5c58-4521-ae9a-dd07c0d9e0c4.png)

### Initial Data Analysis</br>

I think the important columns to explore through further analysis include the sqft of living space, number of bathrooms, building grade, and the sqft of surrounding homes which will indicate the size of homes in the neighborhood. Based on this heatmap, it seems these are all likely strong indicators. </br>

![heatmap](https://user-images.githubusercontent.com/82225286/167062443-5f02582c-cd37-4d64-bb7d-309190b2a448.png)</br>


After splitting the date out into months and aggregating the price to an average price per sq foot, it seems that seasons/months where the weather is subjectively "nice" (spring and fall) such as March/April, and September/October have slightly higher average price per sq foot, so this may be another connection to look into.</br>

![month](https://user-images.githubusercontent.com/82225286/165663010-54d14d49-e468-4395-af88-70e556e82814.png)

This plot shows a relationship between price and sq ft of living space that is also somewhat related to the building grade. </br>

![grade](https://user-images.githubusercontent.com/82225286/165664848-9d7f2ecc-bef0-4588-ad73-dbf6ecc61987.png)

Number of bathrooms also shows a general relationship with the price. </br>

![bathrooms](https://user-images.githubusercontent.com/82225286/165665239-9cfe2e64-f8c8-409e-873e-cb9470bd4938.png)

I've also created some aggregate columns such as average price per square foot of a house based on the number of bathrooms, average price per square foot based on the age, and the average sale price per month. After some trial and error, I also added an aggregate column for average price by zipcode. This caused the Rsquared score to go up by about 5%


## Part 2: Training </br>
For this dataset, I am aiming for regression and implemented the sklearn linear regression model and the SGD regression model.

## Part 3: Post Model Analysis </br>
After adjusting various aggregate columns as mentioned earlier, I was able to get a score of 0.825 for the linear regression model and 0.833 for the SGD regression model. </br> 

**Residuals for Linear Regression Model**</br>
![linear residuals](https://user-images.githubusercontent.com/82225286/167061777-03eaa6f0-2170-4acd-879f-d9ad8e121c11.png)</br>
**Residuals for SGD Regression Model**</br>
![sgd residuals](https://user-images.githubusercontent.com/82225286/167061827-77ed031c-4273-4ac9-9520-089020cfca94.png)</br>
 The residual plots seem to show that the higher the price gets, the less accurate the model is in predicting the price. The residuals are both very similar for the SGD and the linear regression.</br>
**Plot of Actual Price vs Predicted Price using SGD Regression Model** </br>
![sgd actual y vs predicted y](https://user-images.githubusercontent.com/82225286/167061907-2eff712b-1a9b-4172-aa79-d6e9591c07a7.png) </br>
When adjusting the test size, the scores do change as well. Overall, it is slightly less accurate the larger the test size is and therefore the smaller the training sample is. I think it does not have a very big effect because the dataset is rather large. Even at 90% test size, there are still 2000+ data points to train on.</br>
**Plot of test size vs score** </br>

![accuracy](https://user-images.githubusercontent.com/82225286/167063729-2162d213-7dcc-456c-997b-9e88e78c0f09.png)

## Conclusion</br> 
Both of these regression models worked quite well for this dataset. The data was rather clean to begin with and required very little imputing, encoding. or dropping of null values. Adding aggregate columns definitely increased the accuracy of the model. If I had to choose, I would choose the SGD regression simply because it did score slightly higher.


