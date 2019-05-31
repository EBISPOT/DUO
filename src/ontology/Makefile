OBO=http://purl.obolibrary.org/obo
ONT=duo
BASE=$(OBO)/$(ONT)
SRC=$(ONT)-edit.owl
RELEASEDIR=../..
ROBOT= robot
OWLTOOLS= owltools
USECAT= --use-catalog

all: $(ONT).owl $(ONT)-basic.owl $(ONT).csv
	
test:all

prepare-release: 
	$(ROBOT)  reason -i $(SRC) -r ELK relax reduce -r ELK annotate -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT).owl -o $(ONT).owl
	cp $(ONT).owl  $(ONT)-basic.owl $(ONT).csv $(RELEASEDIR) &&\
	git add $(RELEASEDIR)/*.owl 
	echo "Release files are now in $(RELEASEDIR) - now you should commit, push and make a release on github"
	

$(ONT).owl: $(SRC)
	$(ROBOT)  reason -i $< -r ELK relax reduce -r ELK annotate -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT).owl -o $@

$(ONT)-basic.owl: $(ONT).owl root-terms.txt
	$(ROBOT) merge -i $(ONT).owl filter --term-file root-terms.txt --select "annotations self descendants ontology" annotate --ontology-iri $(BASE)-basic.owl -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT)-basic.owl -o $@

$(ONT).csv: $(ONT)-basic.owl make-csv.sparql
	$(ROBOT) query -i $(ONT)-basic.owl --query make-csv.sparql $(ONT).csv

# remove OBO which doesn't work with IAO and is not needed
#$(ONT).obo: $(ONT).owl
#	$(ROBOT) convert -i $< -f obo -o $(ONT).obo.tmp && mv $(ONT).obo.tmp $@


# IMPORTS = iao bfo
# IMPORTS_OWL = $(patsubst %, imports/%_import.owl,$(IMPORTS))

# # Make this target to regenerate ALL
# all_imports: $(IMPORTS_OWL)

# # Use ROBOT, driven entirely by terms lists NOT from source ontology
# imports/%_import.owl: mirror/%.owl imports/%_terms.txt
# 	$(ROBOT) extract -i $< -T imports/$*_terms.txt --method BOT -O $(BASE)/$@ -o $@
# .PRECIOUS: imports/%_import.owl

# remove OBO which doesn't work with IAO and is not needed
# imports/%_import.obo: imports/%_import.owl
#	$(OWLTOOLS) $(USECAT) $< -o -f obo $@

# clone remote ontology locally, performing some excision of relations and annotations
mirror/%.owl: $(SRC)
	$(OWLTOOLS) $(OBO)/$*.owl --remove-annotation-assertions -l -s -d --remove-dangling-annotations  -o $@
.PRECIOUS: mirror/%.owl

release: $(ONT).owl $(ONT)-basic.owl $(ONT).csv 
	cp $^ $(RELEASEDIR)
