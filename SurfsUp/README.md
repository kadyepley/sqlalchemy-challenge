# sqlalchemy-challenge

## Reflect Tables into SQLAlchemy ORM

First, I imported the dependencies, created the engine, and saved the reference names for the tables that I would use later to query through their data.

## Exploratory Precipitation Analysis

To start the analysis of the precipitation data, I used the max function in my querying of the Measurment table to get the most recent date in the dataset. 

I used a quick formula of the most recent date minus 365 days to get the start date for the dataset. This would feed into the query I would perform to filter the data for just the date and precipitation columns beginning after the row with the start date. 

The filtered data could then be plotted in a bar graph and the summary statistics could be run to get the general information about the precipitation each day over the past year. 

## Exploratory Station Analysis 

The next step of analyzing station data would be to query the station data from the Measurements table using the count function to get the number of stations in the dataset. 

I then queried the data in the Measurment table to display the station and the count of the rows that this station showed up in the table. This would be grouped by each of the 9 stations and in order of the station with the highest number of rows in the table to the least. In doing this I identified the most active station as the station at the top of my list, USC00519281.

Next, I used the minimum, maximum, and average functions to query the data filtered for the rows where the station equals USC00519281, the most active station id. 

To make my histogram displaying the frequency of each temperature throughout the past year for the most active station, I queried the data for the 'tobs' column with the filters for the station equaling USC00519281 and the dates after the start date of 2017-08-23.

Once this was displayed, I closed the session.

## Creating the app for API access

I set up the homepage with all the dependencies and the same references to each table used previously. I created all the API routes for inquiry the user may have, precipitation, stations, tobs, and data based on start and end date.

Before working on any of the APIs I would need to first establish how far back the data would go by defining the start date. I used the same date already indentifed to perform a query pulling only the data from the last year. 

For the API for precipitation, I created a list for the preciptation data to be populated by the dictionary for both the dates and their precipitation data. After appending this list, I then returned a JSON representation of the dictionary using jsonify.

For the Stations page, I queried for the stations column in the Station table and used the list function to generated the list of tuples. I then returned a JSON representation of the list using jsonify.

The Tobs page started with a query for the data where the data was more than or equal to the first date in the dataset defined previously. Similarly to the precipitation page, the data filtered for the past years dates would then be added to a list as appended dictionaries for the dates and the tobs columns. Using jsonify, I produced a JSON representation of the list. 

The last two pages would the Start Date and Start-End Range data pulls. I created the list for the data I waned to query for, the minimum, average, and maximum tobs. I then looped through this data to filter for the dates after the start date and to return this as a JSON representation. Using else, I then added the additional filter for a start date and end date, resulting in a JSON representation as well. 