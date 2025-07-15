# Builds relevant formats of the Bureaucracy Poker documentation.
#

DOC=poker
MAIN=$(DOC).sgml
DSSSL=$(DOC).dsl
HALF=$(DOC).halfpage
TOP_SECTS=bpoker.sgml fpoker.sgml details.sgml colophon.sgml
B_SECTS=preface.sgml b_chap1.sgml b_chap2.sgml b_chap3.sgml b_chap4.sgml \
	b_glossary.sgml
F_SECTS=f_chap1.sgml f_chap2.sgml
RM=rm
SECTS=$(TOP_SECTS) $(B_SECTS) $(F_SECTS)
SRC=$(MAIN) $(SECTS) $(DSSSL)
# Note that the stylesheet here is super Debian-specific.
STYLESHEET_TARGET="/usr/share/xml/docbook/stylesheet/docbook-xsl/fo/docbook.xsl"

all: $(DOC).fo $(DOC).pdf $(HALF).fo $(HALF).pdf

$(DOC).fo: $(SRC)
	xsltproc -o $(DOC).fo $(STYLESHEET_TARGET) $(MAIN)

$(HALF).fo: $(SRC)
	xsltproc -o $(HALF).fo --stringparam page.height 8.5in --stringparam page.width 5.5in --stringparam page.margin.inner 0.5in --stringparam page.margin.outer 0.5in $(STYLESHEET_TARGET) $(MAIN)

$(DOC).pdf: $(SRC)
	fop -fo $(DOC).fo -pdf $(DOC).pdf
$(HALF).pdf: $(SRC)
	fop -fo $(HALF).fo -pdf $(HALF).pdf

#$(DOC): $(SRC)
#	docbook2html -d "$$(pwd)/$(DSSSL)#html" -o $(DOC) $(MAIN)

clean:
	-$(RM) -f *.log *.dvi *.aux *.tex *.out
	-$(RM) -rf $(DOC) $(DOC).ps $(DOC).pdf $(DOC).fo
