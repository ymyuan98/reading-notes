RMD := $(wildcard *.Rmd)
HTML := $(RMD:.Rmd=.html)
PDF := $(RMD:.Rmd=.pdf)
TEX := $(RMD:.Rmd=.tex)
DOCX := $(RMD:.Rmd=.docx)
BIB := ProbML-rn.bib

ProbML-rn.pdf: ProbML-rn.Rmd 
	Rscript -e "rmarkdown::render('$<', 'pdf_document');"

ProbML-rn.Rmd: header.md $(RMD)
	cat $^ > $@

all:  $(PDF)

reall: $(PDF) $(TEX) $(DOCX) $(HTML)

clean: 
	rm -f $(PDF) $(TEX) $(DOCX) $(HTML)

%.html: %.Rmd $(BIB)
	Rscript -e "rmarkdown::render('$<', rmarkdown::html_document(pandoc_args = '--self-contained'));"

%.pdf: %.Rmd $(BIB)
	Rscript -e "rmarkdown::render('$<', 'pdf_document');"

%.tex: %.Rmd $(BIB)
	Rscript -e "rmarkdown::render('$<', 'latex_document');"

%.docx: %.Rmd $(BIB)
	Rscript -e "rmarkdown::render('$<', 'word_document');"

