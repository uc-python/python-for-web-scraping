class: center, middle

## #3
# Searching

---

# Searching for Elements

- Navigating the tree is powerful but can get cumbersome in large, deeply-nested HTML

- **Searching** allows us to find elements by their type *or attributes*, including ID and class

---
name: simple-search-html

# Searching for Elements

```python
html = '''
<html>
  <div class="content">
    <h1>My Blog</h1>
    <p>The other day I was eating lunch, which I made from <a href="http://recipes.com/lunch">this recipe</a></p>
  </div>
  <div class="footer">
    <a href="https://twitter.com/me">My Twitter</a>
    <a href="https://facebook.com/me">My Facebook</a>
  </div>
</html>
'''
bs = BeautifulSoup(html, 'html.parser')
```

---
template: simple-search-html

Previously, to get the footer div:

```python
bs.div.next_sibling.next_sibling
```
```
<div class="footer">
<a href="https://twitter.com/me">My Twitter</a>
<a href="https://facebook.com/me">My Facebook</a>
</div>
```

---
template: simple-search-html

With searching:

```python
bs.find(name='div', class_='footer')
```
```
<div class="footer">
<a href="https://twitter.com/me">My Twitter</a>
<a href="https://facebook.com/me">My Facebook</a>
</div>
```

---

# Searching for Elements

- The key to searching is the `.find` method of BeautifulSoup elements

    - Accepts arguments including `name` (the type of tag), `id` (the ID of the tag), and `class_` (the class of the tag)

- It returns the **first element that matches** the criteria

    - Even if that element is several layers deep!

---
template: simple-search-html

<br>

```python
bs.find(class_='content')
```
```
<div class="content">
<h1>My Blog</h1>
<p>The other day I was eating lunch, which I made from <a href="http://recipes.com/lunch">this recipe</a></p>
</div>
```

---
template: simple-search-html

<br> 

You can even mix regular dot syntax with searching:

```python
bs.find(class_='footer').a.string
```
```
'My Twitter'
```

---
template: simple-search-html

<br>

And you're allowed to search for pretty much any attribute...

```python
# What's the text of the link to recipes.com/lunch?
bs.find(href='http://recipes.com/lunch').string
```
```
'this recipe'
```

---
template: simple-search-html

<br>

You can even search for bits of text, and then get their parent element using dot syntax:

```python
bs.find(text='this recipe').parent
```
```
<a href="http://recipes.com/lunch">this recipe</a>
```

---

# Searching for Elements

- As you can probably see, the ability to find anything in the HTML based on its name and attributes is incredibly powerful

- You can even find **all matching elements** (instead of just the first one), using `.find_all` instead of `.find`

    - This takes all the same arguments and returns a list of matching elements

---

# Searching for Elements

- We now know how to use attributes and hierarchy to find individual elements, and to use `.string` to get the text inside of them

- But what if we wanted to get the attributes of an element we've found?

---

# Searching for Elements

```python
bs.find(class_='footer').a
```
```
<a href="https://twitter.com/me">My Twitter</a>
```

--

```python
bs.find(class_='footer').a['href']
```
```
'https://twitter.com/me'
```

---
template: simple-search-html

<br>

```python
# What link does the text "this recipe" point to?
bs.find(text='this recipe').parent['href']
```
```
'http://recipes.com/lunch'
```

---
class: center, middle

## Demo
