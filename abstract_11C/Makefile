# Abstract Build System
# Usage:
#   make          — build PDF
#   make watch    — continuous rebuild on changes
#   make clean    — remove build artifacts
#   make open     — build and open PDF
#   make publish  — build and copy PDF to docs/ for GitHub Pages

MAIN = main
PDF = $(MAIN).pdf

.PHONY: all watch clean open publish

all: $(PDF)

$(PDF): $(MAIN).tex
	pdflatex -interaction=nonstopmode $(MAIN).tex
	pdflatex -interaction=nonstopmode $(MAIN).tex

watch:
	latexmk -pdf -pvc -interaction=nonstopmode $(MAIN).tex

clean:
	rm -f *.aux *.bbl *.blg *.fdb_latexmk *.fls *.log *.out *.synctex.gz *.toc *.nav *.snm *.vrb *.run.xml *-blx.bib *.bcf

open: $(PDF)
	open $(PDF)

publish: $(PDF)
	cp $(PDF) ../docs/abstract.pdf
	@echo "Published to docs/abstract.pdf"
