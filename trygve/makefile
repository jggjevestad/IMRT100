PAGES=$(subst .md,.html,$(shell find . -name "*.md"))
OPTS=-s -f markdown -t html --template=template.html --mathjax

all: refresh

refresh: $(PAGES)

%.html: %.md
	pandoc $(OPTS) -o $@ $^

clean:
	rm -f $(PAGES)
