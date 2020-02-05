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

### Supplemental Question 1 - Which Zip Codes had the best Average Price per Square Foot and Variance of prices?


### Supplemental Question 2 - Which Zip Codes had the best Walk Score (Mark is interested in being able to get around easily without a personal vehicle)?


### Supplemental Question 3 - Which Zip Codes had the best Average Rating of nearby restaurants?
Using the Google Places API, all 25 zip codes in the original list were analyzed to find restaurants within 5000 meters and average and aggregate their google ratings into one value per zip code. A heat map was also created for both average rating and price (though price was not used in the final calculation of the Mark Score)
Price Heatmap:
![Price Heatmap](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/price_heatmap.png)
Rating Heatmap:
![Rating Heatmap](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/rating_heatmap.png)


### Supplemental Question 4 - Which Zip Codes have the lowest Crime Ratings (total, non-violent, and violent)?

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