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
On the x-axis the years in steps of 10 are shown.  
The y-axis shows the temperature data.  
The used colors are explained in the Legend.  

1. The first line plot (fig 1) shows the Simple Moving Average with a windowsize of 5 and 10 years for Athens and the global average temperature.

![fig 1: SMA 5 and 10 years plotted for average temperatures in Athens and globaly](https://raw.githubusercontent.com/universalamateur/Udacity_Data_Analyst_Nanodegree/main/Exploring%20Weather%20Trends%20-%20Project/Plot_Graphics/SMA5-10_temp_for%20Athens_and_Global.PNG)
> fig 1: SMA 5 and 10 years plotted for average temperatures in Athens and globaly

2. To have a better view and possibility for comparison, I printed and calculated the difference between the avergare temp in Athens against what globaly shows.

![fig 2: Difference between the SMA 10 of the avergae temperature in Athens compared to the global average](https://raw.githubusercontent.com/universalamateur/Udacity_Data_Analyst_Nanodegree/main/Exploring%20Weather%20Trends%20-%20Project/Plot_Graphics/Dif_SMA10_temp_Athens_and_Global.PNG)
> fig 2: Difference between the SMA 10 of the avergae temperature in Athens compared to the global average

The calculations resultes in:

- Mean of the avergae yearly temp:  9.052490421455937 ºC
- Mean of the average SMA 5 temp:  9.05139299610896 ºC
- Mean of the average SMA 10 temp:  9.052396825396832 ºC

==> I will use as a correction for a plot the average difference of 9.05 ºC between the average temperature globaly to that of Athens.

3. To better compare the local and global trend I have arranged the correction z-axis shift for the global temperature in this plot

![fig 3: SMA 10 years plotted for average temperatures in Athens and globaly for trend comparison](https://raw.githubusercontent.com/universalamateur/Udacity_Data_Analyst_Nanodegree/main/Exploring%20Weather%20Trends%20-%20Project/Plot_Graphics/SMA10_with_Correction_temp_for_Athens_and_Global.PNG)
> fig 3: SMA 10 years plotted for average temperatures in Athens and globaly for trend comparison

## Observations

The Trend of the Moving Average I will show in an abstracted form in fig 4 to show also my observations.


1. As we have seen in our calculation and in fig 2, the difference between the global average temperature or its Moving Averge over 5 or 10 years stays within 1ºC and is in Average roughly 9ºC. That means the average temperature in Athen localy is 9ºC higher then the global Average, which is explained through Athens location on 37° Latitude, similar as San Francisco, USA. (A data Project for later days).
2. The Trend for the local and the global temperature are very similar.
3. Between 1830 and 1845 was a short period of very low average temperatures localy in Athens and globaly periods.
4. Between 1970 and 1980 the local and global temperature average has grown more rapidly than before.
5. The Average temperature after 2010 is roughly 1ºC higher localy and globaly than the measurements around 1760.

---

## Definitions

**Simple Moving Average** (SMA)
  : Simple Moving Average (SMA) uses a sliding window to take the average over a set number of time periods. It is an equally weighted mean of the previous n data.  
**Full Outer Join**
  : in SQL the FULL OUTER JOIN combines the results of both left and right outer joins and returns all (matched or unmatched) rows from the tables on both sides of the join clause.

## Attachments
