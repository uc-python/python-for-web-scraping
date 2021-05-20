class: center, middle

## #1
# Overview of HTML

---
# HyperText Markup Language

- HTML is a way of *encoding information* that describes what to display in a web browser

- Every page you see while surfing the web is just a huge document of HTML code and not much else

  - Some of the HTML points to image files, which is how pictures get displayed

- HTML has been around as long as browsers have been -- there are new features, but hasn't fundamentally changed much.

---
# HyperText Markup Language

- Why do we need to know it?

  - Scraping sites really boils down to fetching the right HTML and extracting information from it

  - To do that, you need to be able to understand HTML at a basic level

  - A good web scraper should be able to *read* HTML, but not necessarily *write* it

---
# HyperText Markup Language

- HTML uses **text-based "tags"** to denote elements in a page

  - e.g. The `<p>` tag represents a paragraph of text, the `<img>` tag represents an embedded image

- Tags are surrounded by chevrons to set them apart from regular text on the page

- `<h1>`, `<p>`, `<br>`, `<div>`

---
# HTML Enclosing Tags

- Some tags **enclose**, or contain, other content. That content can be simple text or more HTML code.
  
  - Paragraph tags enclose the text of the paragraph

  - Heading tags enclose the text of the heading

  - Divider tags contain other HMTL that lives within that division of the page

--

- Enclosing tags have two parts: an **opening tag** (which comes before the enclosed content) and a **closing tag** (which comes after)

```html
<h1>My Heading</h1>
<p>And some more text I wrote</p>
```

- Note that the closing tag has a forward slash (`/`) before the tag name to distinguish it from an opening tag.
---
# HTML Empty Tags

- The opposite of an enclosing tag is an **empty tag**, which doesn't contain anything else inside it.

  - Image tags, line break tags

--

These tags have only one part, no opening or closing.

```html
Some text before a line break...
<br>
...and some more after.
```
```html
<img src="assets/my_photo.png">
```

- You will sometimes see empty tags represented with a foward slash before the second chevron (`<br/>`) but generally this isn't necessary.

---
# HTML Examples

```html
<h1>Welcome</h1>

<p>This is some really interesting paragraph text. <br> So interesting that you should keep reading.</p>
```

--
<h1>Welcome</h1>

<p>This is some really interesting paragraph text. <br> So interesting that you should keep reading.</p>

---
# HTML Examples

```
<h1>My Blog Post</h1>
<h2>The First Thing I Want to Say</h2>
<p>The hottest take you've ever heard</p>
<h2>The Other Thing I've Been Thinking</h2>
<p>It's less bombastic but still entertaining.</p>
```
--
<h1>My Blog Post</h1>

<h2>The First Thing I Want to Say</h2>
<p>The hottest take you've ever heard</p>

<h2>The Other Thing I've Been Thinking</h2>
<p>It's less bombastic but still entertaining.</p>

---
# HTML Examples

```html
<p>Click <a href="https://google.com">here</a> to go to google.com</p>
```
--
<p>Click <a href="https://google.com">here</a> to go to google.com</p>

---
# HTML Examples

```
<h3>The UC Website Background</h3>
<img src="https://www.uc.edu/about/jcr:content/image.img.cq5dam.thumbnail.500.500.jpg/1610547137667" width="500px;">
```
--
<h3>The UC Website Background</h3>
<img src="https://www.uc.edu/about/jcr:content/image.img.cq5dam.thumbnail.500.500.jpg/1610547137667" width="500px;">
