LUALATEX := lualatex
PDF2SVG := pdf2svg
PDFCROP := pdfcrop
PDFFLIP := pdfflip
PDF180 := pdf180
FONTFORGE := fontforge

.PHONY: all
all: kludge.otf

%.pdf: %.tex
	$(LUALATEX) $<

%-crop.pdf: %.pdf
	$(PDFCROP) $<

%-flipped.pdf: %.pdf
	$(PDFFLIP) $<

%-rotated180.pdf: %.pdf
	$(PDF180) $<

%-baseline.pdf: %.pdf
	H=$$(identify -format "%H" $<); \
	T=$$(expr \( 116 - $$H \) / 2); \
	B=$$(expr 115 - $$H - $$T); \
	$(PDFCROP) --margins "6 $$B 0 $$T" $< $@; \

%.svg: %-crop-flipped-rotated180-baseline.pdf
	$(PDF2SVG) $< $@

kludge.svg: kludge.svg.erb \
	capital-a.svg \
	capital-b.svg \
	capital-c.svg \
	capital-d.svg \
	capital-e.svg \
	capital-f.svg \
	capital-g.svg \
	capital-h.svg \
	capital-i.svg \
	capital-j.svg \
	capital-k.svg \
	capital-l.svg \
	capital-m.svg \
	capital-n.svg \
	capital-o.svg \
	capital-p.svg \
	capital-q.svg \
	capital-r.svg \
	capital-s.svg \
	capital-t.svg \
	capital-u.svg \
	capital-v.svg \
	capital-w.svg \
	capital-x.svg \
	capital-y.svg \
	capital-z.svg
	erb $< > $@

kludge.otf: kludge.svg
	$(FONTFORGE) -lang=ff -c 'Open($$1); Generate($$2);' $< $@
