MAIN=main
ENGINE ?= pdflatex

.PHONY: $(MAIN).pdf clean

all: $(MAIN).pdf

OCANREN_TEX=$(shell ls *.tex)
$(info $(OCANREN_TEX))

ifeq ("$$(ENGINE)","xelatex")

else
$(MAIN).fmt: $(OCANREN_TEX)
	$(ENGINE) -synctex=1 -ini -jobname="$(@:.fmt=)" "&$(ENGINE)" mylatexformat.ltx $(MAIN).tex
$(MAIN).pdf: $(MAIN).fmt $(OCANREN_TEX)
	/usr/bin/time -f "%U" $(ENGINE) -synctex=1 -fmt=$(<:.tex=.fmt) $(MAIN).tex
	#pdflatex $<
	#bibtex $(MAIN).aux
	#pdflatex $<
	#pdflatex $<
endif

clean:
	$(RM) *.aux *.bak *.bbl *.blg *.log *.out *.pag *.synctex.gz

