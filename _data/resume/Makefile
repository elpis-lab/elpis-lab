.PHONY: main_icra.pdf all clean
all: cv_cchamzas.pdf

cv_cchamzas.pdf: cv_cchamzas.tex Makefile
	latexmk -pdf -f -bibtex -pdflatex="pdflatex -interaction=nonstopmode" -use-make cv_cchamzas.tex
	cp cv_cchamzas.pdf ../../assets/pdf

clean:
	latexmk -CA
	mv cv_cchamzas.*[^tex]
