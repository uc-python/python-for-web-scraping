class: center, middle

## 2
# Core HTML Elements to Know

---

# `p` Tag

- The **paragraph** tag

- More generally, often used as a container for any text (not just a paragraph)

  - Though it's not *required* -- text can go directly inside many elements

```html
<p>Come and listen to my story about a man named Jed 
A poor mountaineer, barely kept his family fed</p>
```

---

# `span` Tag

- The **span** tag

- Used to some part of a larger body of text, to style in differently

```html
<p>Some text is <span>very special</span> and should be thought of separately from the rest.</p>
```

--

  - e.g. make some words .big-red[big and red]

  - We'll talk more about styling later

---

# Heading Tags

- `h1`, `h2`, `h3`, `h4`, `h5`

- These tags are for headings, and automatically make the text larger

  - They usually add some padding around the edges too, to space it away from other elements

- `h1` is a top-level heading, like a page title. `h2` is a little smaller, like a section heading. `h3` is yet smaller, etc.

--

```html
<h1>Main Title</h1>
<h3>Subtitle</h3>
<h5>Mini-heading</h5>
```
<h1>Main Title</h1>
<h3>Subtitle</h3>
<h5>Mini-heading</h5>

---

# `img` Tag

- The **image** tag

- Represents a picture to be embedded in the page.

  - The image itself is usually stored on the internet somewhere (maybe in another place on the same website)

  - The image tag uses a link to that location as its "source"

--

```html
<img src="/assets/logo_dark_background.jpg"/>
```
<center><img src="assets/logo_dark_background.jpg" width="10%"/></center>

---

# `a` Tag

- The **anchor** tag, although no one really thinks of it as an achor

- It's almost always used for **links** to other pages

  - The tag encloses the text that will become a link

--

```html
<p>Click <a href="https://www.uc.edu">here</a> to see the UC website.</p>
```
<p>Click <a href="https://www.uc.edu">here</a> to see the UC website.</p>

--

- Note that this tag uses an additional *attribute*, href.

  - href means HyperText Reference, and it must be set to the page where the link should lead

---

# `div` Tag

- The **Content Division** element

- Arguably (in my mind) the cornerstone of HTML

- This is, by and large, how other elements are grouped together

```html
<div>
  <h2>Chapter 1</h2>
  <img src="/images/picture_of_emma.png"/>
  <p>Emma Woodhouse, handsome, clever, and rich, with a comfortable home and happy disposition.</p>
</div>
<div>
  <h2>Chapter 2</h2>
  <img src="/images/picture_of_mr_weston.png"/>
  <p>Mr. Weston was a native of Highbury, and born of a respectable family.</p>
</div>
```

--

- Note how we indent HTML code as it becomes nested.

---

# `table` Tag

- The **table** tag

- Maybe not as foundational as the above tags, but important to us for tabular data

- Tables are sometimes used to display data, but also sometimes used to lay out parts of a page

  - e.g. breaking text into columns, sidebars, etc.

- Relatively complicated HTML structure in order to denote rows & columns.

---

# `table` Tag

```html
<table>
  <tr>
    <th>Name</th>
    <th>Pet</th>
  </tr>
  <tr>
    <td>Harry</td>
    <td>Owl</td>
  </tr>
  <tr>
    <td>Ron</td>
    <td>Rat</td>
  </tr>
  <tr>
    <td>Hermione</td>
    <td>Cat</td>
  </tr>
</table>
```

<table>
  <tr>
    <th>Name</th>
    <th>Pet</th>
  </tr>
  <tr>
    <td>Harry</td>
    <td>Owl</td>
  </tr>
  <tr>
    <td>Ron</td>
    <td>Rat</td>
  </tr>
  <tr>
    <td>Hermione</td>
    <td>Cat</td>
  </tr>
</table>

---

# `table` Tag

- Looking for HTML tables is a big part of `pd.read_html`

---

# Meta Elements

- There are some "meta" elements to know as well

  - `title` -- The text enclosed by this tag becomes the title of the page (shows in your browser tab)

  - `meta` -- Contains meta attributes about the page, to be used by things like search engines

  - `script` -- Encloses or links to other code used by the page, often JavaScript

  - `head` -- Most of the meta tags are enclosed within a `head` tag

  - `body` -- The opposite of `head`; the elements that make up the visible part of the page are usually in here

  - `html` The entire content of a page is typically contained within `<html>...</html>` to indicate it's HTML code.

---

# Other Elements

- There are many, many other elements

- But remember, we're here to read HTML, not write it ourselves

  - If you know the general structure of elements, you can figure most of them out if you run across them

