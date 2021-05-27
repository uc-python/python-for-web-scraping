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

# REST Countries API

- This API, like many available on the internet, is very well-documented:

<img src="assets/name_endpoint_doc.png" width="100%"/>

--

- On the right, you see the general syntax: `https://restcountries.eu/rest/v2/name/{name}`

  - The `{name}` in braces is meant to be replaced by an actual country name (without braces)

- The following two URLs are examples of how you might call this endpoint

---

# REST Countries API

- Let's try it! We'll get information about Italy.

  - First, we need to create a URL that contains the country name, our own "parameter"

  - Then we can issue a GET request (that should look familiar!)

```python
endpoint_url = 'https://restcountries.eu/rest/v2/name/'
country = 'italy'
full_url = endpoint_url + country

response = requests.get(full_url)
response
```
```
<Response [200]>
```
