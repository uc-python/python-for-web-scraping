class: center, middle

## #5
# Summarizing Data

---

# DataFrame-level Summaries

- You can get quick summaries of all numeric columns in a DataFrame using `df.describe()`

```python
planes_df.describe()
```
```
              year      engines        seats       speed
count  3252.000000  3322.000000  3322.000000   23.000000
mean   2000.484010     1.995184   154.316376  236.782609
std       7.193425     0.117593    73.654974  149.759794
min    1956.000000     1.000000     2.000000   90.000000
25%    1997.000000     2.000000   140.000000  107.500000
50%    2001.000000     2.000000   149.000000  162.000000
75%    2005.000000     2.000000   182.000000  432.000000
max    2013.000000     4.000000   450.000000  432.000000
```

---

# DataFrame-level Summaries

- If you want summaries of string/categorical columns instead, use `df.describe(include='object')`

```python
planes_df.describe(include='object')
```
```
       tailnum                     type manufacturer    model     engine
count     3322                     3322         3322     3322       3322
unique    3322                        3           35      127          6
top     N663AW  Fixed wing multi engine       BOEING  737-7H4  Turbo-fan
freq         1                     3292         1630      361       2750
```

---

# Column-level Summaries

- Series (remember, individual columns are Series objects) offer lots of summary options.

- Usually they're invoked as `df[column].SUMMARY()` and return a single, scalar value.

---

# Column-level Numeric Summaries

- `df[column].mean()`

- `df[column].max()`

- `df[column].min()`

- `df[column].quantile(q=0.5) # Median`

<br>
```python
planes_df['year'].min()
```
```
1956.0
```


---

# Column-level Categorical Summaries

- `df[column].nunique() # Number of unique values`

- `df[column].value_counts() # Number of occurrences of each value, descending`

<br>
```python
planes_df['engine'].nunique()
```
```
6
```

```python
planes_df['type'].value_counts()
```
```
Fixed wing multi engine     3292
Fixed wing single engine      25
Rotorcraft                     5
Name: type, dtype: int64
```

<br>
- Note that `value_counts` is an exception to the rule -- it doesn't return a single number, but instead a *Series*.

---
class: center, middle

## Questions
