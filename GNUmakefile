#
## Makefile for TIKZ PDFs
## 
#
#
## Created       August 09th  2019
## Last modified August 09th  2019
#
#
## ----------------------------------------------------


# --------------------------------------------------------------------------------------------------------
# For non recursive make
-include ./rules.mk
# --------------------------------------------------------------------------------------------------------


# --------------------------------------------------------------------------------------------------------
bubbles.source = \
	./src/bubbles.tex ./src/tikz_bubbles.tex ./src/tikzpeople.sty 

options.source = \
	./src/options_forward.tex ./src/tikz_forward.tex

investments.source = \
	./src/investment_portfolio.tex ./src/tikz_portfolio.tex \
	./src/investment_frontier.tex  ./src/tikz_frontier.tex

# --------------------------------------------------------------------------------------------------------


# --------------------------------------------------------------------------------------------------------
## ALL TARGET
all: bubbles options investments
# --------------------------------------------------------------------------------------------------------



## --------------------------------------------------------------------------------------------------------
## 
bubbles: $(bubbles.source)
	$(call colorecho,"Compiling Bubbles Pictures ...")
	pdflatex -interaction=batchmode -output-directory output src/bubbles.tex
	pdflatex -interaction=batchmode -output-directory output src/bubbles.tex
	convert -density 600x600 output/bubbles.pdf -quality 90 -resize 800x600 output/bubbles.png
	rm -f output/*.aux output/*.log output/*.out
	$(TIME-END)
	@echo

options: $(options.source)
	$(call colorecho,"Compiling Options Pictures ...")
	pdflatex -interaction=batchmode -output-directory output src/options_forward.tex
	pdflatex -interaction=batchmode -output-directory output src/options_forward.tex
	rm -f output/*.aux output/*.log output/*.out
	$(TIME-END)
	@echo

investments: $(investments.source)
	$(call colorecho,"Compiling Investments Pictures ...")
	pdflatex -interaction=batchmode -output-directory output src/investment_portfolio.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_portfolio.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_frontier.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_frontier.tex
	rm -f output/*.aux output/*.log output/*.out
	$(TIME-END)
	@echo


# --------------------------------------------------------------------------------------------------------
## Generate graph for this task
graph:
	$(call colorecho,"Building dependency graph...")
	make -Bnd | make2graph | dot -Tpng -o ./log/graph-TikZ-dag.png
	make -Bnd | make2graph | dot -Tsvg -o ./docs/graph/graph-TikZ-dag.svg