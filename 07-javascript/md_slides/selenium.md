class: center, middle

## #2
# Selenium

---

# Selenium

- Selenium is a way to execute JavaScript without a browser

- That means, even for entirely JavaScript-driven pages, you can fetch the same HTML that eventually renders in the browser

---

# Selenium

- Selenium is a highly complex tool, allowing you to interact with web pages in the same ways a human might in a browser

  - You can "click", enter text, submit forms

- It's also not trivial to set up

- That all said, it does have good documentation: [https://selenium-python.readthedocs.io](https://selenium-python.readthedocs.io)

---

# Selenium

- *Hopefully* you don't encounter a highly dynamic site, but it's good to know a tool exists if/when you need it

- We're not going to cover Selenium in great detail, but we will discuss what it can do and how to identify when you should look to it

---

# Selenium

```python
from selenium import WebDriver
from bs4 import BeautifulSoup

# You must download the "driver" for the browser you want to emulate and provide its path.
driver = webdriver.Chrome('/Users/eswan18/Downloads/chromedriver')
# Navigate to a website
driver.get('https://maps.google.com')

# You can fetch the HTML of the current page with .page_source
html = driver.page_source

# And since it's just HTML, we can parse it with BeautifulSoup
bs = BeautifulSoup(html, 'html.parser')
```

---

# Selenium

- I dug in a little to find the HTML...

```python
print(list(bs.html.body.children)[10].prettify())
```
```html
<jsl jstcache="89">
 <div class="print-only id-print" id="print">
 </div>
 <div class="noprint id-consent-bump" id="consent-bump">
 </div>
 <div aria-label="Google Maps" class="vasquette id-app-container pane-empty-mode" id="app-container" jstrack="1" tabindex="-1">
  <div class="noprint id-pushdown" id="pushdown" jstcache="2" style="display:none">
  </div>
  <div class="noprint" id="modal-dialog">
  </div>
  <div class="noprint" id="streetviewcard">
   <div jsl="$u t-7qjTvvaj20o;">
   </div>
  </div>
  <div class="noprint" id="hovercard">
   <div jsl="$u t-l5Kt9oHY0hs;">
   </div>
  ...
```
It goes on and on and on.

---

# Selenium

- Admittedly, Google Maps probably isn't a site you're going to scrape

- But this same pattern is pretty robust for most pages that dynamically load their HTML via JavaScript

---

# When to Use Selenium

- If the HTML you get back in `response.content` doesn't include things you'd expect, or seems must smaller than it should be, you might be looking at a dynamic page

- A good test -- find a short phrase on the page (in your browser) and search for it in `response.content`. If it's not there, it's probably being loaded dynamically via JavaScript

- Once you're *very sure* you need to execute JavaScript, turn to Selenium

--

<br>

- Here's how you might check for the presence of a phrase:

```python
# You'll need to make your string a "byte string" -- just add a `b` in front
b'Sherlock Holmes' in response.content
```
```
False
```

---

# When to Use Selenium

- Also remember: Selenium can do more than just render JavaScript and HTML on page-load

- If you ever need to interact with a website through clicks, text, etc., Selenium could be a valuable option for you.
