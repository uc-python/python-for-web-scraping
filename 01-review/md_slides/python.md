class: center, middle

## #2
# Basic Python

---

# Basic Data Types

--

- **integers** (`int`): Whole numbers, positive or negative or zero

  - e.g. `3`,&nbsp;&nbsp;`0`,&nbsp;&nbsp;`-531`

--

- **floats** (`float`): Decimal numbers

  - e.g. `3.14`,&nbsp;&nbsp;`0.0004`,&nbsp;&nbsp;`-878.482`

--

- **strings** (`str`): Arbitrary text

  - e.g. `"hello"`,&nbsp;&nbsp;`'my name is ethan'`,&nbsp;&nbsp;""

--

- **booleans** (`bool`): Logical values `True` and `False`

  - `True`,&nbsp;&nbsp;`False` -- that's it


---

# Container Types

- Python also has some objects that can "contain" others...

---

# Container Types

**lists** (`list`): Ordered, 1-dimensional sequences of objects

  - Elements may be different types of things.

--

```python
my_list = ['a', 'b', 3, 84.51, False]

# Elements can be accessed by index (which counts from 0!):
mylist[1]
```
```
"b"
```

---

# Container Types


**dictionaries** (`dict`): Mappings from "keys" to "values", good for looking up entries by their key
  
--

```python
my_dict = {
  'address': '123 Oak Street',
  'city': 'Chicago',
  'bedrooms': 2,
  'bathrooms': 1,
  'rent': 1599.99
}

# Values can be "looked up" by key
my_dict['bedrooms']
```
```
2
```

---

# Other Types

- There are many many more data types in Python that you may hear about, but these (along with DataFrames, covered next) are the ones we'll mostly be using.

- The general term for a Python "thing" (of any type) is an **object**.


---
class: center, middle

## Questions
