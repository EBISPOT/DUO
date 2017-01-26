OBO=http://purl.obolibrary.org/obo
ONT=duo
BASE=$(OBO)/$(ONT)
SRC=$(ONT)-edit.owl
RELEASEDIR=../..
ROBOT= robot
OWLTOOLS= owltools
USECAT= --use-catalog

all: 
	cp $(SRC) $(ONT).owl


prepare_release: all
	cp $(ONT).owl $(RELEASEDIR) &&\
	git add $(RELEASEDIR)/*.owl 
	echo "Release files are now in $(RELEASEDIR) - now you should commit, push and make a release on github"
	

$(ONT).owl: $(SRC)
	$(ROBOT)  reason -i $< -r ELK relax reduce -r ELK annotate -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT).owl -o $@

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

release: $(ONT).owl #$(ONT).obo
	cp $^ $RELEASEDIR && cp imports/* $RELEASEDIR/imports
