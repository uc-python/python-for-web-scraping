class: center, middle

## #2
# HTTP Status Codes

---

# What's the Deal with `<Response [200]>`

- We've often pulled data using `requests.get(url)`, which returns a `Response` object.

- Printing that reponse yields something like `<Response [200]>`

--

```python
import requests

response = requests.get('https://google.com/')
response
```
```
<Response [200]>
```

---

# What's the Deal with `<Response [200]>`

- 200 is the **status code** of the response we got from the web server

- 200 is the code for "OK"

  - Basically means: everything worked as expected.

- All codes in the 200s indicate *success*

  - e.g. 201 means that you requested to create data and that data creation was successful

---

# Status Codes

- Status codes are a feature of HTTP and provide a simple and quick-to-check way of communicating basics about the "status" of a request/response cycle.

  - 100s -- "Informational Responses"

  - 200s -- "Successful Responses"

  - 300s -- "Redirects" (send you to a new page instead of the one you asked for)

  - 400s -- "Client errors" (the sender of the request did something wrong)

  - 500s -- "Server errors" (the server ran into a problem when trying to create and send a response)

--

- There are many complete lists of all standard codes, see [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for one from Mozilla.

---

# Status Codes

- If you've ever gone to a URL and gotten a 404, what your browser received was a response with the code for "Not Found" (404).

- Or you may also have had your "Access Denied" somewhere by way of a 403.

- You can always check the code of a response in Python using its `status_code` attribute.

--

<br>

```python
response = requests.get('https://wikipedia.org/wiki/abcdefghijkl')
response
```
```
<Response [404]>
```

---

# Status Codes

- Status codes are handy for us to know about because we can use them as a clue about whether a page exists and we can access it...

<br>

```python
# Start with a list of URLs to check
urls = [...]

for url in urls:
  response = requests.get(url)
  # Only try to scrape the page if we were able to fetch it:
  if 200 <= response.status_code < 300:
    html = response.content
    bs = BeautifulSoup(html, 'html.parser')
    ... # Do your scraping
```

--

<br>

- You can even extend this approach and take specific actions based on certain codes, for example if you were rejected because of invalid credentials (401), you might pass some kind of login details.

---

# Status Codes

- We'll talk a bit more about status codes during our section on Rest APIs

- For now, just make sure you're getting 200s!

  - Sometimes a 304 is okay too -- this means that you've sent the same request before and nothing has changed since the last time, so if you "cached" the original response it's safe to use that one. Tools usually handle this for you automatically so you don't need to think about it.
