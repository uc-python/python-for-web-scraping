# Simple Scraper Lab

### One note before you begin

I've found that occasionally, the content returned from the Edgar site won't contain any data. You'll get a Pandas message like "Content didn't contain any tables". If you get this, but know that the search phrase you used appeared in a table, try rerunning. In cases where I found this, it went away if I ran my code again once or twice. If you still get that error after a few reruns, it's likely that the phrase you're using truly *doesn't* appear.

<br><br>

## 1. Apple's Balance Sheet

Using the Edgar database, locate Apple Inc.'s most recent 10-K and extract the following metrics (from the most recent year) from its balance sheet:
- Total assets, total current assets, total noncurrent assets
- Total liabilities, total current liabilities, total noncurrent liabilities
- Total equity (listed as "Total shareholders' equity")

Then, using this information, confirm...
- Current + noncurrent assets = total assets
- Current + noncurrent liabilities = total liabilities
- Assets - liabilities = equity

*Note:* The apostrophe in "shareholders'" is actually a special glyph, not the single quote that appears in Python when you type on your keyboard. You may need to manually copy and paste it, if you're searching or filtering on that string. Here is the glyph: `’`

<br><br>

## 2. Looking Deeper at HTML

Go to the balance sheet table you found in #1.
Right-click on some of the text inside (not blank space!) and look for an option like "Inspect Element".
If that option isn't available, google for instructions to enable your browser's Developer Tools (e.g. *how to enable developer tools safari*) and then try again.

Once you've successfully "inspected" the "element", use the developer console to look at the HTML shown there.
Try mousing over it and watching the highlights that happen.
Look at some of the code.
Does any of it look familiar?
Do you see any places where the data within the table is recognizable from the HTML?

<br><br>

## 3. Apple's Cash Flows

Now that you've mined Apple's balance sheet, try it again on their cash flows (the *Consolidated Statement of Cash Flows* is two pages after the balance sheet).
Extract entries in the following categories, for 2020 and 2019.
- Cash generated by operating activities
- Cash generated by or used in investing activities
- Cash used in financing activities

Which of these has had the biggest change from 2019 to 2020? Which had the smallest?