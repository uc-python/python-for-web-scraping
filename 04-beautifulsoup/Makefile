MD_FILES = $(wildcard md_slides/*)

.PHONY: slides clean

slides: slides.html
	
slides.html: $(MD_FILES) assets/styles.css
	remarker -o slides.html -c assets/styles.css md_slides

clean:
	rm slides.html
