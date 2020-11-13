# Coursera - IBM Data Science Professional Certification Capstone Project
I designed this project to satisfy the final requirements for the IBM data science certification. The goal was to determine the best possible route for a bar crawl, in Houston, TX, based on 4 custom scoring functions including desired number of locations, price range, venue ratings and walking distance.

## 1. Introduction
Pub crawls are a commonly performed ritual where a group of people tours an area by visiting multiple pubs, or bars, in one night while having at least one drink in each establishment. A well designed crawl will result in a good time had by all and the discovery of new favorite spots in your chosen city.

To build the optimum crawl, you will need to consider the type of bars you would like to visit, the distance between each location, the price range, and whether each location is worth the time being spent there. In order to determine the optimum pub crawl for my city, Houston, TX, we will look at "best bang for your buck" while plotting a route that is easily walkable in one evening.

This ability to design an optimum route for a given city based on adjustable parameters would be of value to anyone trying to organize a fun group outing.

## 2. Data
All of the city information can be found in an ArcGIS system maintained by the city of Houston and available for public use. This is used to define the neighborhoods in the same way that the city does. The venue listings and information (location, price, rating, name, venue type) are all drawn from FourSquare. The number of neighboorhoods included were limited based on their distance from Downtown Houston, to narrow the number of venues included. Based on this, basic Foursquare data was pulled for venues within 1 km of the center of each neighborgood. Once this information was obtained, it was combined into a DataFrame consisting of location and category information. The locations neghborhoods without any venues or enough venues to properly cluster were eliminated.

The venues that appeared to fit the requirements for proximity within a neighborhood were then sent to Foursquare to request more detailed information. This information was then purged of all redundancies and prepared for analysis. These preparations included filling in missing data with appropriate category-median data and eliminating any venues that did not fit the chosen parameters.

## 3. Methodology
Location venues were clustered using Density-based spatial clustering of applications with noise (DBSCAN) to determine location groupings. Outliers were removed and detailed ingfomation was pulled from Foursquare to find the price, ratings, and likes. These were then cross-referenced between cluster and venue type to anaylize the corrolation between Cluster, category, rating, likes and price.

This data was then used to create a predictive value model using KNN to predict missing information at each venue. These cluster scores allowed most of the neighborhoods to be eliminated at this point. The neighborhood groups that remained coincided with local information pertaining to the value of each respective areas' nightlife.

The remaining neighborhoods were ranked based on the number of venues available that fit the initial criteria in order to remove any outliers. These were then grouped by quality, as determined by likes and ratings3. The clusters were ranked and an optimum chosen based on the weighting chosen at the outset.

The chosen "top cluster" was then investigated to determine which venues most worth the time of viewing, and these rankings were used to plot the best group for the actual crawl. Unfortunately, I did have to resort to manual choosing the order of the chosen venues to create the best walkable route.

## 4. Results

#### Neighborhoods chosen for examination
![Neighborhoods of Choice](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture1.png)

#### Correlation of venue information
![Venue Correlation](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture12.png)

#### Frequency of category in each pricing bracket
![Category Frequence](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture2.png)

#### Frequency of category in each pricing bracket
![Category Frequence](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture3.png)

#### Clustered venues chosen
![Venue Clusters](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture4.png)

#### Venue Count by Cluster
![Venue Count by Cluster](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture5.png)

#### Distribution of Venue Ratings in each cluster
![Venue Rating Distribution](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture6.png)

#### Distribution of Venue Likes in each cluster
![Venue Likes Distribution](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture7.png)

#### Ranking Scores by cluster
![Ranking Scores by cluster](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture8.png)

#### Automatically determined route
![Automatic Route](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture9.png)

#### Manually determined route
![Manual Route](https://github.com/wiley0210/Quantitatively-Optimum-Houston-Pub-Crawl/blob/master/Crawl%20Result%20Photos/Picture11.png)

## 5. Discussion
This analysis displayed many shortcomings that could be overcome through a premium data connection with Foursquare that would allow for all venues in the neighborhoods to be chosen, rather than just the ones that are closest to the center. However, it did determine which neighborhoods had the best clustering of nightlife locations. This was very important for validation of the model, because it matched the conventional wisdom of people who live in Houston.

## 6. Conclusion
This data shows the foundation of a systematic method for determining routes for groups to explore new cities and warrants further investigation to determine the possibility of application developement.
