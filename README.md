
# Wine Analysis

<p align="left">
  <img width="320" height="200" src="/img/wine.png">
</p>

## 1. Purpose of analysis
A group of wine appraiser requested an data analysis to see what the distribution of wine types around the world is based on score and price.
From this analysis, it was possible to verify the best cost-benefit and the location of the best wines for this group to plan their travel itinerary.

 

## 2. Data collecting

The presented scenario of the proposal has as data sources the files in .csv format available in Kaggle. It is possible to access the wine data source by clicking [here](https://www.kaggle.com/datasets/zynicide/wine-reviews) and the location used is [GPS coordinates for every world country and every USA state](https://www.kaggle.com/datasets/paultimothymooney/latitude-and-longitude-for-every-country-and-state).

## 3. EDA
### 3.1 Data treatment

Numerical variables were analyzed to verify data distribution, deviation of points and price around the mean and outliers. Thus, filling in the missing data of the points was used the mean because the distribution of the data looks like a normal distribution.

| Variables | Max    | Min  |	Mean  | Median | Std	 | Skew  | Kutosis |
| :---      | :---   | :--- | :---  | :---   | :---  | :---  | :---    |
| Price     |	3300.0 | 4.0	| 35.36 | 25.0   | 41.02 | 18.00 | 829.52  |
| Points    | 100.0  | 80.0	| 88.45 |	88.0   | 3.04	 | 0.05	 | -0.30   |

<p align="left">
  <img width="500" height="250" src="/img/hist_points.png">  <img width="500" height="250" src="/img/hist_price.png">
</p>


For the categorical variables, some terms were verified in the 'description' feature to know some flavors of the types of wine and the quantities. Most of the missing categorical data was filled in as 'Unknown'. For the 'variety' feature, a more careful analysis was performed, as it was only 1 data, to be filled in based on similar characteristics of the wines.

In the image below it is possible to verify 3 flavors requested by the group, the Citrus flavor appears in more than 12k types of wine, being almost 10% of the dataset:

<p align="left">
  <img width="650" height="300" src="/img/type_taste.png">  
</p>

### 3.2 Hyphotesis
An exploratory analysis of the data was carried out to understand how the wines are distributed in relation to their locations, points, price, description, winery, etc. The group raised some hypotheses based on their previous experiences, to validate or invalidate these hypotheses, tests and analyzes were carried out to verify if the statements are true or false.

**H1. Testing if the mean of points from Portugal is the same general mean of 88.45 points:**

False. A one-sample statistical test was applied, testing whether the sample mean (Portugal) is equal to an ideal mean (general mean). The result showed that there is less than a 5% chance of the result being random, so the hypothesis that the average points of the Portuguese wine is the same as the general average of points is rejected.

**H2. Most of the evaluated wines are from France:**

False. Checking the number of wines evaluated in each country, most are in the US and France is in second position.
![Image](/img/wines_eval_country.png)

**H3. Few wines have no Taster rating:**

False. Most of the wines do not have a known taster on the list, the majority being concentrated on "Unknown", the name chosen to fill in the missing data.
![Image](/img/taster.png)

**H4. The highest scoring Merlot is from Italy:**

True. The highest-scoring Merlot type is in Italy.
![Image](/img/best_merlot.png)


**H5. The most expensive wines on average are from France:**

False. The most expensive wines on average are in Switzerland. France is in 5th position.
![Image](/img/price.png)

**H6. Chardonnay are more expensive than Muscat:**

True. Chardonnay wines are on average more expensive than Muscat.
![Image](/img/chardo_muscat.png)

**H7. The best wines are concentrated in Europe.:**

False. There are 5 countries that have wines with 100 points. And 3 of them are European, but they also have Australia and US.
![Image](/img/points.png)

**H8. Roger Voss have the highest mean of the points:**

False. The taster Roger Voss has the highest number of evaluated wines, however, he does not have the highest average points and occupies the 8th position. Anne Krebiehl MW has the highest point average.
![Image](/img/points_taster.png)


## 4. Business analyses
After confirming the hypotheses, the group wanted to know more about the types of wines. Where were the best wines in terms of points, price, location and the best value for money.

- This is the more expensive wine and its characteristics:

| Variety	                 | Country |	Winery	                | Taster	   | Price	| Points |
| :---                     | :---    | :---                     | :---       | :---   | :---   | 
| Bordeaux-style Red Blend | France	 | Château les Ormes Sorbet	| Roger Voss | 3300.0	| 88     |


- These are the cheapest wines and their characteristics:

|Variety	| Country	| Winery | Taster |	Price |	Points |	Ratio |
| :---    | :---    | :---   | :---   | :---  | :---   | :---   | 
|	Merlot |	US |	Bandit	| Unknown	| 4.0 |	86 |	21.50 |
| Pinot Grigio |	Romania	| Cramele Recas	|Anna Lee C. Iijima	|4.0	|86	|21.50|
| Syrah	| Spain	| Felix Solis	|Michael Schachner	|4.0	|85	|21.25|
| White Blend	| US	| Dancing Coyote	|Jim Gordon	|4.0	|85	|21.25|
|	Malbec-Syrah	| Argentina |	Broke Ass	|Michael Schachner |	4.0 | 84	|21.00|
|	Chardonnay	| US | 	Bandit	| Unknown	|4.0	|84	|21.00|
|	Cabernet Sauvignon	| Spain |	Terrenal	|Michael Schachner	|4.0|	84	|21.00|
|	Merlot |	US	| Bandit	| Unknown	|4.0	|84	|21.00|
|	Tempranillo |	Spain	| Terrenal	| Michael Schachner	|4.0	|84	|21.00|
|	Chardonnay	| US	| Pam's Cuties |	Jim Gordon	| 4.0	|83	|20.75|
|	White Blend	| Spain |	Felix Solis	| Michael Schachner	|4.0|	82	|20.50|


- It is possible to get the best cost-benefit based on the low price and highest points: Merlot from the USA and Pinot Grigio from Romania. However, it is observed that this rate relatively has very little variation among all wines with a value of less than $4.

![Image](/img/ratio.png)

- Here are the provinces where the best wines are found. There is a wide range of prices with a low of $80 and a high of $1,500. So, it is possible to get a 100 point wine for only $80 like a Syrah from Washington (USA).

![Image](/img/best_wines.png)

- Since travelers love a map, key information has been entered into a map. For this, a dataset with the latitude and longitude coordinates of each country was added to obtain a better view of this information:
- This map shows the most expensive wines in each country, with the size of the circles representing the price and the color scale of the points:

![Image](/img/map_price_points.png)

- This map only shows the average prices of each country represented by the size of the circles and color scale:

![Image](/img/map_mean_price.png)


