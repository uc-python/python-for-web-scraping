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

- I strongly recommend you create an environment for this class.

- I'll show you how to do that using a tool called **Conda**.

  - To use Conda, you must have downloaded Python via the Anaconda distribution -- see instructions in the course Readme, or simply google "Download Anaconda Python".

<br>
- *If you already know how to install packages and create environments using Conda or a different tool (such as Venv), feel free to skip this bit of the lecture; just install the packages in the [requirements.txt](https://github.com/uc-python/python-for-web-scraping/blob/master/requirements.txt) or [environment.yaml](https://github.com/uc-python/python-for-web-scraping/blob/master/environment.yaml) in the course repo.*

---

# What's Conda?

- Conda is a tool for creating environments and managing packages

- It comes bundled with the Anaconda Python distribution (and is arguably the key feature of that download)

- It's designed with scientific computing in mind, and is thus well-suited to managing data science environments
  
  - Better how? It can handle non-Python dependencies (e.g. C code, LLVM, OS packages) and it has a more advanced dependency solver.

--

- To confirm you have Conda installed, use Spotlight (Mac) or the Start Menu (Windows) to search for "Anaconda".

  - If you get results (likely "Anaconda Navigator" or "Anaconda Prompt"), you installed the Anaconda distribution and almost certainly have Conda installed.

---

# More on Conda

- You can run Conda from the *command line*, or terminal, of your computer.

- But the Anaconda distribution also comes with a graphical interface for using Conda, called **Anaconda Navigator**.
  
  - This is what we'll use in our walkthrough.

- Environments can be specified in files called **environmnent.yaml**.

  - You can find [our environment.yaml](https://github.com/uc-python/python-for-web-scraping/blob/master/environment.yaml) in the course GitHub repository.

---
class: center, middle

## Environment Setup on Mac

---

# Environment Setup on Mac

*These steps may not work exactly as-is on your setup, depending on your operating system, version of Anaconda, and some other factors. If you run into trouble, consult the Anaconda Navigator [Getting Started guide](https://docs.anaconda.com/anaconda/navigator/getting-started/) and [full documentation](https://docs.anaconda.com/anaconda/navigator/).*

1. Download our course materials to your computer, in a location of your choice. Just remember where!

  - You may need to unzip them if you download a zip file. It's important you have access to the files inside.

2. Open Anaconda Navigator (via whatever method you usually use to open apps).

3. In the left sidebar, click on *Environments*.

4. In the new pane that appears, look for an *Import* button in the bottom left. Click it.

5. A dialog box will appear, asking you to choose a name and specification file.

  - For name, enter "uc-python-scraping"

  - For specification file, press the folder button to open a file browser. Find the course materials you downloaded earlier and select the *environment.yaml* file inside.

6. After filling out the dialog box, press the green *Import* button to complete the process.

7. Wait for Anaconda to create the environment. A loading bar should be visible at the bottom of the screen.

  - This can take a while! Be patient.

---
class: center, middle

## Environment Setup on Mac
# Demo

---
class: center, middle

## Environment Setup on Windows

---
# Environment Setup on Windows


*These steps may not work exactly as-is on your setup, depending on your operating system, version of Anaconda, and some other factors. If you run into trouble, consult the Anaconda Navigator [Getting Started guide](https://docs.anaconda.com/anaconda/navigator/getting-started/) and [full documentation](https://docs.anaconda.com/anaconda/navigator/).*

---
class: center, middle

## Environment Setup on Windows
# Demo

---
class: center, middle

# Questions
