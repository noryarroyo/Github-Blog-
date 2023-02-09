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

### 3. Graphs!















