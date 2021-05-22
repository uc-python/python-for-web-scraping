class: center, middle

## #3
# Getting Elements by Hierarchy

---
# The HTML Tree

- Much of BeautifulSoup's power comes from navigating through HTML

- In order to make use of that, we need to think about HTML the way it does -- as a tree

---
# The HTML Tree

```html
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
```

--

<center><img src="assets/html_tree.jpeg" width="30%"></center>

---
name: tree-diagram

# The HTML Tree

<center><img src="assets/html_tree.jpeg" width="30%"></center>

---
template: tree-diagram

- A **child** is an element that lives within another element, and appears below it on the tree, connected by a black line

    - Both divs are children of the `<html>` tag, the leftmost `<a>` tag is a child of the `<p>` tag

---
template: tree-diagram

- A **parent** is an element that contains another element -- the exact inverse of a child
    
    - The HTML element is the parent of both divs, the `<p>` tag is the parent of the leftmost `<a>` tag

---
template: tree-diagram

- A parent can have any number of child elements (sometimes lots!), but every child has exactly one parent element.

    - The only element without a parent is the HTML tag, which we thus call the "root" of the tree

---
template: tree-diagram

- Child elements that share the same parent are called **siblings**
    
    - The two divs are siblings, as are the `<h1>` and `<p>` tags

---
template: tree-diagram

- How would we describe the relationship between the `<h1>` and `<html>` tags? They're not directly connected.

    - We sometimes say "descendents" to mean all children-of-children, and "ancestors" to mean all parents-of-parents

---
name: bs-html

# BS Dot Syntax

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
template: bs-html

<br>

```python
bs.html.div.h1
```
```
<h1>My Blog</h1>
```

---
template: bs-html

<br>

```python
bs.div.h1
```
```
<h1>My Blog</h1>
```

---
template: bs-html

<br>

```python
bs.div.p
```
```
<p>The other day I was eating lunch, which I made from <a href="http://recipes.com/lunch">this recipe</a></p>
```

---
template: bs-html

<br>

```python
bs.div.p.a
```
```
<a href="http://recipes.com/lunch">this recipe</a>
```

---
template: bs-html

<br>

```python
bs.div.p.a.string
```
```
this recipe
```

---
template: bs-html

<br>

```python
bs.a
```
```
<a href="http://recipes.com/lunch">this recipe</a>
```

---

# BS Dot Syntax

- Using dots (`bs.div.p`), you can navigate "down" the tree 

- BeautifulSoup will find the *first element* of that type

    - It will look at both children and further descendents (children of children, ... of children)

---

# BS Dot Syntax

- How can we get the link to "My Twitter"?

```html
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
```

--

<br>
- Sometimes simply finding the first instance of an element isn't enough

---
template: bs-html

```python
bs.div.next_sibling.next_sibling.a
```
```
<a href="https://twitter.com/me">My Twitter</a>
```

--

- We move over by *two* siblings instead of one because the whitespace between the divs is itself a sibling.

---
template: bs-html

<br>

```python
bs.h1.next_sibling
```
```
'\n'
```

---
template: bs-html

<br>

```python
bs.h1.next_sibling.next_sibling
```
```
<p>The other day I was eating lunch, which I made from <a href="http://recipes.com/lunch">this recipe</a></p>
```

---

# BS Dot Syntax

- You can also use `.previous_sibling`, which does exactly what it sounds like

    - I find it less handy though

- Also `.parent` gets you the direct parent of the current element

---

# BS Dot Syntax

- Last, and maybe most importantly, you can get the text inside elements using `.string`

    - **But** this only works on elements that don't contain other things. They need to have only text, or be the parent of an element that contains only text.

---
template: bs-html

<br>

```python
bs.h1.string
```
```
My Blog
```

---
template: bs-html

<br>

```python
bs.div.next_sibling.next_sibling.a.string
```
```
My Twitter
```

---
template: bs-html

<br>

```python
bs.div.p.string
```

(yields `None`)

---

# BS Dot Syntax

- Sometimes you want *all* the text within an element and its children

- You can use `.strings` (note the final `s`) to get a list of all of them.

---
template: bs-html

<br>

```python
list(bs.div.p.strings)
```
```
['The other day I was eating lunch, which I made from ', 'this recipe']
```
---
template: bs-html

<br>

```python
list(bs.div.next_sibling.next_sibling.strings)
```
```
['\n', 'My Twitter', '\n', 'My Facebook', '\n']
```

---
class: center, middle

## Dot Syntax Demo

