PROG		= talk

DIR		= output

LATEX		= pdflatex
LATEXFLAGS	= -halt-on-error -output-directory=$(DIR)
BIBTEX		= bibtex

RM		= rm -f
ECHO		= echo
MKDIR		= mkdir -p
NIRVANA		= >/dev/null
CAT		= cat
EDITOR		= emacs
PREVIEWER	= evince
VIEWER		= evince
SPELLCHECK	= aspell --lang=en_US --encoding=utf-8 -t -c



GARBAGE		= $(DIR)/*


all : $(PROG)

clean :
	@$(ECHO) "Cleaning up ..."
	@$(RM) $(GARBAGE)

edit :
	@$(ECHO) "Opening "$(PROG)".tex ..."
	@$(EDITOR) $(PROG).tex &

check :
	@$(ECHO) "Spell checking ..."
	@$(SPELLCHECK) $(PROG).tex

texlog :
	@$(ECHO) "Latex log file ..."
	@$(CAT) $(DIR)/$(PROG).log

view :
	@$(ECHO) "Opening "$(PROG)".pdf ..."
	@$(VIEWER) $(DIR)/$(PROG).pdf &

pre :
	@$(ECHO) "Opening "$(PROG)".pdf ..."
	@$(PREVIEWER) $(DIR)/$(PROG).pdf &

bib :
	@$(MKDIR) $(DIR)
	@$(ECHO) "Generating Bibtex ..."
	@$(BIBTEX) $(DIR)/$(PROG) $(NIRVANA)

biblog :
	@$(ECHO) "Bibtex log file ..."
	@$(CAT) $(DIR)/$(PROG).blg

full :
	@$(ECHO) "Cleaning up ..."
	@$(RM) $(GARBAGE)
	@$(MKDIR) $(DIR)
	@$(ECHO) "Compiling "$(PROG)" ..."
	@$(LATEX) $(LATEXFLAGS) $(PROG) $(NIRVANA)
	@$(ECHO) "Generating Bibtex ..."
	@$(BIBTEX) $(DIR)/$(PROG) $(NIRVANA)
	@$(ECHO) "Compiling "$(PROG)" ..."
	@$(LATEX) $(LATEXFLAGS) $(PROG) $(NIRVANA)
	@$(LATEX) $(LATEXFLAGS) $(PROG) $(NIRVANA)
	@$(ECHO) "Done!"

$(PROG) : 
	@$(MKDIR) $(DIR)
	@$(ECHO) "Compiling "$(PROG)" ..."
	@$(LATEX) $(LATEXFLAGS) $(PROG) $(NIRVANA)


