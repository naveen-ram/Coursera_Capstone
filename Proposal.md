# Predicting the Best Location for a Restaurant in Boston
* Naveen Ram *
* November 9, 2019 *

### 1. Introduction

#### 1.1 Background

When retirees are charged with choosing a place to live in retirement, it is not an easy decision to make. There are so many different options especially in the US. On top of that, you might be used to a certain way of living, so maybe you want to go somewhere that is familiar. There are a number of options with many being located in Florida, but could there be places that might be better to live in because it is easier to live in? One of the more recent trends is gaining financial independence and retiring early. With an early retirement, this opens up more options than just Texas, Florida, and other warm weather states. Thus I propose further research into what cities are similar and dissimilar. 

#### 1.2 Problem

Retirees have so many options for retirement, especially for those in early retirement. Choosing the right city to settle down in is extremely important to having a peaceful retirement. This presents a problem to retirees because of the sheer number of cities to choose from. I want to make it easy for those people who are choosing by allowing them to enter a city of their choice, and provide multiple suggestion of similar cities that might also be a good idea for retirement. They could even put in the current city they are in, and they will get a list of the cities most similar to that. Thus, this will narrow their list of cities to consider considerably. Allowing for a smoother transition to retirement. 

#### 1.3 Interest

### 2. Data sources, acquisition, and cleaning

#### 2.1 Data sources

The data sources for this project are two-fold. I will be using the Foursquare API to get an understanding of attractions and ameneties around a certain city as well as the weather API to get average weather data for a region. This information will be extracted from a dataset from wikipedia of 314 of the most populous cities in America. Although this may have bias to states that are more populous, I think it will have a good representation of cities that retirees will be interested in. Using this list of cities I will then get the latitude and longitude data for the cities based on the center of the city. I will get this information using the geopy.geocoders API in python. I will then use this to get information from the Foursquare and weather API. This data will then go through cleaning and feature selection and then will be clustered using the k-means algorithm with k set to 10. 


#### 2.2 Data acquisition

Data will be acquired from multiple sources. The main dataset being used in this project comes from Wikipedia.com. It consists of 314 of the most populous cities in the US. This data will be used to acquire 3 additional data. First, it will be used to get geolocation data, longitude and latitude, using the geopy.geocoders API in python. Secondly, it will be used to get data from the Foursquare API. This will provide information about all the ameneties and attractions in each city within a specified radius to the location data. Lastly, the location data will be used to get average temperature data from the weather API. All of this information will be stored in a pandas DataFrame. The next step will be to clean the data from this DataFrame. 

#### 2.3 Data cleaning

This step involves keep good information and getting rid of useless information. In our case the only fields we care about from the wikipedia table are the city and state information. So, we will clear out the columns of useless information. Additionally, we will need to move the data around so that the city becomes the first column of the data. We can even combine the city and state data into one column with the state being converted to its two letter abbreviation. This will allow the other steps to be much easier. We will have to look at all the amenety and attraction info to see what is useful and what isn't. Based on this get rid of the 10 least popular ameneties in each of the regions then take the mean of the counts. This allows us to work with normalized data. 

#### 2.4 Feature Selection

### 3. Exploratory Data Analysis
### 4. Prediction and Analysis
### 5. Conclusion and Discussion