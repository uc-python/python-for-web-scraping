class: center, middle

## #1
# Rest API Basics

---

# Rest APIs

- API stands for **Application Programming Interface**

- In this module, we'll use the term API interchangeably with **Rest API**, which is actually a specific kind of API that you often find on the internet.

---

# Rest APIs

- "**Rest**", properly REST, or sometimes "RESTful", is another abbreviation

  - **Re**presentational **S**tate **T**ransfer, if that means anything to you

- Basically, Rest is a set of requirements that most Web APIs follow -- sort of a protocol

---

# Rest APIs -- Beyond the Semantics

- Rest APIs are a way for us to pull data in a completely different way than a browser would

- We send simpler requests (usually), sometimes with *parameters* to indicate what we want

- The server typically sends back a response with something other than HTML

  - JSON, CSV data, regular text...

--

<br>
- **Most importantly:** Many sites that want to make it easy to get their data will offer an API.

---

# Aside: Other uses of "API"

- In a literal sense, anything that provides an interface that you can access via programming is an API

  - The collection of functions and attributes we used with BeautifulSoup could be considered its API, since they are the *interface* of the package and we use them from Python

- *Sometimes* when people talk about APIs, they are using the word in this sense: any programming interface

---

# Rest APIs

- There are probably millions of APIs on the internet

- Not only are APIs used to let people access data, but they are also the underpinning of how different applications talk to each other

  - e.g. When you add your Google calendar account to your favorite calendar app, that app negotiates with the Google Calendar API to get your data -- and can even make updates to the calendar by sending data back to the API!

--

- The four key HTTP verbs make more sense in the context of APIs, especially those that let you edit some data

  - **GET** -- Fetch some existing data
  - **POST** -- Create some new data
  - **PUT** -- Update some existing data
  - **DELETE** -- Delete some existing data

- However, we're only going to use them for pulling data, and that means mostly GET requests.

---

# API Endpoints

- Rest APIs are usually associated with a partiular URL or collection of URLs, which are called *endpoints* in the context of an APIs.

- In today's lecture, we're going to use a very simple API: The *REST Countries* API: [https://restcountries.eu](https://restcountries.eu)

  - Allows us to fetch information about a country
