# Simple Scraper Lab

## 1. Financial Metrics for Apple Inc.

Using the Edgar database, locate Apple's most recent 10-K and extract the following metrics (from the most recent year) from its balance sheet:
- Total assets, total current assets, total noncurrent assets
- Total liabilities, total current liabilities, total noncurrent liabilities
- Total equity (listed as "Total shareholders' equity")

Then, using this information, confirm...
- Current + noncurrent assets = total assets
- Current + noncurrent liabilities = total liabilities
- Assets - liabilities = equity

*Note:* The apostrophe in "shareholders'" is actually a special glyph, not the single quote that appears in Python when you type on your keyboard. You may need to manually copy and paste it, if you're searching or filtering on that string. Here is the glyph: `’`

## 2. Looking Deeper at HTML

Go to the balance sheet table you found in #1.
Right-click on some of the text inside (not blanks space!) and look for an option like "Inspect Element".
If that option isn't available, google for instructions to enable your browser's Developer Tools (e.g. *how to enable developer tools safari*) and then try again.

Once you've successfully "inspected" the "element", through the developer console at the HTML shown there.
Try mousing over it and watching the highlights that happen.
Look at some of the code.
Does any of it look familiar?
Do you see any places where the data within the table is recognizable from the HTML?

## 3. 
