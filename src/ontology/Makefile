OBO=http://purl.obolibrary.org/obo
ONT=duo
BASE=$(OBO)/$(ONT)
SRC=$(ONT)-edit.owl
RELEASEDIR=../..
ROBOT= robot
OWLTOOLS= owltools
USECAT= --use-catalog
# language annotations should be included here and also added to merge command below
JA=$(ONT)-japanese.owl
ES=$(ONT)-spanish.owl

# make all
all: $(ONT).owl $(ONT)-lang.owl $(ONT)-basic.owl $(ONT).csv $(ONT)-basic-lang.owl $(ONT)-lang.csv
# make without translations
no_lang: $(ONT).owl $(ONT)-basic.owl $(ONT).csv

test:all

prepare_release:
	$(ROBOT) reason -i $(SRC) -r ELK relax reduce -r ELK annotate -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT).owl -o $(ONT).owl
	cp $(ONT).owl $(ONT)-basic.owl $(ONT).csv $(RELEASEDIR) &&\
	git add $(RELEASEDIR)/*.owl
	echo "Release files are now in $(RELEASEDIR) - now you should commit, push and make a release on github"

# create OWL from edit file -  reason relax reduce
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

# create CSV format output of root terms
$(ONT).csv: $(ONT)-basic.owl make-csv.sparql
	$(ROBOT) query -i $(ONT)-basic.owl --query make-csv.sparql $(ONT).tsv

# create CSV format output of root terms with translations
$(ONT)-lang.csv: $(ONT)-basic-lang.owl make-csv-lang.sparql
	$(ROBOT) query -i $(ONT)-basic-lang.owl --query make-csv-lang.sparql $(ONT)-lang.tsv


mirror/%.owl: $(SRC)
	$(OWLTOOLS) $(OBO)/$*.owl --remove-annotation-assertions -l -s -d --remove-dangling-annotations  -o $@
.PRECIOUS: mirror/%.owl

release: $(ONT).owl $(ONT)-basic.owl $(ONT).csv 
	cp $^ $RELEASEDIR
