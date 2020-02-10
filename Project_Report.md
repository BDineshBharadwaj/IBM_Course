## The Clustering of Hotels based on their proximity to Food places
### Introduction/Business Problem
As someone who regularly uses hotel services on my trips, my choice of a hotel has always been dependant on the availability of places to eat food and food delivery options in the proximity of my hotel. Given, I don't always get to stay at one locality or one hotel everytime i visit a city, I can really use an analysis that clusters together the hotels of a city based on the type of food available closeby. That forms the essense of my project. 
In the project, i shall be working on a city i visit frequently, Hyderabad (India) and use Foursquare data in identifying its hotels as well as the food places that surround them to obtain the data I need. I shall then, Identify the most popular types of food that are available nearby and use that data to cluster similar hotels. I shall be using Kmeans clustering for the project.
The stakeholders can use the analysis to suggest hotels to customers based on their food preferences as well as their previous stays.
### Data
The first set of Data will be collecting the list of hotels in Hyderabad, provided by Foursquare. The cleaned up Data looks like the following. 

![Sample Hotel Data from Foursquare](https://github.com/BDineshBharadwaj/IBM_Course/blob/master/DataHotel.PNG)

The second set of Data shall be list of food places within 1500 meters of each hotel. The list will be analysed to arrive at the number of places that serve different cuisines in its proximity. (The list of Cuisine types shall be the top ten popular cuisines in the country).
The list is as follows
1. South Indian
2. North Indian
3. Cafe
4. Fast food
5. Biryani
6. Pizza
7. Burger
8. Chinese
9. Bakery
10. Continental


The cleaned up data should look similar to the following.

"Hotel_Name"     "Cuisine A"     "Cuisine B"     "Cuisine C"     "Cuisine D" .....

   Hotel_1         Score1A         Score1B         Score1C         Score1D  ......

   Hotel_2         Score2A         Score2B         Score2C         Score2D  ......
   
The score for every Hotel-Cuisine pair shall be based on the frequency of the Cuisine in the hotel proximity. The  frequency will be calculated from the number of venues Foursquare outputs for a given Cuisine.
The above data shall be used to cluster Hotels using Kmeans algorithm.
## Methodology
1. The first challenge was to obtain a list of Hotels in Hyderabad. Foursquare only returns 50 venues per an API call. We need a bigger list of Hotels to work with. To facilitate this, ten localities that are evenly spaced out across hyderabad have been picked and hotels in 5 km radius of each of the locality have been obtained. Then the collection of Hotels has been checked for duplicates and a final list of 312 hotels has been obtained.
Areas chosen with their coordinates
![Area Data from Foursquare](https://github.com/BDineshBharadwaj/IBM_Course/blob/master/Areas.PNG)
top 10 of the Hotels with coordinates 
![Hotel Data from Foursquare](https://github.com/BDineshBharadwaj/IBM_Course/blob/master/Hotels.PNG)

2. The hotels have been visualized using Folium package.
![Hotel Data on map](https://github.com/BDineshBharadwaj/IBM_Course/blob/master/Map.PNG)

3. A feature set is generated using collecting the frequency of different cuisines as mentioned in the Data section. FourSquare has been used to get the data. The data has been obtained over a course of four days because of the limits to Foursquare API service.The data is stored on IBM free database. The scaled and normalized feature set is as follows.
![Featureset Data from Foursquare](https://github.com/BDineshBharadwaj/IBM_Course/blob/master/Featureset.PNG)

4. Kmeans algorithm has been used to cluster the feature set into six clusters. the algorithm is run 12 different initiations and the best set is chosen. The sklearn package is used to do the machine learning.

## Results
The distribution of Hotels among the clusters is as follows.
![Cluster numbers]()

The hotels have been clustered into six groups and the following plots are generated to visualize the clusters.
1. Bar charts with the mean of each group.
![Bar1](https://github.com/BDineshBharadwaj/IBM_Course/blob/master/Bar1.PNG)

2.
![Bar2](https://github.com/BDineshBharadwaj/IBM_Course/blob/master/Bar1.PNG)

3. The folium package is used to visualize the clusters on the map.
![hotel map clustered](https://github.com/BDineshBharadwaj/IBM_Course/blob/master/MapCluster.PNG)
 
## Discussion
From Bar1 plot from Results section, We can classify the clusters, roughly, as these categories.
1. Cluster 1 seems to have the lowest frequency of all types of cuisines in its proximity. Not recommended.
2. Cluster 2 seems to be the best spot for most cuisines except Burgers and pizza
3. Cluster 0 seems to a pretty good spot for most cuisines as well.
4. Cluster 4 and 5 are pretty much in the middle of the bar. i.e they have the almost mean frequency on all cuisines making them just okay.

From Bar2 plot from Results section, we can deduce these points.
1. Cluster 1 is clearly, the worst spot for any cuisine on the list. Not recommended.
2. Cluster 2 seems to be the best spot for South Indian food followed by cluster 0, where as cluster 1 is the worst.
3. Cluster 0 takes over cluster 2 asthe best spot to have North Indian.
4. Cafes have the same top trend as North Indian food. Cluster 0, followed by cluster 2.
5. When it comes to Fast food, Biryani, Chinese and Continental food, Cluster 2 dominates again by a higher margin followed by Cluster 0.
6. Cluster 0 wins it when it comes to Burgers and Pizza! 
7. Cluster 5 shows a high frequency for Bakery almost on par with Cluster 2.

## Conclusion
The cluster 2 hotels have the best access to all cuisines in the list, followed by cluster 0. Cluster 5 shows a good frequency of Bakeries. Thus from the battle of Neighbourhoods, we have clustered the hotels in hyderabad based.
