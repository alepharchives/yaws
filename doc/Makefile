
include ../include.mk
include ../vsn.mk

IMG_EPS = $(wildcard *.eps)
IMG_PDF = $(IMG_EPS:.eps=.pdf)

all debug:	
	echo "To build the docs, please use make docs before doing make install"

docs:	yaws.ps yaws.pdf

yaws.ps:	yaws.dvi
	$(COND_DVILATEX)$(DVIPS) -o yaws.ps yaws.dvi
	$(COND_DVILATEX)cp yaws.ps ../www

yaws.pdf:	yaws.tex $(IMG_PDF)
	$(COND_PDFLATEX)$(PDFLATEX) yaws.tex
	$(COND_PDFLATEX)$(PDFLATEX) yaws.tex
	$(COND_PDFLATEX)cp yaws.pdf ../www

yaws.dvi:	yaws.tex  $(IMG_EPS)
	$(COND_DVILATEX)$(DVILATEX) yaws.tex
	$(COND_DVILATEX)$(DVILATEX) yaws.tex

%.pdf:	%.eps
	$(COND_PDFLATEX)$(EPSTOPDF) $<

clean:
	rm  -f *.ps *.dvi *.log *.aux *.pdf *.toc *.beam 2> /dev/null || true

install:
	-install -d $(DESTDIR)$(PREFIX)/share/doc/yaws-$(YAWS_VSN)
	-cp yaws.pdf $(DESTDIR)$(PREFIX)/share/doc/yaws-$(YAWS_VSN)
 
