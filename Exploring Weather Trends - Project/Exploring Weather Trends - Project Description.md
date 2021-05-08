# Exploring Weather Trends - Project Instructions

## Summary

In this project, you will analyze local and global temperature data and compare the temperature trends where you live to overall global temperature trends.

## Instructions

Your goal will be to create a visualization and prepare a write up describing the similarities and differences between global temperature trends and temperature trends in the closest big city to where you live. To do this, you’ll follow the steps below:

1. Extract the data from the database. There's a workspace in the next section that is connected to a database. You’ll need to export the temperature data for the world as well as for the closest big city to where you live. You can find a list of cities and countries in the city_list table. To interact with the database, you'll need to write a SQL query.
2. Write a SQL query to extract the city level data. Export to CSV.
3. Write a SQL query to extract the global data. Export to CSV.
4. Open up the CSV in whatever tool you feel most comfortable using. We suggest using Excel or Google sheets, but you are welcome to use another tool, such as Python or R.
5. Create a line chart that compares your city’s temperatures with the global temperatures. Make sure to plot the moving average rather than the yearly averages in order to smooth out the lines, making trends more observable (the last concept in the previous lesson goes over how to do this in a spreadsheet).
6. Make observations about the similarities and differences between the world averages and your city’s averages, as well as overall trends. Here are some questions to get you started.
Is your city hotter or cooler on average compared to the global average? Has the difference been consistent over time?
“How do the changes in your city’s temperatures over time compare to the changes in the global average?”
What does the overall trend look like? Is the world getting hotter or cooler? Has the trend been consistent over the last few hundred years?

## Submission

Your submission should be a PDF that includes:

1. An outline of steps taken to prepare the data to be visualized in the chart, such as:
2. What tools did you use for each step? (Python, SQL, Excel, etc)
3. How did you calculate the moving average?
4. What were your key considerations when deciding how to visualize the trends?
5. Line chart with local and global temperature trends
6. At least four observations about the similarities and/or differences in the trends

## Criteria

|CRITERIA|MEETS SPECIFICATIONS|
|---|---|
|Student is able to extract data from a database using SQL.|<ul><li>The SQL query used to extract the data is included.</li><li>The query runs without error and pulls the intended data.</li></ul>|
|Student is able to manipulate data in a spreadsheet or similar tool.|Moving averages are calculated to be used in the line chart.|
|Student is able to create a clear data visualization.|<ul><li>A line chart is included in the submission.</li><li>The chart and its axes have titles, and there's a clear legend (if applicable).</li></ul>|
Student is able to interpret a data visualization.|<ul><li>The student includes four observations about their provided data visualization.</li><li>The four observations are accurate.</li></ul>|
