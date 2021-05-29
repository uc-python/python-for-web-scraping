class: center, middle

## #1
# Web Crawlers

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

- For example, if we want to scrape details from all the Wikipedia pages *linked to* by the Sherlock Holmes page

```python
response = requests.get('https://wikipedia.org/wiki/Sherlock_Holmes')
bs = BeautifulSoup(response.content, 'html.parser')

# Get all links on the page.
next_links = []
for a_tag in bs.find_all('a'):
    # Make sure this <a> has an href attribute
    if 'href' in a_tag.attrs and not a_tag['href'].startswith('#'):
        link = a_tag['href']
        if not link.startswith('https://'):
            link = 'https://wikipedia.org' + link
        next_links.append(link)

# Follow those links and scrape them
for url in next_links:
    response = requests.get(url)
    bs = BeautifulSoup(response.content, 'html.parser')
    # Do your scraping here
    ...
```

---

# Choosing URLs on the Fly

- We might even want to keep doing this, finding new links on each page and following those...

    - Note that the code on the next slide will **run forever**! Don't use it, it's just an example

    - Also it will issue many many requests extremely quickly, which is bad manners in web scraping

---

# Choosing URLs on the Fly

```python

links = ['https://wikipedia.org/wiki/Sherlock_Holmes']
# Loop forever
while True:
    # Set up an empty list to add the next group of links to
    next_links = []

    for url in links:
        # Get the content for each link
        response = requests.get(url)
        bs = BeautifulSoup(response.content, 'html.parser')

        # Collect all the pages *this page links to*
        for a_tag in bs.find_all('a'):
            if 'href' in a_tag.attrs and not a_tag['href'].startswith('#'):
                link = a_tag['href']
                if not link.startswith('https://'):
                    link = 'https://wikipedia.org' + link
                next_links.append(link)

        # Also do some scraping for the current page
        ...

    # Before starting over, move the "next_links" to be the current links
    links = next_links
    next_links = []

```

---

# Choosing URLs on the Fly

- You may also want to place some limits on the links you follow

- Things like:

    - Only links in the main content of the page (to avoid navigation bars)

    - Only links to within the same site (some domain)

--

```python
# The updated version of the link loop from the last slide...

# Note that we select the main content div and only links inside it
for a_tag in bs.find(name='div', class_='main-content').find_all('a'):
    if 'href' in a_tag:
        link = a_tag['href']
        # Only add the link if it's also to a wikipedia page.
        if link.startswith('https://') and 'wikipedia.org' not in link:
            continue # Proceed to the next element in the for loop
        else:
            next_links.append(link)
```

---

# Choosing URLs on the Fly

- Using this basic pattern, you can build arbitrarily complex iterative scrapers

    1. Start with a link or links

    2. Loop over the current link(s)

    3. Collect links from this page that meet your criteria

    4. Update the "current links" based on the new links you found

    5. Repeat from step #2

- Such iterative scrapers that crawl from page to page are called **Web Crawlers**

---

# Web Crawlers

- Crawlers are extremely useful when there is a different page for each "record" of information you want to collect

    - For each page you process, just add a record to some list of records and then save the full list at the end

- All the pages need to be linked together, though -- or all linked to from a common page

- Building simple crawlers isn't too hard

    - We just wrote one in 25 lines above!
