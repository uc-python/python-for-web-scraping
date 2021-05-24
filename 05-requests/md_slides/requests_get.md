class: center, middle

## #1
# `requests.get`

---
# `requests.get`

- Whenever we've needed to pull HTML code from the internet, we've used `requests.get`

  - Both with `pd.read_html` and BeautifulSoup

- Sure, we're "get"ting the page. But why is it called requests? And can it do anything else?

---
# Request-response Cycle: Request

<center><img src="assets/rr_cycle_request.jpeg" width="80%"></center>

---
# Request-response Cycle: Response

<center><img src="assets/rr_cycle_response.jpeg" width="80%"></center>

---
name: request-content

# Contents of a Request

When we send a request, it holds two kinds of information...

*Note that this is a very simplified version of requests; there is more info than just the below.*

---
template: request-content

<br>

- Details needed to transmit the data:

  - The URL or IP address of the server we want to send the request to (`wikipedia.org`)

  - Our own IP address, where the response should be sent back

---
template: request-content

<br>

- Details about who we are and what data we want (they're hard to separate)

  - The address of the page *within* the website (`/wiki/Sherlock_Holmes`), sometimes called the **target**

  - The **method** -- usually one of get, post, put, or delete

      - Right now we've only used GET, but we'll come back to this.

  - The **headers**, a dictionary of metadata about our request.
  
      - Includes things like: what software made the request (Firefox, or Python Requests library), what type of data is expected in response (HTML, or JSON), and much more

  - Optionally a request **body** that can be used to send additional data
