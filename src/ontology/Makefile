OBO=http://purl.obolibrary.org/obo
ONT=duo
BASE=$(OBO)/$(ONT)
SRC=$(ONT)-edit.owl
RELEASEDIR=../..
ROBOT= robot
OWLTOOLS= owltools
USECAT= --use-catalog
# language annotations should be included here and also added to merge and TSV output commands below
JA=$(ONT)-japanese.owl
ES=$(ONT)-spanish.owl

# make all
all: $(ONT).owl $(ONT)-lang.owl $(ONT)-basic.owl $(ONT).tsv $(ONT)-basic-lang.owl $(ONT)-es.tsv $(ONT)-ja.tsv
# make without translations
no_lang: $(ONT).owl $(ONT)-basic.owl $(ONT).tsv

test:all

prepare_release:
	$(ROBOT) reason -i $(SRC) -r ELK relax reduce -r ELK annotate -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT).owl -o $(ONT).owl
	cp $(ONT).owl $(ONT)-basic.owl $(ONT).tsv $(RELEASEDIR) &&\
	git add $(RELEASEDIR)/*.owl
	echo "Release files are now in $(RELEASEDIR) - now you should commit, push and make a release on github"

# create OWL from edit file -  reason relax reduce
# version stamped with date at runtime
$(ONT).owl: $(SRC)
	$(ROBOT)  reason -i $< -r ELK relax reduce -r ELK annotate -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT).owl -o $@

# merge language annotations into separate -lang.owl - the input list needs to be manually updated
$(ONT)-lang.owl: $(ONT).owl
	$(ROBOT) merge -i $(ONT).owl -i $(JA) -i $(ES) -o $(ONT)-lang.owl

# create simplified OWL with only root DUO terms
$(ONT)-basic.owl: $(ONT).owl root-terms.txt
	$(ROBOT) merge -i $(ONT).owl filter --term-file root-terms.txt --select "annotations self descendants ontology" annotate --ontology-iri $(BASE)-basic.owl -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT)-basic.owl -o $@

# create simplified OWL with only root DUO terms with translations
$(ONT)-basic-lang.owl: $(ONT)-lang.owl root-terms.txt
	$(ROBOT) merge -i $(ONT)-lang.owl filter --term-file root-terms.txt --select "annotations self descendants ontology" annotate --ontology-iri $(BASE)-basic-lang.owl -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT)-basic-lang.owl -o $@

# create TSV format output of root terms for each language - sparql query file can be amended to change output format and filtering
$(ONT).tsv: $(ONT)-basic.owl make-tsv.sparql make-tsv-es.sparql make-tsv-ja.sparql
	$(ROBOT) query -i $(ONT)-basic.owl --query make-tsv.sparql $(ONT).tsv

$(ONT)-es.tsv: $(ONT)-basic-lang.owl make-tsv-es.sparql
	$(ROBOT) query -i $(ONT)-basic-lang.owl --query make-tsv-es.sparql $(ONT)-es.tsv

$(ONT)-ja.tsv: $(ONT)-basic-lang.owl make-tsv-ja.sparql
	$(ROBOT) query -i $(ONT)-basic-lang.owl --query make-tsv-ja.sparql $(ONT)-ja.tsv

mirror/%.owl: $(SRC)
	$(OWLTOOLS) $(OBO)/$*.owl --remove-annotation-assertions -l -s -d --remove-dangling-annotations  -o $@
.PRECIOUS: mirror/%.owl

# copy files into root directory for release
release: $(ONT).owl $(ONT)-basic.owl $(ONT).tsv 
	cp $^ $RELEASEDIR

# clean up old files before creating new ones
.PHONY : clean
clean :
	-rm $(ONT).owl $(ONT)-lang.owl $(ONT)-basic.owl $(ONT)*.tsv $(ONT)-basic-lang.owl