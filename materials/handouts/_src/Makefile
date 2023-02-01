all: project

project:
	pdflatex -shell-escape project-overview.tex
	cp project-overview.pdf ../
	pdflatex -shell-escape decaf-spec.tex
	cp decaf-spec.pdf ../

clean:
	rm -f *.aux *.log *.out *.toc *.pdf
