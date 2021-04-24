class: center, middle

## #4
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

- Using double brackets returns a **DataFrame**, not a Series
  
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

- Most things in Python index from 0.

  - That means an sequence with 3 elements would label them #0, #1, and #2.

- DataFrames have row indexes, as we've discussed before.

  - You can think of them as row labels.

  - By default, they're just integers from 0 to (number_of_rows - 1).

---

# Indexing

- Here, the indices are 0-4.

<img src="assets/basic_dataframe.png" style="width:100%;"/>

---

# Indexing

- Indices can be selected using `df.loc` and brackets.

```python
# Fetch the 3rd row (because we start counting at 0!)
planes_df.loc[2]
```
```
tailnum                          N103US
year                             1999.0
type            Fixed wing multi engine
manufacturer           AIRBUS INDUSTRIE
model                          A320-214
engines                               2
seats                               182
speed                               NaN
engine                        Turbo-fan
Name: 2, dtype: object
```

--

- Like selecting a single column, indexing a single row returns a **Series**, not a DataFrame.

  - Because, again, it's a 1-dimensional object.

---

# Indexing

- DataFrames can also be indexed with a *range*, instead of a single row index.

- This uses the same `df.loc` syntax, except a range is passed
  
  - `df.loc[starting_index:ending_index]`

```python
# Get rows at index 3 through index 6 (inclusive)
planes_df.loc[3:6]
```
```
  tailnum    year                     type      manufacturer      model  engines  seats  speed     engine  
3  N104UW  1999.0  Fixed wing multi engine  AIRBUS INDUSTRIE   A320-214        2    182    NaN  Turbo-fan  
4  N10575  2002.0  Fixed wing multi engine           EMBRAER  EMB-145LR        2     55    NaN  Turbo-fan  
5  N105UW  1999.0  Fixed wing multi engine  AIRBUS INDUSTRIE   A320-214        2    182    NaN  Turbo-fan  
6  N107US  1999.0  Fixed wing multi engine  AIRBUS INDUSTRIE   A320-214        2    182    NaN  Turbo-fan  
```

---

# Combining Selecting and Indexing

- You can select columns and index rows all at once using `df.loc[row_index, columns]`

```python
# Row indices 3-6, columns "seats" and "tailnum"
planes_df.loc[3:6, ['seats', 'tailnum']]
```
```
   seats tailnum
3    182  N104UW
4     55  N10575
5    182  N105UW
6    182  N107US
```

---
class: padded-table

# Combining Selecting and Indexing

| Goal | Syntax |
|:- |:- | 
| Select columns | `df[columns]` |
| Index rows | `df.loc[row_indices]` |
| Select columns *and* index rows | `df.loc[row_indices, columns]` |

---

# Filtering

- *Filtering* means limiting rows based on a condition of the data

  - e.g. "all rows where the number of engines is greater than 2"

- This is also done with `df.loc`, but you pass in an expression describing which rows to keep.

---

# Filtering

```python
# This syntax is a little clunky; the DataFrame name is specified twice.
planes_df.loc[planes_df['engines'] > 2]
```
```
     tailnum    year                     type            manufacturer              model  engines  seats  speed
603   N281AT     NaN  Fixed wing multi engine        AIRBUS INDUSTRIE           A340-313        4    375    NaN
1037  N381AA  1956.0  Fixed wing multi engine                 DOUGLAS             DC-7BF        4    102  232.0
2109  N670US  1990.0  Fixed wing multi engine                  BOEING            747-451        4    450    NaN
2706  N840MQ  1974.0  Fixed wing multi engine            CANADAIR LTD              CF-5D        4      2    NaN
2764  N854NW  2004.0  Fixed wing multi engine                  AIRBUS           A330-223        3    379    NaN
2771  N856NW  2004.0  Fixed wing multi engine                  AIRBUS           A330-223        3    379    NaN
2931  N905FJ  1986.0  Fixed wing multi engine  AVIONS MARCEL DASSAULT MYSTERE FALCON 900        3     12    NaN
```


<br><br><br>
.footnote[*Note to the eagle-eyed observer: I omitted the final column here for space considerations*]

---

# Filtering

```python
planes_df.loc[planes_df['seats'] == 139]
```
```
     tailnum    year                     type       manufacturer    model engines  seats  speed     engine  
1813  N600TR  1979.0  Fixed wing multi engine  MCDONNELL DOUGLAS  DC-9-51       2    139  432.0  Turbo-jet  
2131  N675MC  1975.0  Fixed wing multi engine  MCDONNELL DOUGLAS  DC-9-51       2    139  432.0  Turbo-jet  
2402  N762NC  1976.0  Fixed wing multi engine  MCDONNELL DOUGLAS  DC-9-51       2    139  432.0  Turbo-jet  
2432  N767NC  1977.0  Fixed wing multi engine  MCDONNELL DOUGLAS  DC-9-51       2    139  432.0  Turbo-jet  
2472  N774NC  1978.0  Fixed wing multi engine  MCDONNELL DOUGLAS  DC-9-51       2    139  432.0  Turbo-jet  
2483  N777NC  1979.0  Fixed wing multi engine  MCDONNELL DOUGLAS  DC-9-51       2    139  432.0  Turbo-jet  
2492  N779NC  1979.0  Fixed wing multi engine  MCDONNELL DOUGLAS  DC-9-51       2    139  432.0  Turbo-jet  
2503  N782NC  1980.0  Fixed wing multi engine  MCDONNELL DOUGLAS  DC-9-51       2    139  432.0  Turbo-jet 
```

---

# Combining Selecting and Filtering

- Like indexing, filtering can be combined with selecting in the `.loc` brackets.

  - `df.loc[row_filter, columns]`

<br>
```python
planes_df.loc[planes_df['seats'] == 139, ['seats', 'tailnum']]
```
```
      seats tailnum
1813    139  N600TR
2131    139  N675MC
2402    139  N762NC
2432    139  N767NC
2472    139  N774NC
2483    139  N777NC
2492    139  N779NC
2503    139  N782NC
```

---
class: padded-table

# Combining Selecting and Filtering

So we can update our syntax chart...

| Goal | Syntax |
|:- |:- | 
| Select columns | `df[columns]` |
| Index rows | `df.loc[row_indices]` |
| Select columns *and* index rows | `df.loc[row_indices, columns]` |
| Filter rows | `df.loc[filter_condition]` |
| Select columns *and* filter rows | `df.loc[filter_condition, columns]` |

--

- Generally:

  - Columns: `df[columns]`

  - Rows: `df.loc[rows]`

  - Both: `df.loc[rows, columns]`

---
class: center, middle

## Questions
