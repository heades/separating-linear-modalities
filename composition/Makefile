PDFLATEX = pdflatex
BIBTEX = bibtex
OTT = ott
OTT_FLAGS := -tex_wrap false -tex_show_meta true -picky_multiple_parses false
SKIM = skim_revert.sh

all: pdf
  # This is for my private machine.  It forces my PDF reader to reload.
  # It should not run unless "skim_revert.sh" is in your PATH.
  ifeq ($(SKIM), skim_revert.sh)
	$(SKIM) $(CURDIR)/main.pdf
	$(SKIM) $(CURDIR)/main.pdf
	$(SKIM) $(CURDIR)/main.pdf
  endif

pdf : main.pdf

quick : main.tex ref.bib Makefile
	$(PDFLATEX) -jobname=main main.tex
        # This is for my private machine.  It forces my PDF reader to reload.
        # It should not run unless "skim_revert.sh" is in your PATH.
ifeq ($(SKIM), skim_revert.sh)
	$(SKIM) $(CURDIR)/main.pdf
	$(SKIM) $(CURDIR)/main.pdf
	$(SKIM) $(CURDIR)/main.pdf
endif

# Now this takes the full LaTex translation and compiles it using
# pdflatex.
main.pdf : main.tex ref.bib Makefile appendix.tex
	$(PDFLATEX) -jobname=main main.tex
	$(BIBTEX) main
	$(PDFLATEX) -jobname=main main.tex
	$(PDFLATEX) -jobname=main main.tex

clean :
	rm -f *.aux *.dvi *.ps *.log *-ott.tex *-output.tex *.bbl *.blg *.rel *.pdf *~ *.vtc *.out *.spl *-inc.tex
