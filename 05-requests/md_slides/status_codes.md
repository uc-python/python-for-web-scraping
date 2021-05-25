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

  - That's literally its meaning if you look it up. Basically means: everything worked as expected.

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
