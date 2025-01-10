MAIN=main
.PHONY: $(MAIN).pdf clean

all: $(MAIN).pdf

OCANREN_TEX=$(shell ls *.tex)
$(info $(OCANREN_TEX))

ocanren.pdf: $(OCANREN_TEX)
	pdflatex $<
	bibtex $(MAIN).aux
	pdflatex $<
	pdflatex $<

clean:
	$(RM) *.aux *.bak *.bbl *.blg *.log *.out *.pag *.synctex.gz

