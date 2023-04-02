---
layout: post
title:  Analyzing the IMDb Database
author: Nory Arroyo
description: An exploratory data analysis post to provide different insights into a movies database.
image: /assets/images/EDA.png
---

Exploratory Data Analysis (EDA) is fundamental to recognizing patterns and trends in your data. You can do many things, but in this post, I will show you some basic graphs you could use when doing your projects. The dataset we will be using comes from an IMDb database. We want to see what makes a movie successful among users. If you want to see how I obtained it, you can check my [previous post](https://noryarroyo.github.io/my386blog/2023/03/16/data-collection.html).  

Note: The data in the previous post might differ from this one as I added variables and cleaned up the data to perform the best possible EDA. 

## What are we looking for? 

These are the first few lines of the dataset we will perform the EDA on. 

<img src="https://raw.githubusercontent.com/noryarroyo/my386blog/main/assets/images/top_300.png" alt="" style="width:400px;"/>

From looking at it, there are a few things we can begin with: 

- A distribution of the IMDb scores
- Critic vs. Audience Scores 
- Top Directors and Actors
- Runtime over the years
- The different genres and ratings.
- How do all the variables correlate? 


We can use visuals to look at these observations. 

## A distribution of the IMDb Scores 

Since we want to see what gets a movie a good rating the first thing I was thinking of is seeing the distribution of User Scores. The ratings go from 1 to 10. 

<img src="https://raw.githubusercontent.com/noryarroyo/my386blog/main/assets/images/eda_1.png" alt="" style="width:400px;"/>

The scores tend to center at the 8.1 to 8.2 range, and most of them go up until the 9.0 score. Only two movies make it past 9.1. 


## Critics vs Audience Score 

Have you ever seen a movie and thought it was excellent and then saw the critics give it a rating in the 60s? Because of experiences like this, I wanted to see if there's a correlation between how the critics and regular people think. So here's a scatterplot that studies the correlation.  

<img src="https://raw.githubusercontent.com/noryarroyo/my386blog/main/assets/images/eda_3.png" alt="" style="width:400px;"/>

As we can observe, there is no correlation between IMDb and Metacritic scores. Metacritic is a website similar to IMDb but for the leading critics in the industry. We can see that audiences and critics don't tend to think the same. If we think about it, critics consider a lot of technical components that the average person doesn't know about. 


## Top Directors and Actors

I wanted to see what Director had the most movies in this top 300 and wanted to check which Actor appears the most and the amount of votes their movies might have accumulated. 


<img src="https://raw.githubusercontent.com/noryarroyo/my386blog/main/assets/images/eda_6.png" alt="" style="width:400px;"/>
We can see that the top director is [Akira Kurosawa](https://en.wikipedia.org/wiki/Akira_Kurosawa). I was impressed because I didn't know who he was. I thought the top one would be Christopher Nolan or James Cameron. The rest of the ranking isn't personally surprising.


We also can do a bar chart to look at the top 5 actors and the number of votes they accumulated on this dataset. 


<img src="https://raw.githubusercontent.com/noryarroyo/my386blog/main/assets/images/eda_7.png" alt="" style="width:400px;"/>

I'm not surprised to see Leonardo Dicaprio as the top actor. His movies have accumulated more than 7 million user votes, followed closely by Tom Hanks. These two actors have been in many recognizable movies, such as Inception, The Departed, Forrest Gump, and Saving Private Ryan.


## Runtime Over Years 

Another helpful insight is to see if the movies have increased their runtime over the years. I mainly wanted to analyze it over decades. So I grouped the Years column and plotted a simple chart. 


<img src="https://raw.githubusercontent.com/noryarroyo/my386blog/main/assets/images/eda_5.png" alt="" style="width:400px;"/>

The decade with the lowest average runtime is the 1920s, which makes sense since the technology was minimal. We have had a constant increase since the 90s in average runtime.


## The different genres and ratings


There are many different genres and ratings in this dataset, so for simplicity (and relevance), I chose the top 6 genres and wanted to see what the ratings for each one looked like.

<img src="https://raw.githubusercontent.com/noryarroyo/my386blog/main/assets/images/eda_4.png" alt="" style="width:400px;"/>


Drama is the genre with the most amount of movies, and overwhelmingly the most prevalent is the R rating, which is also the most common across the other genres. The most common type is Not Rated, meaning a movie was not submitted for rating, which could indicate missing information that could affect our data.  

## How do all the variables correlate? 


Last, we can check a correlation matrix to see if we missed any insights. It could also serve as a summary of all the things we looked above.


<img src="https://raw.githubusercontent.com/noryarroyo/my386blog/main/assets/images/eda_1.png" alt="" style="width:400px;"/>

The strongest correlation in the data is between Votes and the IMDb Score, with the weakest correlation between Metacritic Score and Votes. One interesting correlation that I feel is interesting to take a closer look at is Metacritic Score and Year. 

# Now what? 

I better understand the trends and patterns that make a movie successful among users. I also discovered that there are some limitations when it comes to the dataset we crafted. The findings are very surface-level, which lets me know that I probably need to redirect my research. But this is the point of an EDA, to assess the data quality and the essential features to us. I could look at the box office performance and whether it is on a streaming platform and at the average age of the user. 

If you want to look at the code for both [the data collection and EDA](https://github.com/noryarroyo/386-Data-Project-) you can check it out at this repository. I look forward to explaining the data story. 






