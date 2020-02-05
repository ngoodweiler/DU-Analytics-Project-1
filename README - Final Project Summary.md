# DU-Analytics-Project-1
Find Mark a House!

#### Team Study Buddies
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

## Supplemental Question 1 - Which Zip Codes had the best Average Price per Square Foot and Variance of prices?


## Supplemental Question 2 - Which Zip Codes had the best Walk Score (Mark is interested in being able to get around easily without a personal vehicle)?


## Supplemental Question 3 - Which Zip Codes had the best Average Rating of nearby restaurants?
Using the Google Places API, all 25 zip codes in the original list were analyzed to find restaurants within 5000 meters and average and aggregate their google ratings into one value per zip code. A heat map was also created for both average rating and price (though price was not used in the final calculation of the Mark Score)
![Price Heatmap](https://github.com/ngoodweiler/DU-Analytics-Project-1/blob/master/Images/price_heatmap.png)

## Supplemental Question 4 - Which Zip Codes have the lowest Crime Ratings (total, non-violent, and violent)?

## Supplemental Question 5 - How do we create a system to rank each Zip Code using price, walk score, restaurant ratings, and crime ratings when these are all unrelated to each other?