# Rest APIs Lab

<br><br>

## 1. A Basic API Query

Query the Rest Countries API ([restcountries.eu](https://restcountries.eu)) by country name.
Search for Yemen.

a) What is its capital?

b) What is the name of its primary language?

c) How many regional blocs is it in?

<br>

## 2. Counting Results

Look over the documentation for the Rest Countries API.
Using the API, check how many countries use the US Dollar (code: `usd`)?

<br>

## 3. JSON as a DataFrame

Use the "all" endpoint to fetch all countries.
Convert the results into a Pandas DataFrame.

What is the average population?

What is the average population *by region*?

<br>

## 4. Passing Parameters

The Hipo Labs API allows you to search for universities in a given country.
The endpoint for this service is `http://universities.hipolabs.com/search`, and it accepts GET requests with a parameter called "country".

Search for all universities in Luxembourg.
How many are there?

<br>

## 5. Wrangling University Data

Use the Hipo Labs API to get all univerities in the USA (search with parameter "United States").

Answer the following questions:

- Of the universities with a state/provice labeled (which is actually not many), which state has the most? Which the fewest?

- What is the greatest number of web pages that any university has? Note that the web_pages field contains lists, so you will need to find a way to convert these to counts.

Then, drop the `country` column, set the row labels to be the `name` column, and save the data to a file called `universities.csv`.
