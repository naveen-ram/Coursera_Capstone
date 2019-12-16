# Predicting the Best Location for a Restaurant in Boston
*Naveen Ram*
*November 9, 2019*

### 1. Introduction

#### 1.1 Background

When retirees are charged with choosing a place to live in retirement, it is not an easy decision to make. There are so many different options especially in the US. On top of that, you might be used to a certain way of living, so maybe you want to go somewhere that is familiar. There are a number of options with many being located in Florida, but could there be places that might be better to live in because it is easier to live in? One of the more recent trends is gaining financial independence and retiring early. With an early retirement, this opens up more options than just Texas, Florida, and other warm weather states. Thus I propose further research into what cities are similar and dissimilar.

#### 1.2 Problem

Retirees have so many options for retirement, especially for those in early retirement. Choosing the right city to settle down in is extremely important to having a peaceful retirement. This presents a problem to retirees because of the sheer number of cities to choose from. I want to make it easy for those people who are choosing by allowing them to enter a city of their choice, and provide multiple suggestion of similar cities that might also be a good idea for retirement. They could even put in the current city they are in, and they will get a list of the cities most similar to that. Thus, this will narrow their list of cities to consider considerably. Allowing for a smoother transition to retirement.

#### 1.3 Interest

The interest in the project comes mainly from those people that are looking to move from where they currently live to somewhere similar to where they live or similar to a different city. Mainly the interest in project would come from retirees looking to start retirement in a city of their choice. This project allows them to narrow their search, and as a result it will be of interest to them.

### 2. Data sources, acquisition, and cleaning

#### 2.1 Data sources

The data sources for this project are two-fold. I will be using the Foursquare API to get an understanding of attractions and amenities around a certain city as well as the weather API to get average weather data for a region. This information will be extracted from a dataset from Wikipedia of 314 of the most populous cities in America. Although this may have bias to states that are more populous, I think it will have a good representation of cities that retirees will be interested in. Using this list of cities I will then get the latitude and longitude data for the cities based on the center of the city. I will get this information using the geopy.geocoders API in python. I will then use this to get information from the Foursquare and weather API. This data will then go through cleaning and feature selection and then will be clustered using the k-means algorithm with k set to 10.


#### 2.2 Data acquisition

Data will be acquired from multiple sources. The main dataset being used in this project comes from Wikipedia.com. It consists of 314 of the most populous cities in the US. This data will be used to acquire 3 additional data. First, it will be used to get geolocation data, longitude and latitude, using the geopy.geocoders API in python. Secondly, it will be used to get data from the Foursquare API. This will provide information about all the amenities and attractions in each city within a specified radius to the location data. Lastly, the location data will be used to get average temperature data from the weather API. All of this information will be stored in a pandas Data Frame. The next step will be to clean the data from this Data Frame.

#### 2.3 Data cleaning

This step involves keep good information and getting rid of useless information. In our case the only fields we care about from the Wikipedia table are the city and state information. So, we will clear out the columns of useless information. Additionally, we will need to move the data around so that the city becomes the first column of the data. We can even combine the city and state data into one column with the state being converted to its two letter abbreviation. This will allow the other steps to be much easier. We will have to look at all the amenity and attraction info to see what is useful and what isn't. Based on this get rid of the 10 least popular amenities in each of the regions then take the mean of the counts. This allows us to work with normalized data.

### 3. Exploratory Data Analysis

### 4. Prediction

#### 4.1 Models

Once the data was in the proper format, I removed the column that said what the location was and passed the rest of the data into a K-means clustering model. This model comes from the Sci-py machine learning package. The model allows me to group the data based on the spatial location of the data. Based on the k value I inputted the output would create k centroids that the data would then cluster around and repeatedly update until each of the points is in a cluster group. For my model, I used a k value of 40. As the dataset size was so large, 314 cities, the output of each cluster was too large at small k values. As I increased the k values, there were some labels that only had a few cities in it, so I went through and removed all the data from the labels that had less than 5 cities in it. As a result, I was able to cluster in a way that there was a good amount of cities in the remaining labels, not too many or few.

### 5. Results

The output of the k means algorithm shows us the different groups of the cities. This is based on the data that was passed in to the algorithm. Using the means of the amenities and attractions nearby as well as the population. When a city is used, the clustering algorithm will provide at least 4 other city suggestions that are similar to the city. For example, if you take Miami for example, the other cities in that cluster from the output were Colorado Springs, CO, Long Beach, CA, Omaha,NE, Raleigh, NC, and Virginia Beach, VA. These cities were the most similar to the attractions and amenities to Miami. Similarly, we can do this for the other 313 cities in the dataset.

### 6. Discussion

This study is clearly showing that the US cities can be separated and grouped based on what types of amenities are available nearby. As a result, we are able to use this information to take informed and calculated decisions when moving to a new city. The results of this study allow the user to choose a place similar to the one they are currently in or a city of their choice. It reduces the options to a select few cities, where the largest group has 36 cities to choose, a big step down from 314 in the original dataset. However, amenities and population are not the only factors when choosing a new place to live. As a result, the reliability of this information is not complete. Future work with this project would include adding additional information from cities such as demographic data, weather data, traffic data, geographical data, and others to the feature set of each city. This will provide better, more predictive features that can be used for clustering the data. With more information, there is also the tradeoff of choosing the right features, so that would be something to keep in mind when adding more features.

### 7. Conclusion

In conclusion, this project answers the question, can we help people, retirees in particular, in choosing a place to move? Can we narrow down the search of cities to move to? Can we suggest a place that would allow them to have a similar life to that which they are having now? All of these questions can be answered through the output of our clustering algorithm. However, since the training dataset is not complete with all the most predictive features, the predictions are not completely reliable. However, the investigation into these questions has allowed us to provide an answer that can be used. 
