MAIN = main
PDF = $(MAIN).pdf

.PHONY: all watch clean open publish

all: $(PDF)

$(PDF): $(MAIN).tex references.bib
	pdflatex -interaction=nonstopmode $(MAIN).tex
	bibtex $(MAIN)
	pdflatex -interaction=nonstopmode $(MAIN).tex
	pdflatex -interaction=nonstopmode $(MAIN).tex

watch:
	latexmk -pdf -pvc -interaction=nonstopmode $(MAIN).tex

clean:
	rm -f *.aux *.bbl *.blg *.fdb_latexmk *.fls *.log *.out *.synctex.gz *.toc *.nav *.snm *.vrb *.run.xml *-blx.bib *.bcf

open: $(PDF)
	open $(PDF)

publish: $(PDF)
	cp $(PDF) ../docs/abstract_v3.pdf
	@echo "Published to docs/abstract_v3.pdf"
