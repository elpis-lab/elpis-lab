.PHONY: main_icra.pdf all clean
all: cv_cchamzas.pdf

cv_cchamzas.pdf: cv_cchamzas.tex Makefile
	latexmk -pdf -f -bibtex -pdflatex="pdflatex -interaction=nonstopmode" -use-make cv_cchamzas.tex
	mv cv_cchamzas.pdf ../../assets/pdf

clean:
	latexmk -CA
	rm cv_cchamzas.*[^tex]
