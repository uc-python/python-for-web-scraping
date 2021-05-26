class: center, middle
## #4
# HTTP Headers

---

# Headers

Remember headers? From our overview of an HTTP request:

<br>

  - The **headers**, a dictionary of metadata about our request.
  
      - Includes things like: what software made the request (Firefox, or Python Requests library), what type of data is expected in response (HTML, or JSON), and much more

---

# Headers

- Headers can make a big difference in the response you get to your request

  - So far we've been assuming that for any URL, a GET request always returns the same thing. But not so!

- From our perspective, servers do this for some helpful and some unhelpful reasons

--

  - Helpful: Sometimes we can request the response be in a specific format -- HTML or JSON. Getting the best format to parse can make our job easier

--

  - Unhelpful: Some websites don't want you accessing them programmatically, and won't return content to you unless your headers look like those that a browser would send

---

# Custom Headers

- We can pass a set of headers as a dictionary in our call to `requests.get`

```python
# Tell the server explicitly that we expect HTML content and that this request is coming
# from Python's requests library.
my_headers = {
  'Accept': 'text/html',
  'User-Agent': 'python-requests/2.25.1',
}
url = 'http://wikipedia.org/wiki/Sherlock_Holmes'
response = requests.get(url, headers=my_headers)
```

--

- But why would we want to pass custom headers?

---

# Custom Headers

- While custom headers can be useful for a few reasons, the most common purpose is pretending to be a browser

  - This is typically done by setting the `'User-Agent'` field of the headers, although it depends on the site -- some are more rigorous than others and you need to pass a set of believable headers to get content back

- We'll briefly discuss the ethics and legality of web scraping, but for now keep in mind that you should always investigate the specifics of your situation before trying to "fool" a site into giving you data it might not want to

  - Disclaimer: *I am not a lawyer and this is not legal advice, etc.*

  - That said, most of the time, if the information is publicly available via a browser, this should be safe. But do your homework case-by-case!

      - Big companies that really really want you not to scrape data have lots of avenues to make life difficult

---

# Custom Headers

- Should the need arise (and you have made sure you're legally allowed to and comfortable with doing so), a good way to pretend to be a browser is to *just send the same headers your browser is sending*

  - If your browser can get the data with those headers, you can probably do the same with Python

- It's surprisingly easy to do that from Developer Tools:

  1. Inspect an element, as we've done before

  2. Change to the *Network* tab in the developer panel

  3. Click on the very first item in the "Name" list -- it will probably look like the part of the page URL after the first slash

  4. Click on the *Headers* tab within this panel and scroll down to Request headers

--

- Googling "How to find request headers in Safari/Chrome/Firefox" should also get you some good, more customized directions

---

# Custom Headers

- Copying headers from your browser repeatedly can be a pain though, and once you find a set of believable headers, sometimes it's nice to just stick with those

- For example, here is one header dictionary that I use:
```python
HEADERS = {
    "accept": "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8",
    "accept-encoding": "gzip, deflate, br",
    "accept-language": "en-US,en;q=0.8",
    "upgrade-insecure-requests": "1",
    "user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36",
}
```

---

# Custom Headers

- As a last note on headers...

- **Don't worry about them unless you have to**

  - That's going to be a recurring theme for more advanced parts of web scraping
