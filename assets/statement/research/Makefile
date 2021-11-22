.PHONY: main_icra.pdf all clean
all: research.pdf

research.pdf: research.tex Makefile
	latexmk -pdf -f -bibtex -pdflatex="pdflatex -interaction=nonstopmode" -use-make research.tex

clean:
	latexmk -CA
	rm research.*[^tex]
