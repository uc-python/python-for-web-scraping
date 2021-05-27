class: center, middle

## #3
# JSON

---

# JSON

- JSON is, in some ways, the lingua franca of internet data

- Originally stood for *JavaScript Object Notation*
    
    - JavaScript is the scripting language used within web pages

- JSON provides a way to convert data to text, so we can send it across the internet and anyone who receives it understands how to decode it

---
name: json-syntax

# JSON

- Conveniently for us, JSON looks almost identical to Python syntax

    - Usually nested lists and dictionaries

    - Atomic elements can be strings, numbers, booleans, or *null* (like `None`)

---
template: json-syntax

<br>

```javascript
{"first_name": "Ethan", "last_name": "Swan", "height_in_inches": 71.5, "is_employed": true, "name_of_pet": null}
```

- Notice subtle differences: `true` instead of `True`, and `null` instead of `None`

---
name: json-loading

# JSON Loading

- Lucky for us, Python knows how to convert JSON into native Python objects via the `json` library (which ships with Python)

```python
# Our JSON from before, stored in a string:
j = '{"first_name": "Ethan", "last_name": "Swan", "height_in_inches": 71.5, "is_employed": true, "name_of_pet": null}'
```

---
template: json-loading

```python
import json
# loads means "LOAD from String"
ethan = json.loads(j)
ethan
```
```
{'first_name': 'Ethan',
 'last_name': 'Swan',
 'height_in_inches': 71.5,
 'is_employed': True,
 'name_of_pet': None}
```

- Notice that this is regular Python! `True` and `None` are clues.

---
template: json-loading

```python
import json
# loads means "LOAD from String"
ethan = json.loads(j)
print(ethan['last_name'])
print(ethan['height_in_inches'])
```
```
Swan
71.5
```

- We can access fields and otherwise treat this like any other Python data structure once we've converted it from JSON.

---
name: json-loading-nested

# JSON Loading

- JSON we get on the web is usually a list or a dictionary, and often contains other lists/dictionaries inside it.

```python
j = '[{"company": "Kroger", "prices": [15.38, 201.34]}, {"company": "Apple", "prices": [103.13, 111.58]}]'
```
<br>

---
template: json-loading-nested

```python
result = json.loads(j)
result
```
```
[{'company': 'Kroger', 'prices': [15.38, 201.34]},
 {'company': 'Apple', 'prices': [103.13, 111.58]}]
```

```python
type(result)
```
```
list
```

```python
result[0]
```
```
{'company': 'Kroger', 'prices': [15.38, 201.34]}
```

---
template: json-loading-nested

- For JSON that's structured as a list of records (like this one), Pandas even knows how to convert it into a DataFrame automatically!

```python
import pandas as pd
df = pd.read_json(j)
```
```python
df
```
```
  company            prices
0  Kroger   [15.38, 201.34]
1   Apple  [103.13, 111.58]
```
