DIST = trac
HIGHLIGHT = code
TRASHEXT = .pdf .aux .log .nav .out .snm .toc
TRASH = $(addprefix $(DIST), $(TRASHEXT))

all: $(DIST).pdf
$(DIST).pdf: $(DIST).tex 
	#cd code && make
	pdflatex $<
	pdflatex $< # Twice, so TOC is also updated

.PHONY: clean
clean:
	rm -f $(TRASH)
