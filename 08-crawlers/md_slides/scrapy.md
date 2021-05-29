class: center, middle

## #2
# Scrapy

---

# Scrapy

- If you have need of a really complex crawler, the Scrapy package is your answer

    - *Scrapy is a fast high-level web crawling and web scraping framework, used to crawl websites and extract structured data from their pages. It can be used for a wide range of purposes, from data mining to monitoring and automated testing.*

    - [scrapy.org](https://scrapy.org)

- Scrapy refers to its web crawler utility as a "spider"

- Features:

    - A whole suite of tweakable settings, for things like the delay between page requests and whether to follow links that lead to different domains

    - A predefined framework for building pipelines from parsing to storing individual records

---

# Scrapy

- Using Scrapy means working outside of Jupyter notebooks

- You build *classes* and *methods* that Scrapy automatically invokes for you, depending on the content of the pages it finds

- You kick of Scrapy from the command line (terminal), not from within Python

- Like selenium, Scrapy has its own tools for parsing through the HTML of a page ... but as with Selenium, you can just use BeautifulSoup instead if you prefer

---

# Scrapy

- All told, I find Scrapy very powerful but a bit of an investment -- if I have a simple task and can write my own page-following logic easily, I usually stay away from it

- *But* you will hear about it in the web scraping space, and if you ever build something to scrape thousands of pages, learning more about Scrapy is a good use of time
