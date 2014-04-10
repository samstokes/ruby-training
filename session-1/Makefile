NAME = ruby-training-1
SLIDES_STYLESHEET = $(wildcard slides.css)
IMAGES = $(wildcard *.png)
ASSETS = $(IMAGES) $(SLIDES_STYLESHEET)

all: $(NAME)-slides.html
dist: $(NAME)-slides-standalone.html $(ASSETS)
	mkdir -p dist
	cp $(ASSETS) dist
	cp $< dist

$(NAME)-slides.html: $(NAME).otl
	OTL slidy <$< >$@
	if [ -n "$(SLIDES_STYLESHEET)" ]; then sed -i '' 's|</head>|<link href="$(SLIDES_STYLESHEET)" type="text/css" rel="stylesheet" /></head>|' $@; fi

$(NAME)-slides-standalone.html: $(NAME)-slides.html $(SLIDES_STYLESHEET) splice.sed
	sed -f splice.sed $< >$@

$(NAME).html: $(NAME).otl
	OTL html <$< >$@

clean:
	rm -rf $(NAME)-slides.html $(NAME)-slides-standalone.html
