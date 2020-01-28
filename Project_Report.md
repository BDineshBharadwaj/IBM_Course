## The Clustering of Hotels based on their proximity to Food places
### Introduction/Business Problem
As someone who regularly uses hotel services on my trips, my choice of a hotel has always been dependant mostly on the availability of places to eat food and food delivery options in the proximity of my hotel. Given, I don't always get to stay at one locality or one hotel everytime i visit a city, I can really use an analysis that clusters together the hotels of a city based on the type of food available closeby. That forms the essense of my project. 
In the project, i shall be working on a city i visit frequently, Hyderabad (India) and use Foursquare data in identifying its hotels as well as the food places that surround them to obtain the data I need. I shall then, Identify the most popular types of food that are available nearby and use that data to cluster similar hotels. I shall be using Kmeans clustering for the project.
### Data
The first set of Data will be collecting the list of hotels in Hyderabad. For convenience, I'll be selecting the hotels managed by the hotel chain "OYO". The cleaned up Data should have the following columns. 

"Hotel_Name"  "Latitude"  "Longitude" "Rating"

The rating although will not be a part of the clustering, it can help in selection and will be used in visualization to see highlight best rated hotels.

The second set shall be list of food places within 1500 meters of each hotel. The list will be analysed to arrive at the number of places that serve different cuisines. (The list of Cuisines shall be the top ten popular cuisines in the city). The cleaned up data should look similar to the following

"Hotel_Name"  "Cuisine A"  "Cuisine B"  "Cuisine C"  "Cuisine D" .....

   Hotel_1         Score1A        Score1B        Score1C         Score1D  ......

   Hotel_2         Score2A        Score2B        Score2C         Score2D  ......
   
The score for every Hotel-Cuisine pair shall be based on the frequency and ratings of the Cuisine in the hotel proximity.
The above data shall be used to cluster Hotels using Kmeans algorithm.
