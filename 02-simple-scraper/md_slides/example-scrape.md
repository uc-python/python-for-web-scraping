class: center, middle

## #2
# Example: Pulling the Kroger Balance Sheet 

---
# Our Mission

- We want to pull the Kroger balance sheet for fiscal year 2020 into Pandas

- By interactively [searching Edgar](https://www.sec.gov/edgar/search-and-access), we were able to track down the URL for an HTML version of their 10k 
  - It's important that it's the HTML version! This won't work on a PDF, inline image, or other non-HTML format

- That URL is [https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm](https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm)

---
# Preparing

- First off, this is a big document. We need to find the balance sheet so we know what the data we're trying to extract will look like, and where it is.

- A search within the document for "Consolidated Balance Sheet" is a decent way to start.

- Eventually, we can track down the table, which is on **page 48**.

---
# Preparing

- We're going to use Pandas to pull all tables in this document, but need a way to distinguish this one from all the others.

- What's a phrase that likely occurs in this table but not in any others?

  - Let's start with `"Common shares"`

  - Case sensitive!

- Worst case: If it turns out that this string is in other tables too, we'll just get multiple tables back and have to look through them all.

---
# Code

- First, import the packages we need: `pandas` for DataFrames and `requests` for pulling web data

```python
* import requests
* import pandas as pd
```

---
# Code

- Then, create variables storing the URL and the text we're using to find the right table

```python
  import requests
  import pandas as pd

* URL = 'https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm'
* PATTERN = 'Common shares'
```

---
# Code

- Use the requests library to issue a GET request to the URL and pull back the content of the response

```python
  import requests
  import pandas as pd

  URL = 'https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm'
  PATTERN = 'Common shares'

* html = requests.get(URL).content
```

---
# Code

- Have Pandas parse through HTML content looking for tables that contain our pattern

```python
  import requests
  import pandas as pd

  URL = 'https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm'
  PATTERN = 'Common shares'

  html = requests.get(URL).content
* result = pd.read_html(html, match=PATTERN)
```

---
# Code

- `result` will always be a list, filled with all the DataFrames that Pandas found meeting our criterion

<br>

```python
  type(result)
```
```
list
```

<br>

```python
  type(result[0])
```
```
pandas.core.frame.DataFrame
```

---
# Code

- Luckily, in this case, only one table comes back -- our text pattern was sufficiently specific!

<br>

```python
len(result)
```
```
1
```

---
# Code

- We can extract the first (and only) element of the list the same way we've seen before, `[0]`

```python
  import requests
  import pandas as pd

  URL = 'https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm'
  PATTERN = 'Common shares'

  html = requests.get(URL).content
  result = pd.read_html(html, match=PATTERN)

* df = result[0]
```

---
# Code

<img src="assets/balance_sheet_df.png" width="80%"/>

---
class: center, middle

## Questions
