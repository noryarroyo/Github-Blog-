---
layout: post
title:  "Python as a tool to visualize SQL Data"
author: Nory Arroyo
description: "Instructions on how to utilize Python to look at SQL Data "
image: /assets/images/image3.png
---
# Why use SQL and Python? 

As statistics students, we are accustomed to using R Programming for most of our classes. Still, from personal experience, most recruiters in the Data field look for people who can handle these two programming languages adequately. SQL is a great tool for keeping information and a very simple programming language to understand, but if you wish to visualize the data inside the database, Python is a great tool to do so. 

## Requirements 

To perform this tutorial you will need to install: 

1. Jupyter Notebook 
2. MySQl

If needed: 

[Install Jupyter Notebook](https://jupyter.org/install)  

[Install MySQL](https://dev.mysql.com/doc/mysql-installation-excerpt/5.7/en/)

### 1. Set up a connector between SQL and Python 

First, you will need the following packages: pandas, numpy, seaborn, matplotlib.pyplot and sqlalchemy. If you don't have these packages here's how to [install python packages.](https://packaging.python.org/en/latest/tutorials/installing-packages/)

Your cell in Jupyter Notebook should look like the next (you can pick your aliases). 

![Figure](https://github.com/noryarroyo/my386blog/raw/main/assets/images/packages.png)

There are many ways that you can connect SQL with Python. In this tutorial, we will be using SQLAlchemy and will create an engine that serves to connect to a local SQL database and pull the information to Python. 
![Figure](https://github.com/noryarroyo/my386blog/raw/main/assets/images/engine.png)

 You should place your username, password, database of choice, I have a database called movies in mySQL database, which I'll use for the next few steps. Your engine should now be able to pull information from SQL. If you wish to [create your own database](https://learn.microsoft.com/en-us/sql/relational-databases/databases/create-a-database?view=sql-server-ver16) or [add sample data.](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms) 


### 2. Create a dataframe 

To create a dataframe we need to extract the information from the SQL database. As we know SQL databases have many tables. There are many ways that you can join these tables, but as of know, I am only interested in one. I will use the following command to pull the table movie from the movies database. Once again, you can choose whatever database and tables you want. 

![Figure](https://github.com/noryarroyo/my386blog/raw/main/assets/images/first_dataframe.png)

This dataframe now contains around five thousand of the most popular films. I selected movie title, runtime, budget and revenue, because the rest of the fields didn't provide any helpful information. To proceed with the graphing portion of the tutorial, let's eliminate zero values and Nas and then create a column that tells each movie's profit. 

![Figure](https://github.com/noryarroyo/my386blog/raw/main/assets/images/cleaned_dataframe.png)

Now that we have the cleaned dataframe it'll be easier to proceed with the visualization portion of the tutorial. 

### 3. Visualizing insights 

There are many things I could choose to do with this portion of the tutorial, but for simplicity's sake let's do some very basic plots. To begin we will do a bar plot that tells us the top 5 most profitable movies. 

![Figure](https://github.com/noryarroyo/my386blog/raw/main/assets/images/first_graph.png)

Looking at the graph, we can tell that the most profitable movie of all time is Avatar and that its profit is in the billions. Now, looking at the rest of the top 5, we can notice that all these movies are part of franchises. This is an example of the insights we can draw with simple code and graphs. We shall proceed to look at a boxplot of the runtime. 

Code: 

![Figure](https://github.com/noryarroyo/my386blog/raw/main/assets/images/code_graph.png)


Graph: 
![Figure](https://github.com/noryarroyo/my386blog/raw/main/assets/images/boxplot_graph.png)

From our observations from the boxplot we can see that the average movie runtime is around 110 (1 hour and 40 minutes) and 75% of the movies are less than 130 
(2 hours and 10 minutes), with 25% less than 95 minutes (1 hour and 35 minutes). Thinking about the movies that I typically watch these insights seem typical to me. 

## Conclusion 

There are many more things you can do with SQL and Python. But I hope that this small tutorial was able to show you just the surface of what is hopefully a very long journey into data science. Of course, practicing is the best way to learn, so grab your data and experiment with new packages, techniques and statistical tools. 





















