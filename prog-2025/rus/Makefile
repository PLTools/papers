.PHONY: 
.SUFFIXES: .fmt .pdf
ENGINE ?= xelatex
MAIN = mainrus


all: $(MAIN).pdf
clean::
	latexmk -C $(MAIN).pdf -f
ifeq ("$(ENGINE)","xelatex")
$(MAIN).pdf: $(MAIN).tex preamble.tex
	/usr/bin/time -f "%U" latexmk -$(ENGINE) -synctex=1 -interaction=nonstopmode -file-line-error -shell-escape $<
	@echo FINISHED $(ENGINE) -fmt=$(<:.tex=.fmt) $<
else
$(MAIN).fmt: $(MAIN).tex preamble.tex
	$(ENGINE) -synctex=1 -ini -jobname="$(@:.fmt=)" "&$(ENGINE)" mylatexformat.ltx $<
$(MAIN).pdf: $(MAIN).tex  $(MAIN).fmt
	/usr/bin/time -f "%U" $(ENGINE) -synctex=1 -fmt=$(<:.tex=.fmt) $<
endif

clean::
	@$(RM) -r _minted*
	@$(RM) *.aux *.bbl *.blg *.dvi *.log *.nav *.out *.snm *.toc *.vrb *.synctex.gz
	@$(RM) *.pdf *.fmt

DEBS += texlive-font-utils
DEBS += texlive-plain-generic
DEBS += lmodern # nicer fonts
DEBS += fonts-linuxlibertine

debs:
	sudo apt install -y $(DEBS)

