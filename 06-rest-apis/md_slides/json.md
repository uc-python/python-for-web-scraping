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

---
name: italy-json

# JSON in the REST Countries API

```python
endpoint_url = 'https://restcountries.eu/rest/v2/name/'
country = 'italy'
full_url = endpoint_url + country
response = requests.get(full_url)
```

---
template: italy-json

<br>

- Let's go back to our Countries API example.

- Recall that we pulled information on Italy but it came back as "bytes", and we didn't know how to turn it into a Python object we could use

---
template: italy-json

```python
response.content
```
```
b'[{"name":"Italy","topLevelDomain":[".it"],"alpha2Code":"IT","alpha3Code":"ITA","callingCodes":["39"],"capital":"Rome",
"altSpellings":["IT","Italian Republic","Repubblica italiana"],"region":"Europe","subregion":"Southern Europe",
"population":60665551,"latlng":[42.83333333,12.83333333],"demonym":"Italian","area":301336.0,...'
```

---
name: italy-json-parsed
template: italy-json

- But now we can see that this is JSON, and we know how to parse it!

```python
import json
italy_info = json.loads(response.content)
```

---
template: italy-json-parsed
```python
italy_info
```
```
[{'name': 'Italy',
  'topLevelDomain': ['.it'],
  'alpha2Code': 'IT',
  'alpha3Code': 'ITA',
  'callingCodes': ['39'],
  'capital': 'Rome',
  'altSpellings': ['IT', 'Italian Republic', 'Repubblica italiana'],
  'region': 'Europe',
  'subregion': 'Southern Europe',
  ...
}]
```

---
template: italy-json-parsed

```python
type(italy_info)
```
```
list
```

```python
italy_info[0]['capital']
```
```
'Rome'
```

---
template: italy-json

- It's so common for HTTP responses to have JSON content that `Response` objects have a `.json()` method that parses the JSON automatically

```python
# Equivalent to json.loads(response.content):
italy_info = response.json()
```
```
[{'name': 'Italy',
  'topLevelDomain': ['.it'],
  'alpha2Code': 'IT',
  'alpha3Code': 'ITA',
  'callingCodes': ['39'],
  'capital': 'Rome',
  'altSpellings': ['IT', 'Italian Republic', 'Repubblica italiana'],
  'region': 'Europe',
  'subregion': 'Southern Europe',
  ...
}]
```

---

# JSON in the REST Countries API

- The full JSON object returned in this case is too big for one slide, and this isn't even a "large" response relative to many APIs

```
[{'name': 'Italy',
  'topLevelDomain': ['.it'],
  'alpha2Code': 'IT',
  'alpha3Code': 'ITA',
  'callingCodes': ['39'],
  'capital': 'Rome',
  'altSpellings': ['IT', 'Italian Republic', 'Repubblica italiana'],
  'region': 'Europe',
  'subregion': 'Southern Europe',
  'population': 60665551,
  'latlng': [42.83333333, 12.83333333],
  'demonym': 'Italian',
  'area': 301336.0,
  'gini': 36.0,
  'timezones': ['UTC+01:00'],
  'borders': ['AUT', 'FRA', 'SMR', 'SVN', 'CHE', 'VAT'],
  'nativeName': 'Italia',
  'numericCode': '380',
  'currencies': [{'code': 'EUR', 'name': 'Euro', 'symbol': '€'}],
  'languages': [{'iso639_1': 'it',
    'iso639_2': 'ita',
    'name': 'Italian',
    'nativeName': 'Italiano'}],
  'translations': {'de': 'Italien',
   'es': 'Italia',
   'fr': 'Italie',
   'ja': 'イタリア',
   'it': 'Italia',
   'br': 'Itália',
   'pt': 'Itália',
   'nl': 'Italië',
   'hr': 'Italija',
   'fa': 'ایتالیا'},
  'flag': 'https://restcountries.eu/data/ita.svg',
  'regionalBlocs': [{'acronym': 'EU',
    'name': 'European Union',
    'otherAcronyms': [],
    'otherNames': []}],
  'cioc': 'ITA'}]
```

---

# JSON in the REST Countries API

- You can see that certain fields are "deeply nested" -- to access them, you need to dig deep in the structure

```python
italy_info = response.json()
italy_currency_name = italy_info[0]['currencies'][0]['name']
```
```python
italy_currency_name
```
```
'Euro'
```

---
name: italy-switzerland

# Dealing with JSON

- Getting the info you want out of JSON can be a time-consuming process, requiring you to look carefully at the structure of the object

- However, most APIs return JSON with similar (or identical) structure if you query them for the same type of things

--

```python
endpoint_url = 'https://restcountries.eu/rest/v2/name/'
italy_info = requests.get(endpoint_url + 'italy').json()
switzerland_info = requests.get(endpoint_url + 'switzerland').json()
```

---
template: italy-switzerland

```python
italy_info[0]
```
```
{'name': 'Italy',
 'topLevelDomain': ['.it'],
 'alpha2Code': 'IT',
 'alpha3Code': 'ITA',
 'callingCodes': ['39'],
 'capital': 'Rome',
 'altSpellings': ['IT', 'Italian Republic', 'Repubblica italiana'],
 'region': 'Europe',
 'subregion': 'Southern Europe',
 'population': 60665551,
 'latlng': [42.83333333, 12.83333333],
 'demonym': 'Italian',
 'area': 301336.0,
 'gini': 36.0,
 ...
}
```

---
template: italy-switzerland

```python
switzerland_info[0]
```
```
{'name': 'Switzerland',
 'topLevelDomain': ['.ch'],
 'alpha2Code': 'CH',
 'alpha3Code': 'CHE',
 'callingCodes': ['41'],
 'capital': 'Bern',
 'altSpellings': ['CH',
  'Swiss Confederation',
  'Schweiz',
  'Suisse',
  'Svizzera',
  'Svizra'],
 'region': 'Europe',
 ...
}
```

---
template: italy-switzerland

<br>
- And, if you structure your deep queries properly, they can work across multiple results from the API

```python
italy_info[0]['currencies'][0]['name']
```
```
Euro
```

```python
switzerland_info[0]['currencies'][0]['name']
```
```
Swiss franc
```
