# Phase 1 Project

## Introduction

Congratulations on completing phase 1! In this notebook, you will complete a final project that applies your python and visualization skills to real word business data. 

## Objectives 
In this project, you will...
- Read in data that has been stored as a `json` file.
- Describe how the data is structured.
- Use Python to filter a nested data structure
- Define python functions
- Calculate descriptive statistics
- Visualize data via matplotlib


# Task: Compare New York Pizza Restaurants with Above Average and Below Average Ratings
![Pizza gif](https://media.giphy.com/media/eK1eFdpj5kMWqZ9bLJ/giphy.gif?cid=ecf05e47rkbp48nwz3za6dloo8xfwzueu0rx2vklguo7xyhu&rid=giphy.gif&ct=g)

## Business Understanding 

A client at your analytics firm is considering opening a pizza restaurant in New York City. 

They have asked you to develop a business intelligence report to fact check the following claims:
1. Your client wants to ensure they have an above average Yelp rating. They have previously owned restuarants in other cities, where a `3` was the average. They would like to know if that holds true in New York City. 
1. Your client has noticed that restaurants on yelp with a high review count seem to be quite successful. They have decided to focus on maximizing their review count which they believe will allow them to have an above average overall review. 
1. After looking at a few restaurants on Yelp, your client believes that most above average restaurants have a price point of `$$`. They are considering increasing their prices from `$` to `$$` to match the majority of above average restaurants, and would like you to find the most common price point for above average restaurants in New York City.
1. In terms of location they have been told that above average restaurants are usually further east and below average are usually further west, but that the biggest difference is whether the restaurant is on the north or south side. They would like you to determine if the data supports this claim.
1. They believe that the `10012` zipcode in New York City is the best place to open a restaurant. They wish to open a restaurant in close proximity to other highly rated restaurants, and they believe `10012` has the most in NYC.



The primary purpose of this analysis is _descriptive_, meaning your analysis should report calculated statistics such as `counts` and `mean`, and should be focused on providing a simple, factual, understanding of the data. 


## Data Understanding

You have been provided a Yelp dataset containing information about restaurants in New York City. The data is named `pizza_businesses.json` and is stored in the current working directory. You will need to load in this dataset, inspect how the data is structured, and use the provided information to fact check your client's claims. 

## Load the data

A dataset containing information about New York pizza restaurants is stored in this notebook's repository with the name `pizza_businesses.json`.

In the cell below, load the json data into a python dictionary.


```python
# Import the json python package
# YOUR CODE HERE

# Load in the data
# YOUR CODE HERE
```


```python
#__SOLUTION__
# Import the json python package
import json

# Load in the data
file = open('pizza_businesses.json', 'r')
restaurants = json.load(file)
file.close()
```

## Describe the data

Now that you've loaded in the dataset, the structure of the data should be inspected.

In the cell below, evaluate 
- The datatype of the overall dataset
- The datatype of a single observation
- The number of observations, and then
- Isolate the first observation in the dataset


```python
# Replace None with your code!

# Find the datatype for the overall dataset
dataset_type = None
# Find the datatype for a single observation
observation_type = None
# How many observations are there
num_observations = None
# Isolate the first observation
first_observation = None
```


```python
#__SOLUTION__
# Find the datatype for the overall dataset
dataset_type = type(restaurants)
# Find the datatype for a single observation
observation_type = type(restaurants[0])
# How many observations are there
num_observations = len(restaurants)
# Isolate the first observation
first_observation = restaurants[0]
```

Run this following cell unchanged to print out descriptive information for the dataset!


```python
from pprint import pprint

print(f'The dataset is a \033[1m{dataset_type}\033[0m')
print(f'The observations are a \033[1m{observation_type}\033[0m',)
print(f'There are \033[1m{num_observations} observations.\033[0m')
print('\033[1m\nThe first observation:\033[0m')
print('==========================================')
pprint(first_observation)
print('==========================================')
```

    The dataset is a [1m<class 'list'>[0m
    The observations are a [1m<class 'dict'>[0m
    There are [1m1000 observations.[0m
    [1m
    The first observation:[0m
    ==========================================
    {'latitude': 40.72308755605564,
     'location': {'address1': '27 Prince St',
                  'address2': None,
                  'address3': '',
                  'city': 'New York',
                  'country': 'US',
                  'display_address': ['27 Prince St', 'New York, NY 10012'],
                  'state': 'NY',
                  'zip_code': '10012'},
     'longitude': -73.99453001177575,
     'name': 'Prince Street Pizza',
     'phone': '+12129664100',
     'price': '\\$',
     'rating': 4.5,
     'review_count': 3976,
     'transactions': ['delivery', 'pickup']}
    ==========================================



```python
#__SOLUTION__
from pprint import pprint

print(f'The dataset is a \033[1m{dataset_type}\033[0m')
print(f'The observations are a \033[1m{observation_type}\033[0m',)
print(f'There are \033[1m{num_observations} observations.\033[0m')
print('\033[1m\nThe first observation:\033[0m')
print('==========================================')
pprint(first_observation)
print('==========================================')
```

    The dataset is a [1m<class 'list'>[0m
    The observations are a [1m<class 'dict'>[0m
    There are [1m1000 observations.[0m
    [1m
    The first observation:[0m
    ==========================================
    {'latitude': 40.72308755605564,
     'location': {'address1': '27 Prince St',
                  'address2': None,
                  'address3': '',
                  'city': 'New York',
                  'country': 'US',
                  'display_address': ['27 Prince St', 'New York, NY 10012'],
                  'state': 'NY',
                  'zip_code': '10012'},
     'longitude': -73.99453001177575,
     'name': 'Prince Street Pizza',
     'phone': '+12129664100',
     'price': '\\$',
     'rating': 4.5,
     'review_count': 3976,
     'transactions': ['delivery', 'pickup']}
    ==========================================


## Find the possible rating options. 

In the cell below, create a variable called `rating_options` that has a [set datatype](https://realpython.com/python-sets/), and is a unique collection of the possible ratings a restaurant can recieve.


```python
# Create the `rating_options` variable
rating_options = None

# Loop over all of the observations in the dataset


    # Isolate the rating for the restaurant
    # YOUR CODE HERE
    
    # Add the rating for to 
    # the `rating_options` variable
    # YOUR CODE HERE
    
rating_options
```


```python
#__SOLUTION__
# Create the `rating_options` variable
rating_options = set()

# Loop over all of the observations in the dataset
for restaurant in restaurants:
    # Isolate the rating for the restaurant
    rating = restaurant['rating']
    # Add the rating for to 
    # the `rating_options` variable
    rating_options.add(rating)
    
rating_options
```




    {1.0, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0}



Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(rating_options) == set
assert len(rating_options) == 8
assert list(rating_options)[0] != list(rating_options)[1]
```


```python
#__SOLUTION__
assert type(rating_options) == set
assert len(rating_options) == 8
assert list(rating_options)[0] != list(rating_options)[1]
```

## Plot the distribution for ratings

Now that you know what rating options are available, in the cell below plot a histogram showing the distribution of ratings. 


```python
# Import matplotlib's pyplot module

# Create an empty list.
# We will store all ratings in this list
ratings = None

# Loop over every restaurant in the dataset
# YOUR CODE HERE

    # Isolate the rating
    # YOUR CODE HERE
    # Append the rating to the `ratings` list
    # YOUR CODE HERE

# Create a matplotlib subplot
# YOUR CODE HERE

# Plot a histogram of the ratings list
# YOUR CODE HERE
```


```python
#__SOLUTION__
# Import matplotlib's pyplot module
import matplotlib.pyplot as plt

# Create an empty list.
# We will store all ratings in this list
ratings = []

# Loop over every restaurant in the dataset
for restaurant in restaurants:
    # Isolate the rating
    rating = restaurant['rating']
    # Append the rating to the `ratings` list
    ratings.append(rating)

# Create a matplotlib subplot
fig, ax = plt.subplots(figsize=(15,6))
# Plot a histogram of the ratings list
ax.hist(ratings);
```


    
![png](README_files/README_18_0.png)
    


**Interpret the ratings histogram. How does the visualization relate to your client's claims?**

==SOLUTION==

The `ratings` histogram shows us that Yelp ratings are centered around `4.0` and the majority of restaurants have a rating between `3.5` and `4.5`. 

This visualization disproves my clients belief that the average rating for an NYC pizza restaurant is `3.0`. In fact, a restaurant with a `3.0` rating is quite low!

## Isolate the restaurants with an above average rating

Now that you have an understanding for what is an average rating, next you will isolate restaurants with above average and below average ratings so you can compare them.

In the cell below, filter out all restaurants that do not have a rating of at least `4.5`.


```python
# Create an empty list
# You will store restaurants in this list
above_average = None

# Loop over the dataset
# YOUR CODE HERE

    # Isolate the rating
    # YOUR CODE HERE
    
    # Check if the rating is at least 4.5
    # YOUR CODE HERE
        # If the rating is at least 4.5
        # Add the restaurant to the list
        # YOUR CODE HERE
```


```python
#__SOLUTION__
# Create an empty list
# You will store restaurants in this list
above_average = []

# Loop over the restaurants in the dataset
for restaurant in restaurants:
    # Isolate the rating
    rating = restaurant['rating']
    # Check if the rating is at least 4.5
    if rating >= 4.5:
        # If the rating is at least 4.5
        # Add the restaurant to the list
        above_average.append(restaurant)
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(above_average) == list
assert type(above_average[0]) == dict
assert len(above_average) == 306
```


```python
#__SOLUTION__
assert type(above_average) == list
assert type(above_average[0]) == dict
assert len(above_average) == 306
```

## Isolate restaurants with a below average rating

Now repeat the process for below average ratings.

In the cell below, isolate restaurants that have a rating of no more than `3.5`.


```python
# Create an empty list
# You will store restaurants in this list
below_average = None

# Loop over the restaurants in the dataset
# YOUR CODE HERE

    # Isolate the rating
    # YOUR CODE HERE
    
    # Check if the rating is no more than 3.5
    # YOUR CODE HERE
    
        # If the rating no more than 3.5
        # Add the restaurant to the list
        # YOUR CODE HERE
```


```python
#__SOLUTION__
# Create an empty list
# You will store restaurants in this list
below_average = []

# Loop over the restaurants in the dataset
for restaurant in restaurants:
    # Isolate the rating
    rating = restaurant['rating']
    # Check if the rating is no more than 3.5
    if rating <= 3.5:
        # If the rating no more than 3.5
        # Add the restaurant to the list
        below_average.append(restaurant)
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(below_average) == list
assert type(below_average[0]) == dict
assert len(below_average) == 247
```


```python
#__SOLUTION__
assert type(below_average) == list
assert type(below_average[0]) == dict
assert len(below_average) == 247
```

## Calculate the mean review count for above average restaurants.

Now that you've isolated above average and below average restaurants, you can calculate the average number of reviews received by both groups.

To do this, you will need to isolate the ratings for both groups, and calculate their mean. 

The code for isolating the ratings will look very similar to code you have previously written, which is a good sign that a function should be defined!

In the cell below, define a function called `isolate_values` that receives two arguments:
1. A list of dictionaries
2. A string indicating the key that should be isolated for each dictionary

This function should:
- Loop over every dictionary in the inputted list
- Pull out the value assigned to the inputted key
- Append the value to a new list
- Return the new list of values


```python
def isolate_values(dictionaries, key):
    # Create an empty list
    # for storing data
    # YOUR CODE HERE
    
    # Loop over every dicionary 
    # YOUR CODE HERE
        
        # Isolate the value of the dictionary with they `key`
        # YOUR CODE HERE
        
        # Append the value to the list
        # YOUR CODE HERE
    
    # Return the list of values
    # YOUR CODE HERE
```


      File "<ipython-input-18-031c9061accf>", line 16
        # YOUR CODE HERE
                        ^
    SyntaxError: unexpected EOF while parsing




```python
#__SOLUTION__
def isolate_values(dictionaries, key):
    # Create an empty list
    # for storing data
    values = []
    
    # Loop over every dicionary 
    for dictionary in dictionaries:
        
        # Isolate the value of the dictionary with they `key`
        value = dictionary[key]
        
        # Append the value to the list
        values.append(value)
    
    # Return the list of values
    return values
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
from types import FunctionType

assert type(isolate_values) == FunctionType
assert type(isolate_values([{'test': 1}], 'test')) == list
assert len(isolate_values([{'test': 1}], 'test')) == 1
assert len(isolate_values(above_average, 'name')) == len(above_average)
assert isolate_values(above_average, 'name')[-1] == above_average[-1]['name']
```


```python
#__SOLUTION__
from types import FunctionType

assert type(isolate_values) == FunctionType
assert type(isolate_values([{'test': 1}], 'test')) == list
assert len(isolate_values([{'test': 1}], 'test')) == 1
assert len(isolate_values(above_average, 'name')) == len(above_average)
assert isolate_values(above_average, 'name')[-1] == above_average[-1]['name']
```

Now use the `isolate_values` function to create a list called `abv_avg_rev_cnts` that contains the review counts for every above average restaurant.


```python
# Replace None with your code
abv_avg_rev_cnts = None
```


```python
#__SOLUTION__
abv_avg_rev_cnts = isolate_values(above_average, 'review_count')
```

Now use the `isolate_values` function to create a list called `blw_avg_rev_cnts` that contains the review counts for every above average restaurant.


```python
# Replace None with your code
blw_avg_rev_cnts = None
```


```python
#__SOLUTION__
blw_avg_rev_cnts = isolate_values(below_average, 'review_count')
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(abv_avg_rev_cnts) == list
assert type(abv_avg_rev_cnts[0]) == int
assert type(blw_avg_rev_cnts) == list
assert type(blw_avg_rev_cnts[0]) == int
assert len(abv_avg_rev_cnts) == len(above_average)
assert len(blw_avg_rev_cnts) == len(below_average)
assert abv_avg_rev_cnts[101] == above_average[101]['review_count']
assert blw_avg_rev_cnts[101] == below_average[101]['review_count']
```


```python
#__SOLUTION__
assert type(abv_avg_rev_cnts) == list
assert type(abv_avg_rev_cnts[0]) == int
assert type(blw_avg_rev_cnts) == list
assert type(blw_avg_rev_cnts[0]) == int
assert len(abv_avg_rev_cnts) == len(above_average)
assert len(blw_avg_rev_cnts) == len(below_average)
assert abv_avg_rev_cnts[101] == above_average[101]['review_count']
assert blw_avg_rev_cnts[101] == below_average[101]['review_count']
```

Now that you've isolated the review counts for both groups, you can calculate the average review count!

But before you do that, you should inspect the distribution of review counts to make sure `mean` is an appropriate measure of centrality.

In the cell below, we plot a histogram for above average and below average restaurant review counts.


```python
# Initialize a matplotlib subplot
# with 1 row and 2 columns
fig, ax = plt.subplots(1,2, figsize=(15,6))

# Plot a histogram of below average review counts
# on the first axis
ax[0].hist(blw_avg_rev_cnts)

# Set the title for the first axis
# to "Below Average - Review Counts"
ax[0].set_title("Below Average - Review Counts")

# Plot a histogram of above average review counts
# on the first axis
ax[1].hist(abv_avg_rev_cnts)

# Set the title for the first axis
# to "Above Average - Review Counts"
ax[1].set_title("Above Average - Review Counts");
```


```python
#__SOLUTION__
# Initialize a matplotlib subplot
# with 1 row and 2 columns
fig, ax = plt.subplots(1,2, figsize=(15,6))

# Plot a histogram of below average review counts
# on the first axis
ax[0].hist(blw_avg_rev_cnts)

# Set the title for the first axis
# to "Below Average - Review Counts"
ax[0].set_title("Below Average - Review Counts")

# Plot a histogram of above average review counts
# on the first axis
ax[1].hist(abv_avg_rev_cnts)

# Set the title for the first axis
# to "Above Average - Review Counts"
ax[1].set_title("Above Average - Review Counts");
```


    
![png](README_files/README_50_0.png)
    


**Interpret the above visualizations. What statistic is best suited for these data?**

==SOLUTION==

The above distributions both have significant outliers in the positive direction. The vast majority of review counts are between 0 and 1000 for Below Average Rating Restaurants, and between 0 and ~800 for Above Average Rating Restaurants. Given how skewed these data are, a median is a better measure of centrality.

In the cell below, calculate the average review count for above average and below average restaurants.


```python
# Import numpy
# YOUR CODE HERE

# Replace None with your code
abv_avg_rev_cnt_mean = None
blw_avg_rev_cnt_mean = None

print('Above average mean review count:', abv_avg_rev_cnt_mean)
print('Below average mean review count:', blw_avg_rev_cnt_mean)
```

    Above average mean review count: None
    Below average mean review count: None



```python
#__SOLUTION__
# Import numpy
import numpy as np

# Replace None with your code
abv_avg_rev_cnt_mean = np.median(abv_avg_rev_cnts)
blw_avg_rev_cnt_mean = np.median(blw_avg_rev_cnts)

print('Above average mean review count:', abv_avg_rev_cnt_mean)
print('Below average mean review count:', blw_avg_rev_cnt_mean)
```

    Above average mean review count: 65.5
    Below average mean review count: 168.0


**Interpret the average review count for both groups. How does this relate to your client's claims?**

==SOLUTION==

Restaurants with a low average rating, on average review ~100 more reviews than Restaurants with an above average rating. My client's claim that more reviews = better ratings is not supported by the data.

## Count the price option frequency

The `price` variable in the dataset is a string of dollar signs indicating how expensive a restaurant's price point is. 

In the cell below, write a for loop that counts how frequently a given price point appears for the `above_average` dataset


```python
# Create an empty dictionary to store the
# counts for each price point
abv_avg_prices = {}

# Loop over the above average restaurants
# YOUR CODE HERE

    # Isolate the price point for the restuarant
    # YOUR CODE HERE
    
    # Check if the price has been added to the dictionary
    # YOUR CODE HERE
    
            # If the price is already a key in the dictionary
            # Add one to the count for that price point
            # YOUR CODE HERE
            
    # If the price has not been added to the dictionary
    # Set the price as the key and the value as the integer `1`
    # YOUR CODE HERE
```


```python
#__SOLUTION__
# Create an empty dictionary to store the
# counts for each price point
abv_avg_prices = {}

# Loop over the above average restaurants
for row in above_average:
    # Isolate the price point for the restuarant
    price = row['price']
    # Check if the price has been added to the dictionary
    if price in abv_avg_prices:
            # If the price is already a key in the dictionary
            # Add one to the count for that price point
            abv_avg_prices[price] += 1
    # If the price has not been added to the dictionary
    # Set the price as the key and the value as the integer `1`
    else:
        abv_avg_prices[price] = 1
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(abv_avg_prices) == dict
assert len(abv_avg_prices) == 5
assert '\\$\\$\\$\\$' in abv_avg_prices
```


```python
#__SOLUTION__
assert type(abv_avg_prices) == dict
assert len(abv_avg_prices) == 5
assert '\\$\\$\\$\\$' in abv_avg_prices
```

**Now reapply the same process, but instead calculate the price point frequencies for the `below_average` dataset.**


```python
# Create an empty dictionary to store the
# counts for each price point
# YOUR CODE HERE

# Loop over the below average restaurants
# YOUR CODE HERE

    # Isolate the price point for the restuarant
    # YOUR CODE HERE
    
    # Check if the price has been added to the dictionary
    # YOUR CODE HERE
    
            # If the price is already a key in the dictionary
            # Add one to the count for that price point
            # YOUR CODE HERE
            
    # If the price has not been added to the dictionary
    # Set the price as the key and the value as the integer `1`
    # YOUR CODE HERE
```


```python
#__SOLUTION__
# Create an empty dictionary to store the
# counts for each price point
blw_avg_prices = {}

# Loop over the below average restaurants
for row in below_average:
    # Isolate the price point for the restuarant
    price = row['price']
    # Check if the price has been added to the dictionary
    if price in blw_avg_prices:
            # If the price is already a key in the dictionary
            # Add one to the count for that price point
            blw_avg_prices[price] += 1
    # If the price has not been added to the dictionary
    # Set the price as the key and the value as the integer `1`
    else:
        blw_avg_prices[price] = 1
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(blw_avg_prices) == dict
assert len(blw_avg_prices) == 4
assert '\\$' in blw_avg_prices
```


```python
#__SOLUTION__
assert type(blw_avg_prices) == dict
assert len(blw_avg_prices) == 4
assert '\\$' in blw_avg_prices
```

## Create a bar plot that sets the frequency of each price point as the y axis


```python
# Import matplotlib
# YOUR CODE HERE

# Create a matplotlib subplot with 1 row and 2 columns
# YOUR CODE HERE

# Isolate keys of the below average price count dictionary
# This will be the x-axis
# YOUR CODE HERE

# Isolate the values of the below average price count dictionary
# This will be the y-axis
# YOUR CODE HERE

# Plot the below average price point counts as a bar plot
# on the first axis
# YOUR CODE HERE

# Set the title for the first axis
# to the string "Below Average"
# YOUR CODE HERE

# Isolate keys of the above average price count dictionary
# This will be the x-axis
# YOUR CODE HERE

# Isolate the values of the above average price count dictionary
# This will be the y-axis
# YOUR CODE HERE

# Plot the above average price counts as a bar plot
# on the second axis
# YOUR CODE HERE

# Set the title for the second axis to 
# the string 'Above Average'
# YOUR CODE HERE
```


```python
#__SOLUTION__
# Import matplotlib
import matplotlib.pyplot as plt

# Create a matplotlib subplot with 1 row and 2 columns
fig, ax = plt.subplots(1, 2, figsize=(15,6))

# Isolate keys of the below average price count dictionary
# This will be the x-axis
x = blw_avg_prices.keys()

# Isolate the values of the below average price count dictionary
# This will be the y-axis
y = blw_avg_prices.values()

# Plot the below average price point counts as a bar plot
# on the first axis
ax[0].bar(x, y)

# Set the title for the first axis
# to the string "Below Average"
ax[0].set_title('Below Average')

# Isolate keys of the above average price count dictionary
# This will be the x-axis
x = abv_avg_prices.keys()

# Isolate the values of the above average price count dictionary
# This will be the y-axis
y = abv_avg_prices.values()

# Plot the above average price counts as a bar plot
# on the second axis
ax[1].bar(x, y)

# Set the title for the second axis to 
# the string 'Above Average'
ax[1].set_title('Above Average');
```


    
![png](README_files/README_72_0.png)
    


**Interpret the above visualization. How does it relate to your client's claims?**

==SOLUTION==

The above visualization shows that the least expensive price point `$` is the most frequent option for restaurants with a below average rating, and that the price option `Unknown` is the most common for restaurants with an above average rating. My client claims that the price option `$$` is the most common price option for above average restaurants. While this visualization suggests that my client's claim is incorrect, the `$$` price option _is_ the second most frequent price point for above average restaurants. If my clients goal is to align their price options with more above average restaurants a move from `$` to `$$` is justified. I am, however, unable to identify the most commmon price option for above average rating restaurants due to missing data. Further investigating is required.

## Analyze restaurant location

In the cell below, use the `isolate_value` function to isolate `longitude` and `latitude` for above and below average restaurants.


```python
# Replace None with your code

# Isolate longitude for above average restauransts
abv_avg_lon = None

# Isolate latitude for above average restaurants
abv_avg_lat = None

# Isolate longitude for below average restauransts
blw_avg_lon = None

# Isolate latitude for below average restaurants
blw_avg_lat = None

plt.figure(figsize=(15,6))
plt.scatter(abv_avg_lon, abv_avg_lat, label='Above')
plt.scatter(blw_avg_lon, blw_avg_lat, label='Below')
plt.legend();
```


    
![png](README_files/README_76_0.png)
    



```python
#__SOLUTION__
# Isolate longitude for above average restauransts
abv_avg_lon = isolate_values(above_average, 'longitude')

# Isolate latitude for above average restaurants
abv_avg_lat = isolate_values(above_average, 'latitude')

# Isolate longitude for below average restauransts
blw_avg_lon = isolate_values(below_average, 'longitude')

# Isolate latitude for below average restaurants
blw_avg_lat = isolate_values(below_average, 'latitude')

plt.figure(figsize=(15,6))
plt.scatter(abv_avg_lon, abv_avg_lat, label='Above')
plt.scatter(blw_avg_lon, blw_avg_lat, label='Below')
plt.legend();
```


    
![png](README_files/README_77_0.png)
    


## Remove the outlier

There is one restaurant in the above average dataset with a location dramatically west and south of all other observations. Let's remove that restaurant from the above average dataset and regenerate the scatter plot.


```python
# Create an empty list
# to that will contain data with
# the outlier removed
no_outliers = # YOUR CODE HERE

# Create an empty list to append the outlier
outlier = # YOUR CODE HERE

# Loop over every restaurant in the above average dataset
# YOUR CODE HERE
    
    # Isolate the restaurant's longitude
    # YOUR CODE HERE
    
    # Check if the longitude value is greater than the integer -90
    # YOUR CODE HERE
        
        # Append the restaurant to the no_outliers list
        # YOUR CODE HERE
        
    # If longitude is less than -90 it is an outlier
    # and should be append to the outlier list
    # YOUR CODE HERE
```


```python
#__SOLUTION__
# Create an empty list
# to that will contain data with
# the outlier removed
no_outliers = []

# Create an empty list to append the outlier
outlier = []

# Loop over every restaurant in the above average dataset
for restaurant in above_average:
    
    # Isolate the restaurant's longitude
    longitude = restaurant['longitude']
    
    # Check if the longitude value is greater than the integer -90
    if longitude > -90:
        
        # Append the restaurant to the no_outliers list
        no_outliers.append(restaurant)
        
    # If longitude is less than -90 it is an outlier
    # and should be append to the outlier list
    else:
        outlier.append(restaurant)
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(no_outliers) == list
assert type(outlier) == list
assert len(no_outliers) == len(above_average) - 1
assert len(outlier) == 1
```


```python
#__SOLUTION__
assert type(no_outliers) == list
assert type(outlier) == list
assert len(no_outliers) == len(above_average) - 1
assert len(outlier) == 1
```

Now regenerate the longitude and latitude for above average restaurants using the `no_outliers` dataset, and regenerate the scatter plot!


```python
abv_avg_lon = None
abv_avg_lat = None

plt.figure(figsize=(15,6))
plt.scatter(abv_avg_lon, abv_avg_lat, label='Above')
plt.scatter(blw_avg_lon, blw_avg_lat, label='Below')
plt.legend();
```


```python
#__SOLUTION__
abv_avg_lon = isolate_values(no_outliers, 'longitude')
abv_avg_lat = isolate_values(no_outliers, 'latitude')

plt.figure(figsize=(15,6))
plt.scatter(abv_avg_lon, abv_avg_lat, label='Above')
plt.scatter(blw_avg_lon, blw_avg_lat, label='Below')
plt.legend();
```


    
![png](README_files/README_86_0.png)
    


Nice. This is much more interesting. 

## Plot the distribution of latitude and longitude

To get a better sense about how latitude and longitude are working, in the cell below plot histograms for latitude and longitude.


```python
# Create a matplotlib subplot with 1 row and 2 columns
# YOUR CODE HERE

# Plot a histogram of above average longitude
# on the first subplot axis. Set alpha to .6
# YOUR CODE HERE

# Plot a histogram of below average longitude
# on the first subplot axis. Set alpha to .6
# YOUR CODE HERE

# Set the title for the first subplot axis
# to the string "Longitude"
# YOUR CODE HERE

# Plot a histogram of above average latitude
# on the second subplot axis. Set alpha to .6
# YOUR CODE HERE

# Plot a histogram of below average latitude
# on the second subplot axis. Set alpha to .6
# YOUR CODE HERE

# Set the title for the second subplot axis
# to the string "Latitude"
# YOUR CODE HERE
```


```python
#__SOLUTION__
# Create a matplotlib subplot with 1 row and 2 columns
fig, ax = plt.subplots(1,2, figsize=(15,6))

# Plot a histogram of above average longitude
# on the first subplot axis. Set alpha to .6
# Set label to the string "Above"
ax[0].hist(abv_avg_lon, alpha=.6, label='Above')

# Plot a histogram of below average longitude
# on the first subplot axis. Set alpha to .6
# Set label to the string "Below"
ax[0].hist(blw_avg_lon, alpha=.6, label='Below')

# Set the title for the first subplot axis
# to the string "Longitude"
ax[0].set_title('Longitude')

# Plot a histogram of above average latitude
# on the second subplot axis. Set alpha to .6
# Set label to the string "Above"
ax[1].hist(abv_avg_lat, alpha=.6, label='Above')

# Plot a histogram of below average latitude
# on the second subplot axis. Set alpha to .6
# Set label to the string "Below"
ax[1].hist(blw_avg_lat, alpha=.6, label='Below')

# Set the title for the second subplot axis
# to the string "Latitude"
ax[1].set_title('Latitude')

# Activate the legend for both subplot axes
ax[0].legend()
ax[1].legend();
```


    
![png](README_files/README_90_0.png)
    


**Interpret the above visualization. How does it relate to your client's claims?**

==SOLUTION==

The above visualization shows that above average rating restaurants are centered slightly more to the east than below average rating restaurants. Both distributions appear to largly centered in the same place when it comes to latitude (north --> south). My client's claim that above average restaurants are further east is supported by this visualization, though the different is quite small. This visualization refutes my client's claim that north vs southern placement is a good seperator for above average and below average rating restaurants.

## Find the most common zipcode for above average restaurants

In the cell below, loop over the restaurants in the above average dataset and count the frequency of the the restaurants zipcode.


```python
# Create an empty dictionary
# This dictionary will hold the counts
# for each zipcode
abv_avg_zip_cnts = # YOUR CODE HERE

# Loop over the above average dataset
# YOUR CODE HERE
    
    # Isolate the restaurant's zipcode 
    # YOUR CODE HERE
    
    # Check if the zipcode is a key in the dictionary
    # YOUR CODE HERE
        
        # Add one to the zipcode's value
        # YOUR CODE HERE
    
    # If the zipcode is not a key
    # add it to the dictionary with a value of 1
    # YOUR CODE HERE
```


```python
#__SOLUTION__
# Create an empty dictionary
# This dictionary will hold the counts
# for each zipcode
abv_avg_zip_cnts = {}

# Loop over the above average dataset
for restaurant in above_average:
    
    # Isolate the restaurant's zipcode 
    zipcode = restaurant['location']['zip_code']
    
    # Check if the zipcode is a key in the dictionary
    if zipcode in abv_avg_zip_cnts:
        
        # Add one to the zipcode's value
        abv_avg_zip_cnts[zipcode] += 1
    
    # If the zipcode is not a key
    # add it to the dictionary with a value of 1
    else:
        abv_avg_zip_cnts[zipcode] = 1
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(abv_avg_zip_cnts) == dict
assert len(abv_avg_zip_cnts) == 104 or len(abv_avg_zip_cnts) == 103
assert '10012' in abv_avg_zip_cnts
```


```python
#__SOLUTION__
assert type(abv_avg_zip_cnts) == dict
assert len(abv_avg_zip_cnts) == 104 or len(abv_avg_zip_cnts) == 103
assert '10012' in abv_avg_zip_cnts
```

Now loop over the `abv_avg_zip_cnts` dictionary and find the zipcode with the largest count. 

For this question, there are multiple ways to find the solution. Comments have not been provided.


```python
# Your code here
```


```python
#__SOLUTION__

# SOLUTION 1 - Sort the dictionary

### Create a list of tuples using `.items`
items = abv_avg_zip_cnts.items()

### Sort the list of tuples in descending order
items_sorted = sorted(items, key=lambda x: x[1], reverse=True)

#### Pull the zipcode from the first value 
#### to find the zipcode with the largest count
most_common_zip_1 = items_sorted[0][0]

# SOLUTION 2 - Loop over the dictionary

### Create a placeholder varaible to store the answer
most_common_zip_2 = None

### Create a counter variable to store the counts
largest_count = 0

### Loop over the dictionary of zipcode counts
for zipcode in abv_avg_zip_cnts.keys():
    
    # Isolate the zipcode count
    count = abv_avg_zip_cnts[zipcode]
    
    # Check if the count is greater than `largest_count`
    if count > largest_count:
        
        # Set most_common_zip to the zipcode
        most_common_zip_2 = zipcode
        
        # Update largest count
        largest_count = count
        
# Confirm both solutions produce the same results
assert most_common_zip_1 == most_common_zip_2

# Print result
print('The most common zipcode for above average restaurants:', most_common_zip_1)
```

    The most common zipcode for above average restaurants: 10014


**Interpret the results. How does the most frequent zipcode relate to your client's claims?**

==SOLUTION==

This finding rejects my client's claim. The zipcode containing the most above average restaurants, given that above average is defined as having a rating >= 4.5, is 10014. It is not 10012. 

## Compile your findings into a report

You have address all of your client's claims! In the cell below, describe the findings of your analysis.

==SOLUTION==

**This analysis finds** 
- `4` is average yelp rating in NYC.
- Restaurants with a below average rating have a higher avergae review count than restaurants with an above average rating.
- `$$` is the second most common price option for above average restaurants. Due to missing data, further investigation is required in order to determine the the most common price point. `$` is the most common price option for restaurants with a below average rating.
- Restaurants with an above average rating are slightly further east than restaurants with a below average rating. There does not appear to be a difference North to South.
- `10014` is the zipcode with the most above average rated restaurants, it is not `10012`.

# Summary

Well done! As you can see, manipulating nested data stuctures can be a challenging task. Pulling information from json objects requires a thoughtful inspection of how the data is organized, and code that allows you to avoid repetition.
