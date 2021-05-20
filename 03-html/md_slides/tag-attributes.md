
class: center, middle

## #4
# Tag Attributes

---

# Attributes

- In looking at HTML in the browser, we saw lots of tags that were more complicated than the simple ones we learned in Section 2

```html
<div id="toc" class="toc" role="navigation" aria-labelledby="mw-toc-heading">
  ...
</div>
```

<img src="assets/content-div.png" width="15%"/>

---

# Attribute Example

```html
<div id="nav-bar" class="nav">
  ...
</div>
```

- Here, we would say that the div has two **attributes**: `id` and `class`

  - These are two of the most common attributes of HTML tags, though there are many more

--

- Each attribute also has a **value**

  - The value of the id attribute is "nav-bar"

  - The value of the class attribute is "nav"

---

# Attribute Example

- We've already seen a couple of attributes

--

- Images have a `src` attribute to point to the image file

```html
<img src="assets/image.png"/>
```

--

- Links (anchor tags) have an `href` attribute to hold the linked URL

```html
<a href="https://google.com">Go to Google</a>
```

---

# Types of Attributes

- `src` and `href` are examples of attributes that only make sense on certain elements

  - It doesn't make much sense to have a "source" for a paragraph, or a HyperText Reference for a content division

- But certain tags are applicable to pretty much all elements, most prominently:

  - **id**

  - **class**

  - **style**

---

# ID Attribute

- A unique name (within the current page) to identify the element

```html
<img src="/assets/logo.png" id="site-logo"/>
```

- There must only one element on the page with this ID.

---

# Class Attribute

```html
<h2 class="chapter-title">Chapter 7: Salamander</h2>
<p>
  ...
</p>
<h2 class="chapter-title">Chapter 8: Rat</h2>
<p>
  ...
</p>
```

- Both chapter titles are the same type of thing
  
  - Probably are the same font, size, color, etc

  - Marking them as the same class makes it easier to standardize them

---

# Style Attribute

- The style attribute allows styling (think color, size, font type, padding) to be applied to an element

```html
<img src="/assets/logo.png" style="width:100%;padding:3px;"/>
```

- *But* styling of elements is more traditionally done in separate files, so you won't see this too much

---

# HTML Styling & CSS

- We're not going to talk about styling in this class

  - Sorry, we only have so much time and it's (yet another) big topic

- Good to know a few things though:

  - Styles are usually applied through separate files called Cascading Stylesheets (CSS), or sometimes just "stylesheets"

  - Styles are applied to given elements based on type (e.g. `div`), ID, and class

  - That's the point of the ID and class attributes, in case you were wondering -- to mark elements for certain styling

---

# A Quick Peek at CSS

```css
/* Make chapter titles big and red */
h2.chapter-title {
  color: red;
  font-size: 3em;
}

/* Add some padding around our site logo image */
#site-logo {
  padding: 20px;
}
```
