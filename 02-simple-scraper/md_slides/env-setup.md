class: center, middle

## #1
# Environment Setup

---

# Python Packages and Environments

- Part of Python's appeal is its huge ecosystem of add-ons, or "packages"

- We're going to use several Python packages to help us in our scraping

  - Like *Pandas*, which we've seen already

  - Also quite a few new ones, such as *requests*, *beautifulsoup*, and *scrapy*

---

# Python Packages and Environments

- In order to keep our needs for this class separate from any future (or past) projects you'll work on, we want to use an isolated **environment**.

- Python environments are separate sandboxes that each keep track of their own packages

  - i.e. *pandas* and *requests* might be installed in environment A, but not in environment B -- which might have totally different packages

  - This isolation makes it less likely that upgrades or new installations for one project cause the code of another project to stop working

- We need to create an environment with *pandas*, *requests*, *beutifulsoup*, *scrapy*, etc.
  
  - When it comes time to run code, we'll use the Python and packages from this environment.

---

# Environment Management Tools

- There are several commonly-used environment management tools, but the two most popular are:

  - **Venv** -- No matter how you installed Python, Venv is included. Short for *Virtual Environment*, and people sometimes use that name for it.

  - **Conda** -- Bundled only with the Anaconda distribution of Python, which you may have downloaded (it's the way I recommend installing Python). Slightly less common than Venv overall, but more tailored to the data science ecosystem.

---

# Environment Management Tools

- Which to choose for this class?
  
  - If you have Conda installed (because you downloaded the Anaconda Python distribution), use it. Otherwise use Venv.

  - To check if you have Conda installed, use Spotlight (Mac) or the Start Menu (Windows) to search for "Anaconda". If you get results (likely "Anaconda Navigator" or "Anaconda Prompt"), you almost certainly have Conda installed.

---

# Creating an Environment

- **Heads Up**: Learning how to create environments and run code using them is likely going to be the trickiest bit of this entire course.

  - Since we're working outside of Python (we're actually setting up Python itself), things work very differently depending on your setup and operating system.

  - Don't get discouraged if you run into trouble! Read the linked documentation if you get stuck, and remember you can ask for help during our lab sessions.

---

# Creating an Environment: Conda

---

# Creating an Environment: Venv

---

# Questions
