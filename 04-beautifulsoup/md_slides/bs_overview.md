class: center, middle

## #1
# BeautifulSoup Overview

---
name: docs

# What's BeautifulSoup?

- Direct from the [documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/):

> *Beautiful Soup is a Python library for pulling data out of HTML and XML files. It works with your favorite parser to provide idiomatic ways of navigating, searching, and modifying the parse tree. It commonly saves programmers hours or days of work.*

---
template: docs

- **"pulling data out of HTML and XML files"** -- Extracting data that is stored as part of a web page, programmatically

---
template: docs

- **favorite parser** -- BeautifulSoup can use several other packages as its "parser", a tool to break down the HTML code. For simplicity, we'll use a parser that's built into Python: `html.parser`

---
template: docs

- **idiomatic ways of navigating, searching, and modifying the parse tree** -- The best part of BeautifulSoup isn't that it can break down HTML; it's that it provides a very intuitive interface for doing that

---
template: docs

- Ultimately, BeautifulSoup is the standard tool for **Post-processing** raw HTML code

---
# Interface

- Everything starts with a `BeautifulSoup` object, which takes the HTML code as an argument in order to parse it.

    - Also takes the name of the parser we'll be using, which will be `'html.parser'` for the duration of this class

```python
from bs4 import BeautifulSoup

html = '<h1>Welcome</h1><p>This is my website.</p>'
bs = BeautifulSoup(html)
``` 

---
# Interface

- Printing the soup object shows you the HTML that it wraps

```python
print(bs)
```
```
<html><h1>Welcome</h1><p>This is my website.</p></html>
```

- Notice how it added `html` tags

--

- It's much easier to read HTML that's been indented properly, so there is also a `prettify()` method.
```python
print(bs.prettify())
```
```
<html>
    <body>
        <h1>
            Welcome
        </h1>
        <p>
            This is my website.
        </p>
    </body>
</html>
```

---
# Interface

- The really good parts of the interface are for navigating and searching for elements in the HTML "tree", which we'll talk about next.
