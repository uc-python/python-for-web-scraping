class: center, middle

## #3
# HTTP Methods

---

# HTTP Methods

- We've used `requests.get` several times at this point

- This is called issuing a "GET" request

  - In the sense that you're getting a page and its contents

- *However* there are other types of requests, called **methods**

---

# HTTP Methods

- Methods are all *verbs*

- There are many allowed by the HTTP protocol, but four are most common, and of those we usually only use two in web scraping:

<br>
--

  - **GET** -- We know this one. Fetch something (usually a web page in our case).

--

  - **POST** -- Submit some information. Used for logging into websites that require authentication and submitting web forms.

--

  - **PUT** and **DELETE** -- Update or delete records in a database; rarely used for scraping

    - While all four of these verbs have meanings in the context of a database, but these two don't do much beyond that.

---

# HTTP Methods

- We will only use GET requests in this course, but it's good to be familiar with all of them if you pursue web scraping further

  - In order to access some pages, you may need to first submit a POST request to authenticate

  - You probably won't need run into PUT and DELETE unless you use APIs for something other than extracting information from the web (although again, good to be aware of them!)
