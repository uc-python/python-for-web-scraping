class: center, middle

## #3
# Selecting, Indexing, and Filtering

---

# Subsetting Data

- Before you do much else, you need to be able to get at pieces of a DataFrame that you're interested in.

- This usually means limiting to certain columns, to certain rows, or both at the same time.

---

# Selecting

- Subsetting data by its columns is often called **selecting**

  - You might say "select the name column from the data"

- The syntax to select a single column is `df[column_name]`

  - This returns a **series** object, a 1-dimensional Pandas object

  - Series are a lot like Python lists, except all the data in them is usually of the same type

---

# Selecting

```python
planes_df['seats']
```
```
0        55
1       182
2       182
3       182
4        55
       ... 
3317    100
3318    142
3319    100
3320    142
3321    142
Name: seats, Length: 3322, dtype: int64
```
<br>

- Remember, this isn't a DataFrame, it's a Series
  - One way to tell is the bottom line, which says the name of the column, the length (number of entries), and the type of the elements in it.

---

# Selecting

- Selecting multiple columns is done with double brackets

  - The inner brackets indicate to Pandas that you're passing a *list of columns*

- Using double brackets returns a DataFrame, not a Series
  
  - You can even use double brackets with a single column if you don't want a Series

---

# Selecting

```python
planes_df[['seats', 'tailnum']]
```
```
      seats tailnum
0        55  N10156
1       182  N102UW
2       182  N103US
3       182  N104UW
4        55  N10575
...     ...     ...
3317    100  N997AT
3318    142  N997DL
3319    100  N998AT
3320    142  N998DL
3321    142  N999DN

[3322 rows x 2 columns]
```

---

# Selecting

- `['seats', 'tailnum']` is actually a list we pass into `planes_df[]`, which is why we get a 2-dimensional object (a DataFrame) back.

```python
columns = ['seats', 'tailnum']
planes_df[columns]
```
```
      seats tailnum
0        55  N10156
1       182  N102UW
2       182  N103US
3       182  N104UW
4        55  N10575
...     ...     ...
3317    100  N997AT
3318    142  N997DL
3319    100  N998AT
3320    142  N998DL
3321    142  N999DN

[3322 rows x 2 columns]
```

---

# Indexing

- "Indexing" is the word we use for subsetting rows based on their location or row label.

---
class: center, middle

## Questions
