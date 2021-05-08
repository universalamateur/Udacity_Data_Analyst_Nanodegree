# Submission - Falko Sieverding - Exploring Weather Trends

## Goal of the project

I wil analyze local and global temperature data and compare the temperature trends.  
For the porject, I choose the city, I am currently living in, [Athens, Greece, Europe](https://osm.org/go/xxSiEUQ-) to visualize and describe the similarities and differences between the local and global temperature trends.

## Steps taken

### Data extraction from database using SQL

#### The Dataset

For this project I was provided with a database of 3 tables via a webinterface with the following schema:
1. city_list - Fields: city \ country
2. city_data - Fields: year \ city \ country \ avg_temp (ºC)
3. global_data - This contains the average global temperatures by year (ºC)

#### The SQL Queries

1. One Query per table:  
1.1. table city_data  

```
SELECT year, avg_temp AS avg_temp_athens FROM city_data WHERE city='Athens'
```

- result count: 261  

1.2. table global_data

```
SELECT year, avg_temp AS avg_temp_global FROM global_data
```

- result count: 266  

2. Even one step further would be a FULL (OUTER) JOIN (Returns all records when there is a match in either table) to get all results.  
2.1. Full Outer join on table city_data and table global_data

```
SELECT city_data.year, global_data.year, global_data.avg_temp AS avg_temp_global, city_data.avg_temp AS avg_temp_athens FROM global_data FULL JOIN city_data ON global_data.year = city_data.year WHERE city_data.city='Athens';
```

- result count: 261  

3. As the Full join does not have the expected result count of 266 or more, something is going wrong. I will go on with the 2 SQL queries (one on each table) and join the dataframes later.

### Manipulation of data

I choose to manipulate the data in a jupyter python notebook (attached here and [also on github](https://github.com/universalamateur/Udacity_Data_Analyst_Nanodegree/blob/main/Exploring%20Weather%20Trends%20-%20Project/Exploring%20Weather%20Trends%20-%20Athens%2C%20GR%20compared%20to%20global.ipynb)), in which I use [Pandas Libary](https://pandas.pydata.org/docs/index.html) for python to manipulate the data.

1. After I have uploaded the CSV files to my GitHub Repo and then read those into dataframes with the ```pandas.read_csv()``` function, I checked the data for wholes and duplicates, but could not find any, just that the datasets were not fully overlapping and the global dataset had some datapoints more than the Athens one.

2. Then I used the pandas inherent function ```pandas.DataFrame.rolling(window=Windowssize)```, which provides a rolling window calculations, with the "mean" aggregation ```pandas.DataFrame.rolling(window=Windowssize).mean()```. This I did for the local and global dataframe each with a window size of 5 and 10 years.
   - example code for adding a 5 year Simple Moving Average (SMA) into my dataframe:  

 ```pandas.DataFrame['avg_temp_Athens_SMA_5']=pandas.DataFrame.iloc[:,1].rolling(window=5).mean()```

3. After these steps I had 2 dataframes (global and local_Athens) with a 5 and 10 year SMA

### Visualization of data

For the visualization of the data I choose to use the python [libary matplotlib](https://matplotlib.org/stable/index.html).



## Observations

## Definitions

- **Simple Moving Average** (SMA): Simple Moving Average (SMA) uses a sliding window to take the average over a set number of time periods. It is an equally weighted mean of the previous n data.
- **Full Outer Join**: in SQL the FULL OUTER JOIN combines the results of both left and right outer joins and returns all (matched or unmatched) rows from the tables on both sides of the join clause.

## Attachments
