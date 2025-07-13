# Builds relevant formats of the Bureaucracy Poker documentation.
#

DOC=poker
MAIN=$(DOC).sgml
DSSSL=$(DOC).dsl
TOP_SECTS=bpoker.sgml fpoker.sgml details.sgml colophon.sgml
B_SECTS=preface.sgml b_chap1.sgml b_chap2.sgml b_chap3.sgml b_chap4.sgml \
	b_glossary.sgml
F_SECTS=f_chap1.sgml f_chap2.sgml
SECTS=$(TOP_SECTS) $(B_SECTS) $(F_SECTS)
SRC=$(MAIN) $(SECTS) $(DSSSL)
RM=rm

all: $(DOC) $(DOC).pdf $(DOC).ps

$(DOC).ps: $(SRC)
	docbook2ps -d "$(DSSSL)#print" $(MAIN)

$(DOC).pdf: $(SRC)
	docbook2pdf -d "$(DSSSL)#print" $(MAIN)

$(DOC): $(SRC)
	docbook2html -d "$$(pwd)/$(DSSSL)#html" -o $(DOC) $(MAIN)

clean:
	-$(RM) *.log *.dvi *.aux *.tex *.out
	-$(RM) -r $(DOC) $(DOC).ps $(DOC).pdf
