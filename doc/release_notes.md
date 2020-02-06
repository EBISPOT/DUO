
# DUO - Release notes

## v2020-02-03

This release addresses several outstanding tickets:

- A flat file (CSV) version of DUO is now being created at release time. This file is available from http://purl.obolibrary.org/obo/duo/duo.csv Despite being versioned this file does not include the version explicitely: a ticket has been created to do this in the next release, https://github.com/EBISPOT/DUO/issues/40
- HMB has been moved to be a child of GRU and sibling of GRU-CC : HMB definition doesn't include clinical care and the hierarchy was therefore updated to reflect this.
- The term 'consent code' has been relabeled as 'data use limitation'. To optimise search the term 'consent code' has been retained as an alternative term.
- The term 'consent code primary category' and 'secondary category' have been deprecated: they were not used to tag datasets but instead as patterns for DUO codes capture. Those patterns are institue specific and would be better reflected by Schemablocks constraints specific to a repository.


Minnor fixes
- Addition of xsd:datatype to text field, as per https://github.com/EBISPOT/DUO/issues/33. Reported and fixed by @haoyuanli
- Consistency of ID annotation properties, as per https://github.com/EBISPOT/DUO/issues/32. Reported by @haoyuanli
- typo has been ported back to IAO, https://github.com/EBISPOT/DUO/issues/24

## no release notes for older versions
