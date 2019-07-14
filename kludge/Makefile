LUALATEX := lualatex
PDF2SVG := pdf2svg

%.pdf: %.tex
	$(LUALATEX) $<

%.svg: %.pdf
	$(PDF2SVG) $< $@
