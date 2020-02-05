# DU-Analytics-Project-1
Find Mark a House!

## Team Study Buddies
Nate Crawford
Mark Medernach
Nolan Goodweiler
Sam Rotbart

## Overall Question - Which Zip Code is the most promising of the Zip Codes that Mark is looking at to purchase a home?
The overall top 5 Zip Codes, using the Mark Score (explained in a supplemental question below) were:
80401
80002
80211
80212
80204
![Final Mark Score](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/mark_score_final_values.PNG)
From these 5 Zip Codes, an API call can be used to find specific houses that are within our parameters.


### Supplemental Question 1 - Which Zip Codes had the best Average Price per Square Foot and Variance of prices?
An API call was used to get 200 houses from each of the top 25 zip codes Mar has been searching for a home, for both the 200 most recently sold properities and pthose recently put up for sale. Box plots were then created for both the for sale and sold dataframe on their Average Price per Square Foot values to see the statistical values (average, quartiles, and outliers) within the zip codes. These boxplots helped create a visual of which may be the most desirable zip codes, but only looked at the prices rather than all of the categories we are analyzing.  We also output dataframes for use in the Mark Score below.
For Sale Boxplot:
![For Sale Boxplot](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/for_sale_boxplot.png)
Sold Boxplot:
![Sold Boxplot](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/sold_boxplot.png)

### Supplemental Question 2 - Which Zip Codes had the best Walk Score (Mark is interested in being able to get around easily without a personal vehicle)?
Another API was used to get a single walk score by zip code based on the latitude/longitude for each. We used a centralized zip code database to find the central lat/long for each and determine an average walkscore for each Zip Code. A heatmap was generated as well as pushing the data out as a csv for dataframe usage and the Mark Score calculation.  
Walk Score Heatmap:
![Walk Score Heatmap](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/walkscore_heatmap.png)

### Supplemental Question 3 - Which Zip Codes had the best Average Rating of nearby restaurants?
Using the Google Places API, all 25 zip codes in the original list were analyzed to find restaurants within 5000 meters, average and aggregate their google ratings into one value per zip code. A heat map was also created for both average rating and price (though price was not used in the final calculation of the Mark Score).  Final rating per zip code was exported for use in the Mark Score below. 
Price Heatmap:
![Price Heatmap](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/price_heatmap.png)
Rating Heatmap:
![Rating Heatmap](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/rating_heatmap.png)


### Supplemental Question 4 - Which Zip Codes have the lowest Crime Ratings (total, non-violent, and violent)?
Individual crimes were collected as a csv from the internet for the Denver Police Department. https://www.denvergov.org/opendata/dataset/city-and-county-of-denver-crime This data did not have zip codes, so a geocoding application was used to reverse find the zip code based on the crime's latitude and longitude. This process took a long time to run through each crime (over 300,000 data points) so an initial Mark Score was used to get our top 5 zip codes without incorporating the crime rating. After getting the zip codes to analyze, the data was split into either non-violent or violent crimes based on the crime type (aggravated assault, arson, sexual assault, murder, and robery for violent and everything else in non-violent). These results were aggregated to give total number of non-violent and violent crimes grouped by zip code in a dataframe. Bar charts were then created to visualize the number of crimes in each zip code and a couple of samples are below (see the repo for images for each of the zip codes).
80204 Non-Violent Crimes
![80204 Non-Violent Crimes](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/Non%20Violent%20Crime%20in%2080204.png)
80204 Violent Crimes
![80204 Violent Crimes](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/Violent%20Crime%20in%2080204.png)

### Supplemental Question 5 - How do we create a system to rank each Zip Code using price, walk score, restaurant ratings, and crime ratings when these are all unrelated to each other?
Given that we had numerical values for each of the 5 major categories (price per square foot, variance, walk score, restaurant ratings, and crime ratings), we decided that with some weighting we can create a formula to give one final score for each zip code, hence the Mark Score.
The values before factors and weighting are below:
![Final Mark Score Individual Values](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/mark_score_ind_values.PNG)

We first used different factors to get all of the values to a reasonably similar magintude and range of values, as well as make the Average Price per Sq Ft and Crime Scores negative, as we want the lowest values for them in the final equation. The weights were then agreed upon by the entire group to make sure that each category was being factored in correctly based on their final individual values. The final factors used were:

Average Price per Square Foot (APSF): 1.0
Variance (Var): 2.5
Walk Score (WS): 0.5
Restaurant Ratings (ARR): 0.2
Crime Rating (CS): 0.15

Mark Score = APSF*APSF_Factor*APSF_Wt + etc.

This returned the table below:
![Final Mark Score Values](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/mark_score_final_values.PNG)
This not only gave the group the top 5 zip codes, but allowed us to make another heatmap of the Mark Scores for the final 5 zip codes:
![Final Mark Score Heatmap](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/final_score_heatmap.png)

Using the final 5 zip codes, we narrowed down the results by an overall price range, desired bedrooms, bathrooms, etc.  to create a view of listings in the most desirable zip codes within Mark's budget and with his preferences.  We created an interactive scatter plot with the results to show basic information of the various listings that meet Mark's critera.  

### Final Question – What houses should Mark look to purchase?

The final stage of our project was to plot the available houses in the final 5 zip codes we had identified. We used an additional set of filters to determine the list of houses with characteristics Mark is looking for in a home (beds, baths, price). With this final list of homes we created an interactive plotly.express scatter plot. The interactive plot allows us to hover over each of the data points and find the final list of houses Mark should go visit.

Using the plotly scatter plot, we narrowed the search down to three final houses. These houses were all within Mark’s price range and had a larger square footage than the other houses in the zip codes we analyzed. Unfortunately, due to the Denver Real Estate market, we are going to have to rerun our analysis since all of the homes we identified for Mark are now under contract!
