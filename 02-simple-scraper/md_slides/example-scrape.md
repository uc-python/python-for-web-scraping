class: center, middle

## #2
# Example: Pulling the Kroger Balance Sheet 

---
# Our Mission

- We want to pull the Kroger balance sheet for fiscal year 2020 into Pandas and extract:

  - Total assets, total liabilities, and total equity

  - For both fiscal year 2020 and fiscal year 2019

- By interactively [searching Edgar](https://www.sec.gov/edgar/search-and-access), we were able to track down the URL for an HTML version of their 10k 
  - It's important that it's the HTML version! This won't work on a PDF, inline image, or other non-HTML format

- That URL is [https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm](https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm)

---
# Preparation

- First off, this is a big document. We need to find the balance sheet so we know what the data we're trying to extract will look like, and where it is.

- A search within the document for "Consolidated Balance Sheet" is a decent way to start.

- Eventually, we can track down the table, which is on **page 48**.

---
# Preparation

<center><img src="assets/raw_balance_sheet.png" width="50%"/></center>

---
# Preparation

- We're going to use Pandas to pull all tables in this document, but need a way to distinguish this one from all the others.

- What's a phrase that likely occurs in this table but not in any others?

  - Let's start with `"Common shares"`

  - Case sensitive!

- Worst case: If it turns out that this string is in other tables too, we'll just get multiple tables back and have to look through them all.

---
# Pulling Data

- First, import the packages we need: `pandas` for DataFrames and `requests` for pulling web data

```python
* import requests
* import pandas as pd
```

---
# Pulling Data

- Then, create variables storing the URL and the text we're using to find the right table

```python
  import requests
  import pandas as pd

* URL = 'https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm'
* PATTERN = 'Common shares'
```

---
# Pulling Data

- Use the requests library to issue a GET request to the URL and pull back the content of the response

```python
  import requests
  import pandas as pd

  URL = 'https://www.sec.gov/Archives/edgar/data/56873/000155837021003706/kr-20210130x10k.htm'
  PATTERN = 'Common shares'

* html = requests.get(URL).content
```

---
# Pulling Data

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
# Pulling Data

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
# Pulling Data

- Luckily, in this case, only one table comes back -- our text pattern was sufficiently specific!

<br>

```python
len(result)
```
```
1
```

---
# Pulling Data

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
# Result

<img src="assets/balance_sheet_df.png" width="70%"/>

... it goes on

---
# Result

- So ... this is not really what we might have imagined!

  - Columns have useless names

  - The real column names are split into two rows (`January 30,` and `2021` are in separate cells)

  - Dollar signs have ended up in their own columns!

  - Row names ended up in the first column, not the row labels

  - And more

--

- **This is where our data wrangling skills with Pandas come in!**

---
# Post-processing

- You're often (*usually*) going to need to some post-processing on data you pull from the web.

- Luckily, in this case we don't need to make the table perfect in order to pull out the info we need.

  - We'll just drop empty columns and update row & column labels to make it easier to work with.

---
# Post-processing

- First off, let's rename the columns more sensibly

  - While we're at it, we can make certain columns that should be dropped

--

```python
# I just did this by visual inspection -- see which columns hold which data.
df.columns = ['label', 'drop_1', 'drop_2', 'fy_2020', 'drop_3', 'drop_4', 'fy_2021', 'drop_5']
```

--

```python
# axis=1 is required so Pandas knows these are columns, not rows
df = df.drop(['drop_1', 'drop_2', 'drop_3', 'drop_4', 'drop_5'], axis=1)
```

---
# Post-processing

<center><img src="assets/balance_sheet_df_col_cleanup.png" width="40%"/></center>

---
# Post-processing

- Definitely progress!

---
# Post-processing

- Since the first three rows are now useless, we can drop them too.

```python
# Note axis=0 to drop rows
df = df.drop([0, 1, 2], axis=0)
```

--

- The remaining rows all have names in the `"label"` column, so we can make those the row labels for easier lookups.

```python
df = df.set_index('label')
```

---
# Post-processing

<center><img src="assets/balance_sheet_df_full_cleanup.png" width="40%"/></center>

---
# Extraction

- At last, we can extract the information we want!

- With our newly-clean data, we can easily do lookups with the `.loc` syntax we already know:

  - `df.loc[row_label, column_label]`

--

```python
df.loc['Total Assets', 'fy_2020']
```
```
48662
```

--
```python
df.loc['Total Equity', 'fy_2021']
```
```
8573
```

---
# Extraction

- More elegantly, if we wanted to get all the data at once and then save it to a file...

```python
extracted = df.loc[['Total Assets', 'Total Liabilities', 'Total Equity']]
extracted
```

<center><img src="assets/balance_sheet_df_extracted.png" width="30%"/></center>

--

```python
extracted.to_csv(path_to_my_saved_data)
```

---
class: center, middle

## Questions
