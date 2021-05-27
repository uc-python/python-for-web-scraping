class: center, middle

## #2
# Pulling Data from a Rest API

---

# REST Countries API

- The REST Countries API offers multiple endpoints (URLs)

<center><img src="assets/endpoints_list.png"/></center>

---

# REST Countries API

- Each of these endpoints represents a different way to interact with the API.

  - Each requires different parameters or returns a different result.

  - In this way (and many others!), Rest endpoints are a lot like functions. A single API service can have many endpoints, like a Python library contains many functions.

- Let's look at the *Name* endpoint.

---
name: name-endpoint-doc

# REST Countries API

- This API, like many available on the internet, is very well-documented:

<img src="assets/name_endpoint_doc.png" width="100%"/>

---
template: name-endpoint-doc

- On the right, you see the general syntax: `https://restcountries.eu/rest/v2/name/{name}`

  - The `{name}` in braces is meant to be replaced by an actual country name (without braces)

- The following two URLs are examples of how you might call this endpoint

---
template: name-endpoint-doc

<br>
- We can think of this endpoint as a function that takes one argument (`name`) and returns information about a country

---
name: italy-request

# REST Countries API

- Let's try it! We'll get information about Italy.

  - First, we need to create a URL that contains the country name, our own "parameter"

  - Then we can issue a GET request (that should look familiar!)

```python
endpoint_url = 'https://restcountries.eu/rest/v2/name/'
country = 'italy'
full_url = endpoint_url + country

response = requests.get(full_url)
```

---
template: italy-request

<br>
```python
response
```
```
<Response [200]>
```
- A 200 means success, so that's good!

---
template: italy-request

```python
response.content
```
```
b'[{"name":"Italy","topLevelDomain":[".it"],"alpha2Code":"IT","alpha3Code":"ITA","callingCodes":["39"],"capital":"Rome",
"altSpellings":["IT","Italian Republic","Repubblica italiana"],"region":"Europe","subregion":"Southern Europe",
"population":60665551,"latlng":[42.83333333,12.83333333],"demonym":"Italian","area":301336.0,...'
```
```python
type(response.content)
```
```
bytes
```
---
name: json-intro

# REST Countries API

```python
response.content
```
```
b'[{"name":"Italy","topLevelDomain":[".it"],"alpha2Code":"IT","alpha3Code":"ITA","callingCodes":["39"],"capital":"Rome",
"altSpellings":["IT","Italian Republic","Repubblica italiana"],"region":"Europe","subregion":"Southern Europe",
"population":60665551,"latlng":[42.83333333,12.83333333],"demonym":"Italian","area":301336.0,...'
```
```python
type(response.content)
```
```
bytes
```

- There's clearly information in the response's content, but it's a "bytes" object, which we haven't seen before

- It kind of looks like Python lists and dictionaries

- Is there a way we can translate it into a Python object?

