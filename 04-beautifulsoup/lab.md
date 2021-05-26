# BeautifulSoup Lab

<br><br>

This lab is fairly long; it's okay if you don't finish the entire thing.
Some of the later questions are meant to challenge you to solve new problems and require tools we haven't explicitly covered in lecture.

## 1. Another Fictional Character Wikipedia Page

The URL of the Wikipedia page for Harry Potter is `https://en.wikipedia.org/wiki/Harry_Potter_(character)`.
Scrape this page for the same details we looked at for Sherlock Holmes, Elizabeth Bennet, and Bilbo Baggins:
- Page title
- URL of the image of the character
- Full text of the page.

Save that result in a file called `harry.txt`. Look over its contents to confirm you fetched the information you expected, and follow the image URL (remember that you may need to add `https` at the beginning).

## 2. Looping Over Multiple Characters

Using Python's `for` loop, we can iterate through a collection of items and take actions on each.
The following code creates a list of dictionaries, where each dictionary represents a certain character and contains their page URL and the name of the file where their scraped data should be saved.
Loop through it, extract the same information from their page as you did from Harry Potter's, and store it in the appropriate filename.

```python
characters = [
    {'url': 'https://en.wikipedia.org/wiki/Prince_Caspian_(character)', 'filename': 'caspian.txt'},
    {'url': 'https://en.wikipedia.org/wiki/Oliver_Twist_(character)', 'filename': 'oliver_twist.txt'},
    {'url': 'https://en.wikipedia.org/wiki/Jay_Gatsby', 'filename': 'gatsby.txt'},
]
```

To get you started, your loop might begin like this:

```python
for character in characters:
    url = character['url']
    filename = character['filename']
    ...
```

In Jupyter, loops must be entirely defined in a single cell -- so you may need to condense your code.

**Bonus Challenge:** If you're familiar with writing functions, try to define a function `scrape_to_file` so that your loop can be simply the following:

```python
for character in characters:
    scrape_to_file(character['url'], character['filename'])
```

## 3. A New Page Format to Scrape
