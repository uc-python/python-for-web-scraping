# BeautifulSoup Lab

<br><br>

This lab is fairly long; it's okay if you don't finish the entire thing.
Some of the later questions are meant to challenge you to solve new problems and require tools we haven't explicitly covered in lecture.

## 1. Another Fictional Character Wikipedia Page

The URL of the Wikipedia page for Harry Potter is `https://en.wikipedia.org/wiki/Harry_Potter_(character)`.
Scrape this page for the same details we looked at for Sherlock Holmes, Elizabeth Bennet, and Bilbo Baggins:
- Page title
- URL of the image of the character
- Full text of the page.

Save that result in a file called `harry.txt`. Look over its contents to confirm you fetched the information you expected, and follow the image URL (remember that you may need to add `https` at the beginning).

## 2. Looping Over Multiple Characters

Using Python's `for` loop, we can iterate through a collection of items and take actions on each.
The following code creates a list of dictionaries, where each dictionary represents a certain character and contains their page URL and the name of the file where their scraped data should be saved.
Loop through it, extract the same information from their page as you did from Harry Potter's, and store it in the appropriate filename.

```python
characters = [
    {'url': 'https://en.wikipedia.org/wiki/Prince_Caspian_(character)', 'filename': 'caspian.txt'},
    {'url': 'https://en.wikipedia.org/wiki/Oliver_Twist_(character)', 'filename': 'oliver_twist.txt'},
    {'url': 'https://en.wikipedia.org/wiki/Jay_Gatsby', 'filename': 'gatsby.txt'},
]
```

To get you started, your loop might begin like this:

```python
for character in characters:
    url = character['url']
    filename = character['filename']
    ...
```

In Jupyter, loops must be entirely defined in a single cell -- so you may need to condense your code.

**Bonus Challenge:** If you're familiar with writing functions, try to define a function `scrape_to_file` so that your loop can be simply the following:

```python
for character in characters:
    scrape_to_file(character['url'], character['filename'])
```

## 3. A New Page Format to Scrape: Yahoo Finance

The Yahoo Finance page for Kroger is located at [https://finance.yahoo.com/quote/KR](https://finance.yahoo.com/quote/KR).
Write a Python script or notebook to programmatically pull the current market cap for Kroger and save it to a file called `KR.txt`.

*Note* -- you may want to search for attributes other than ID and class in this problem (it's not required but could make this easier). If you choose to, you can look for custom attributes using `bs.find` via the `attrs` argument...
```python
bs.find(name='div', attrs={'custom-attribute-name': 'attribute-value'})
```

## 4. Multiple Yahoo Finance Pages

In general, a company's Yahoo Finance overview can be found by appending its ticker (e.g. KR) to the URL 'https://finance.yahoo.com/quote/'.
Write a loop to extract the market cap for each of the following tickers and save them in files named based on the company's ticker (e.g. Apple's market cap should be stored in `AAPL.txt`).

Tickers: AAPL, MSFT, GOOG, AMZN


Here is some code to get you started writing your loop:
```python
tickers = ['AAPL', 'MSFT', 'GOOG', 'AMZN']

for ticker in tickers:
    url = 'https://finance.yahoo.com/quote/' + ticker
    filename = ticker + '.txt'
    ...
```

## 5. Saving Multiple Results in a DataFrame.

So far, when scraping multiple pages we've saved each page's extracted data to a separate file.
However, to do analysis, we usually want all the data in a single file or database for easy loading and processing.

Update your solution to question 4 so that each ticker is a row in a Pandas DataFrame, rather than a separate file.
The columns should be named `"ticker"` and `"market_cap"`.

For example, the first row of the DataFrame might be

| ticker | market_cap |
| ----- | ----- | 
| AAPL | 2.118T |

**Bonus Challenge**: The current format of our market caps isn't ideal for numeric computation. Not only is it a string, but it's not trivially convertible to a number because it's abbreviated (e.g. 2.118T needs to become 2,118,000,000,000). Write code to update the market_cap column to be numeric, and then compute the average market cap of these companies.
