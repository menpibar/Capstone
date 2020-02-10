   This repository has been made for the coursera Data Science course. In the last course, they ask to create and complete a project based on real world data.
   # Where to start
## Introduction
  My project consist on a program that will determine which neighbourhood is the best suitable for opening a new store, shop, restaurant or similar businesses in the city of Toronto. However, for this project I will search the best neighbourhood for opening a bank office. Toronto is the financial capital of Canada, therefore there is a lot of presence of big banks. In this project, I will emulate that I am working for a small bank -DataBank- that wants to open an office in Toronto. The results obtained will help the small bank to decide where to open and which are the main competitors. However, as I said, the aim of this project is to adapt it to any businesses, therefore, results will change depending on which category of business we want to open, obviously. \
  When we are opening a business -our bank office-, we do not want to do it so in a very saturated area in which the competition is very high. Nevertheless, we also do not want to open it on an area in which there are any similar businesses -meaning that in such area there not exist potential demand. Therefore, we would want to open it in an area in which the saturation of similar businesses is near the average.\
  Following that reasoning, this project will analyse the neighbourhoods of Toronto to determine which areas does not have a lot of competition but are equally suitable to open a specific type of business.
## Data
This project was conceived as the continuity of the previous module. Therefore, the sources of data I am going to use are:
  - For the neighbourhood locations, the Wikipedia page https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M
  - For the venues, the Foursquare API
  - For creating maps, Folium library
  - For geospatial data, the csv file of Module 3 https://cocl.us/Geospatial_data
## Methodology
### Data wrangling
First and foremost, I imported the necessary libraries to operate throughout all the project on a Jupyter notebook. As I said in the data section, I took the data of the neighbourhoods of Toronto from the Wikipedia website. Then, I procceded to create a dataframe in pandas with the names of the neighbourhoods. After that, I dropped all the not assigned values.\
From the csv file of Module 3, I took the geospatial data of the neighbourhoods of the previous dataframe and created a new dataframe. Then I merged both datasets in an unique one.
#### Map preparation
Using Folium I created a map for Toronto. I looked for the coordinates in the internet. Then I added markers representing all the neighbourhoods on it.
### Using the Foursquare API
I searched for my Foursquare credentials created in previous weeks. Then I wanted to test my dataset with the API so I did a request for only one neighbourhood location. It returned me some venues as expected, so I procceded to define a function to get all the venues of all the eighbourhoods in the dataset.\
I got a big dataframe of shape (9935, 7). That was because a lot of values were duplicated, as some neighbourhoods locations are near each other. So I dropped all the duplicated values, resulting in a dataframe  of shape (801,7). That means that in Toronto there are 801 distinct bank offices, according to Foursquare. I added markers for each venue to the map I prepared before. The map can be seen in the code of the Jupyter notebook.\
## Results
### Businesses per neighbourhood
Then, I wanted to analyse the data to see how many similar bank offices each neighbourhood had. In this way, I could determine which neighbourhoods had the best density of offices to open a new one.\
I plotted a boxplot chart to visualize the distribution of the data. This chart can be seen in the lines of code. There was only an extreme value at 20 offices in the neighbourhood. I looked then for the mean of businesses per neighbourhood, and it was 5. The mean was the target of my project, as the neighbourhoods that had that density were nor very saturated nor empty. I searched for the venues with that number of offices. They were 7:    
- Clairlea,Golden Mile,Oakridge
- Deer Park,Forest Hill SE,Rathnelly,South Hill,...
- Downsview West
- Downsview,North Park,Upwood Park
- Rosedale
- Woburn
- Woodbine Gardens,Parkview Hill
