---
layout: post
title:  "Top 300 Movies in IMDb"
author: Nory Arroyo
description: We all love movies and this dataset shows you the highest rated movies by users in IMDb. 
image: /assets/images/image_4.png
---

# Introduction

IMDb is a website containing databases about different media types, such as shows, movies, books, video games, etc. For my project, I would like to focus on data containing movies. More specifically, the top 300 films rated by users. What makes a movie popular among users? Is it the Genre? Is there an average runtime? How successful were these movies at the box office? We will analyze all these things and then try to predict if a film will be successful among users. 


## Getting the data 

We will collect the data as specified above from the [IMDb website](https://www.imdb.com/search/title/?groups=top_1000&sort=user_rating,desc&count=100&ref_=adv_prv).

In the following sections, I will describe how I scraped the relevant information for the top 300 movies. 

In a later post, we will perform EDA to determine what all these successful movies have in common. 



# Data Collection 

I used Python specifically the Requests and BeautifulSoup to web scrape the data from the website. According to [IMDb Conditions of Use](https://www.imdb.com/conditions), this is legal as long as we don't use it for commercial purposes, which is not the case, so we're good to go. 


## Step 1: Create Beautiful Soup Object 

1. Use requests and beautiful soup to send requests to the website and parse the html content

```
url = 'https://www.imdb.com/search/title/?count=100&groups=top_1000&sort=user_rating'
r = requests.get(url) 
bs = BeautifulSoup(r.text) 

```
## Step 2: Tests your beautiful soup objects

2. Because it can get tricky finding the diffrent tags inside the website and the correct information for each of these I think the best way to go is first doing one individual instance of the tag to verify all the correct information. I wanted to get the movie's name, the rating, runtime, genre, user and critics ratings and the gross revenue. 

```
bs.find("h3", {"class": "lister-item-header"}).get_text().strip() 
bs.find("span", {"class": "certificate"}).get_text().strip()
bs.find("span", {"class": "runtime"}).get_text().strip()
bs.find("span", {"class": "genre"}).get_text().strip()
bs.find("div", {"class": "inline-block ratings-imdb-rating"}).get_text().strip() 
bs.find("span", {"class": "metascore favorable"}).get_text().strip() 
bs.find("p", {"class": "sort-num_votes-visible"}).get_text().strip() 

```

## Step 3: Loop through all the instances of the tag containing the movie information


3. All the information we found on the previous question are contained under the class tag lister-item-content, we will loop through each one of these and then form a dataset 

```

class_name = 'lister-item-content' 
all_instances = bs.find_all('div', class_=class_name)

top_movies_part_1 = {'Name':[], 'Rating':[], 'Runtime':[], 'Genre':[], 'IDBM Score':[], 'Metacritic Score':[], 'Gross Revenue':[]} #

loop through all the instances 

for instance in all_instances: 
    top_movies_part_1['Name'].append(instance.find('a').text.strip())
    top_movies_part_1['Rating'].append(instance.find('span', class_='certificate').text.strip() if instance.find('span', class_='certificate') else None)
    top_movies_part_1['Runtime'].append(instance.find('span', class_='runtime').text.strip())
    top_movies_part_1['Genre'].append(instance.find('span', class_='genre').text.strip())
    top_movies_part_1['IDBM Score'].append(instance.find('div', class_='inline-block ratings-imdb-rating').text.strip())
    top_movies_part_1['Metacritic Score'].append(instance.find('span', class_='metascore').text.strip() if instance.find('span', class_='metascore') else None)
    top_movies_part_1['Gross Revenue'].append(instance.find('span', attrs={'name': 'nv'}).text.strip())

convert the dictionary created in the loop into a dataframe 

df_1 = pd.DataFrame.from_dict(top_movies_part_1) #creates first dataframe

```

## Step 4: Complete dataset 

In order to do the top 300 I had to repeat step 3 two more times, to get 1-100, 101-200, 201-300 on the list. There should be a better way to do this, but is outside of my knowledge at the moment 

4. We can now simply add all the dataframes together 

```

top_movies = pd.concat([df_1, df_2, df_3], ignore_index=True)
top_movies

Here's the completed dataset! All the 300 movies together. 

![Figure](https://raw.githubusercontent.com/esnt/my386blog/main/assets/images/df_complete.png)
```

# Conclusion 

In this post, I showed how to extract the data from the IMDb database, but you can use this same method to gather other type of information that interests you. On the EDA, I will find out the reason why these movies are so popular. 

If you have any questions, feedback or comments let me know. 

