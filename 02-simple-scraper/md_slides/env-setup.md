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

# Setting up Our Own Environment

- I strongly recommend you create an environment for this class

- I'll show you how to do that using a tool called **Conda**.

  - Using Conda requires that you've downloaded Python via the Anaconda distribution -- see instructions in the course Readme, or simply google "Download Anaconda Python".

- If you already know how to install packages and create environments using Conda or a different tool (such as Venv), feel free to skip this bit of the lecture; just install the packages in the [requirements.txt](https://github.com/uc-python/python-for-web-scraping/blob/master/requirements.txt) or [environment.yaml](https://github.com/uc-python/python-for-web-scraping/blob/master/environment.yaml) in the course repo.

---

# What's Conda?

- Conda is a tool for creating environments and managing packages

- It comes bundled with the Anaconda Python distribution (and is arguably the key feature of that download)

- It is designed with scientific computing in mind, and is thus well-suited to managing data science environments
  
  - How is it better? It can handle non-Python dependencies (e.g. C code, LLVM, OS packages) and it has a more advanced dependency solver.

--

- To confirm you have Conda installed, use Spotlight (Mac) or the Start Menu (Windows) to search for "Anaconda". If you get results (likely "Anaconda Navigator" or "Anaconda Prompt"), you installed the Anaconda distribution and lmost certainly have Conda installed.

---

# Conda: Creating an Environment

- **Heads Up**: Learning how to create environments and run code using them is likely going to be the bumpiest part of this entire course for some of you.

  - Since we're working outside of Python (we're actually setting up Python itself), things work very differently depending on your setup and operating system.

  - Don't get discouraged if you run into trouble! Read the linked documentation if you get stuck, and remember you can ask for help during our lab sessions.

---

# Questions
