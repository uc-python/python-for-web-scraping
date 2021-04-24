class: center, middle

## #2
# Pandas DataFrames

---

# Pandas

- The Pandas package is the backbone of data analysis in Python

- Pandas is all about **DataFrames**, objects that store tabular data

  - The package was originally developed by financial analysts who wanted to do data analysis in Python, but needed an abstraction similar to DataFrames from the R language to do so.

- The funny name is short for **Pan**el **Da**ta

---

# DataFrames -- Basics

- DataFrames are tabular data

  - Think: DataFrames in R, tables in SQL, Datasets in SAS

- DataFrames have **column names** and **row indices**

<img src="assets/basic_dataframe.png" style="width:100%;"/>

---

# DataFrames -- Importing Data

- Easy to read in data from common formats (CSV, JSON, SQL databases)

- `pd.read_csv`, `pd.read_json`, `pd.read_excel`, `pd.read_sql` are several of the many options for importing data.

  - When reading from a flat file, just pass in the path to the file.

```python
df = pd.read_csv('data/my_data.csv')


df = pd.read_json('data/my_data.json')


df = pd.read_excel('data/my_spreadsheet.xlsx')


# SQL tables require first creating a connection to the database, which varies by type of DB
df = pd.read_sql('my_table', db_connection) 
```

- Other formats Pandas can read: parquet, fixed-width text, feather, Stata, SAS, pickle, HDF5

- Also can read from the web, which we'll come back to: **`pd.read_html`**

---

# DataFrames -- Inspecting Data

`df.head()` is usually the place to start -- returns the first 5 rows
<br><br><br><br>

```python
df.head()
```

<img src="assets/basic_dataframe.png" style="width:100%;"/>

---

# DataFrames -- Inspecting Data

Other options...

```python
df.shape # Return (n_rows, n_columns)
```

```
(3322, 9)
```

```python
df.columns # Return column names
```

```
Index(['tailnum', 'year', 'type', 'manufacturer', 'model', 'engines', 'seats',
       'speed', 'engine'],
      dtype='object')
```

---

# DataFrames -- Inspecting Data

`df.info()` gives a comprehensive overview, ideal when working interactively.

```python
df.info()
```

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 3322 entries, 0 to 3321
Data columns (total 9 columns):
 #   Column        Non-Null Count  Dtype  
---  ------        --------------  -----  
 0   tailnum       3322 non-null   object 
 1   year          3252 non-null   float64
 2   type          3322 non-null   object 
 3   manufacturer  3322 non-null   object 
 4   model         3322 non-null   object 
 5   engines       3322 non-null   int64  
 6   seats         3322 non-null   int64  
 7   speed         23 non-null     float64
 8   engine        3322 non-null   object 
dtypes: float64(2), int64(2), object(5)
memory usage: 233.7+ KB
```

---

# DataFrames -- Exporting Data

- Pandas can save data in most of the formats it supports importing from.

- Instead of `pd.read_FILETYPE`, it's usually `df.to_FILETYPE`

```python
df.to_csv('data/my_data.csv')


df.to_json('data/my_data.json')


# Again, you need an existing database connection to work with SQL.
df.to_sql('my_table', db_connection)
```


- We'll probably mostly save data in CSVs in this course, for simplicity.

---
class: center, middle

## Questions
