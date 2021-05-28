# Module 8: Web Crawlers and Scrapy

After installing [remarker2](https://github.com/eswan18/remarker2/tree/develop), on a Unix-y system, you can build the presentation with:
```bash
make slides
```

Simply open the produced `slides.html` in your browser to see the slides.

## Exporting to PDF

Using Conda and [decktape](https://github.com/astefanutti/decktape), it's not too hard to convert slides to PDF.

First, create a conda environment and install decktape there, using npm.
```bash
# Create the environment
conda create -n decktape nodejs
# Activate it
conda activate decktape
# Install decktape itself
npm install -g decktape
```
Now, as long as this environment is activated (which you can do any time with `conda activate decktape`), the executable `decktape` will be in your path.

To use it for exporting, `cd` into the folder with your slides.
Open the slides in your browser, however you usually do that (probably just opening `slides.html`) and copy the URL.
Then run the following line, but replacing `<url>` with the URL you copied.

```bash
decktape remark "<url>" slides.pdf --chrome-arg=--disable-web-security --size=320x180
```

The `slides.pdf` file will contain your slides.
