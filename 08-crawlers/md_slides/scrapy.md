class: center, middle

## #1
# Scrapy

---

# Looping Over Pages

- To this point, we have occasionally scraped multiple pages at once

- That usually meant saving several URLs in a list, and looping through them:

<br>

```python
urls = [
    'https://wikipedia.org/wiki/Sherlock_Holmes'
    'https://wikipedia.org/wiki/Elizabeth_Bennet'
    'https://wikipedia.org/wiki/Harry_Potter_(character)'
]

for url in urls:
    response = requests.get(url)
    bs = BeautifulSoup(response.content)
    # Do the parsing for each page
    ...
```

---

# Choosing URLs on the Fly

- Sometimes we don't know all our URLs of interest ahead-of-time

- For example, if we want to scrape details from 
