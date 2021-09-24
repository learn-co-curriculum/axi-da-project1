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
# Isolate the first observation
first_observation = None
# Find the datatype for the first observation
observation_type = None
# How many observations are there
num_observations = None
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

## Find the possible rating options. 

In the cell below, create a variable called `rating_options` that has a [set datatype](https://realpython.com/python-sets/), and is a unique collection of the possible ratings a restaurant can recieve.


```python
# Create the `rating_options` variable
rating_options = None

# Loop over all of the observations in the dataset


    # Isolate the rating for the restaurant
    # YOUR CODE HERE
    
    # Add the rating to 
    # the `rating_options` variable
    # YOUR CODE HERE
    
rating_options
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
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

**Interpret the ratings histogram. How does the visualization relate to your client's claims?**

YOUR ANSWER HERE

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

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
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

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(below_average) == list
assert type(below_average[0]) == dict
assert len(below_average) == 247
```

## Calculate average review counts for both groups

Now that you've isolated above average and below average restaurants, you can calculate the average number of reviews received by both groups.

To do this, you will need to isolate the review counts for both groups, and calculate their average. 

The code for isolating the review counts will look very similar to code you have previously written, which is a good sign that a function should be defined!

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
        
        # Isolate the value of the dictionary with the `key`
        # YOUR CODE HERE
        
        # Append the value to the list
        # YOUR CODE HERE
    
    # Return the list of values
    # YOUR CODE HERE
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

Now use the `isolate_values` function to create a list called `abv_avg_rev_cnts` that contains the review counts for every above average restaurant.


```python
# Replace None with your code
abv_avg_rev_cnts = None
```

Now use the `isolate_values` function to create a list called `blw_avg_rev_cnts` that contains the review counts for every below average restaurant.


```python
# Replace None with your code
blw_avg_rev_cnts = None
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

**Interpret the above visualizations. What statistic is best suited for these data?**

YOUR ANSWER HERE

In the cell below, calculate the average review count for above average and below average restaurants.


```python
# Import numpy
# YOUR CODE HERE

# Replace None with your code
abv_avg_rev_cnt_center = None
blw_avg_rev_cnt_center = None

print('Above average review count:', abv_avg_rev_cnt_center)
print('Below average review count:', blw_avg_rev_cnt_center)
```

**Interpret the average review count for both groups. How does this relate to your client's claims?**

YOUR ANSWER HERE

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
    # Else set the price as the key and the value as the integer `1`
    # YOUR CODE HERE
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
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

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(blw_avg_prices) == dict
assert len(blw_avg_prices) == 4
assert '\\$' in blw_avg_prices
```

## Create a bar plot that sets the frequency of each price point as the y axis


```python
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

**Interpret the above visualization. How does it relate to your client's claims?**

YOUR ANSWER HERE

## Analyze restaurant location

In the cell below, use the `isolate_values` function to isolate `longitude` and `latitude` for above and below average restaurants.


```python
# Replace None with your code

# Isolate longitude for above average restaurants
abv_avg_lon = None

# Isolate latitude for above average restaurants
abv_avg_lat = None

# Isolate longitude for below average restaurants
blw_avg_lon = None

# Isolate latitude for below average restaurants
blw_avg_lat = None

plt.figure(figsize=(15,6))
plt.scatter(abv_avg_lon, abv_avg_lat, label='Above')
plt.scatter(blw_avg_lon, blw_avg_lat, label='Below')
plt.legend();
```

## Remove the outlier

There is one restaurant in the above average dataset with a location dramatically west and south of all other observations. Let's remove that restaurant from the above average dataset and regenerate the scatter plot.


```python
# Create an empty list
# that will contain data with
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
    # and should be appended to the outlier list
    # YOUR CODE HERE
```

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
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

Nice. This is much more interesting. 

## Plot the distribution of latitude and longitude

To get a better sense about how latitude and longitude are working, in the cell below plot histograms for latitude and longitude.


```python
# Create a matplotlib subplot with 1 row and 2 columns
# YOUR CODE HERE

# Plot a histogram of above average longitude
# on the first subplot axis. Set alpha to .6
# Set label to the string "Above"
# YOUR CODE HERE

# Plot a histogram of below average longitude
# on the first subplot axis. Set alpha to .6
# Set label to the string "Below"
# YOUR CODE HERE

# Set the title for the first subplot axis
# to the string "Longitude"
# YOUR CODE HERE

# Plot a histogram of above average latitude
# on the second subplot axis. Set alpha to .6
# Set label to the string "Above"
# YOUR CODE HERE

# Plot a histogram of below average latitude
# on the second subplot axis. Set alpha to .6
# Set label to the string "Below"
# YOUR CODE HERE

# Set the title for the second subplot axis
# to the string "Latitude"
# YOUR CODE HERE
```

**Interpret the above visualization. How does it relate to your client's claims?**

YOUR ANSWER HERE

## Find the most common zipcode for above average restaurants

In the cell below, loop over the restaurants in the above average dataset and count the frequency of the restaurants zipcode.


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

Run the next cell unchanged to test your work!
> If the below cell runs without throwing an error, your code is likely correct!


```python
assert type(abv_avg_zip_cnts) == dict
assert len(abv_avg_zip_cnts) == 104 or len(abv_avg_zip_cnts) == 103
assert '10012' in abv_avg_zip_cnts
```

Now loop over the `abv_avg_zip_cnts` dictionary and find the zipcode with the largest count. 

For this question, there are multiple ways to find the solution. Comments have not been provided.


```python
# Your code here
```

**Interpret the results. How does the most frequent zipcode relate to your client's claims?**

YOUR ANSWER HERE

## Compile your findings into a report

You have address all of your client's claims! In the cell below, describe the findings of your analysis.

YOUR ANSWER HERE

# Summary

Well done! As you can see, manipulating nested data stuctures can be a challenging task. Pulling information from json objects requires a thoughtful inspection of how the data is organized, and code that allows you to avoid repetition.
