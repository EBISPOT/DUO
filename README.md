[![Build Status](https://travis-ci.org/EBISPOT/DUO.svg?branch=master)](https://travis-ci.org/EBISPOT/DUO)

Table of Contents
=================

   * [DUO - the Data Use Ontology - the essentials](#duo---the-data-use-ontology---the-essentials)
      * [Availability](#availability)
      * [What is DUO?](#what-is-duo)
      * [Versions](#versions)
         * [Stable release versions](#stable-release-versions)
         * [Editors' version](#editors-version)
      * [Contact](#contact)
      * [DUO users](#duo---users)
   * [DUO - Full documentation](#duo---full-documentation)
      * [What is DUO?](#what-is-duo-1)
      * [How did DUO come about?](#how-did-duo-come-about)
      * [Evolution of DUO](#evolution-of-duo)
      * [Examples of use](#examples-of-use)
         * [Tagging with ‘data use restrictions/conditions’](#tagging-with-data-use-restrictionsconditions)
         * [Powering dataset access screening queries](#powering-dataset-access-screening-queries)
         * [DUO Webinar](#duo-webinar)
      * [Automated data access requests](#automated-data-access-requests)
         * [How does querying work when using DUO?](#how-does-querying-work-when-using-duo)
         * [Research Purpose : Data Use Limitation Matching](#research-purpose--data-use-limitation-matching)
         * [Research Purpose to Query](#research-purpose-to-query)
      * [Versions](#versions-1)
      * [Contributions](#contributions)
      * [Data Use Ontology Workstream (in alphabetical order)](#data-use-ontology-workstream-in-alphabetical-order)
      * [Other contributors (in alphabetical order)](#other-contributors-in-alphabetical-order)
      * [Funding](#funding)
      * [DUO logos](#duo-logos)
      * [DUO Pictograms](#duo-pictograms)
      
      
# DUO - the Data Use Ontology - the essentials

## Availability

The latest version of the ontology can always be found at: http://purl.obolibrary.org/obo/duo.owl

DUO can be browsed online via the [Ontology Lookup Service](http://www.ebi.ac.uk/ols/ontologies/duo/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FDUO_0000001) or [Ontobee](http://www.ontobee.org/ontology/DUO). 

It has been registered with the [OBO Foundry](http://obofoundry.org/ontology/duo.html).

DUO is distribtued under the CC-BY 4.0 licence.

## What is DUO?

DUO allows to semantically tag datasets with restriction about their usage, making them discoverable automatically based on the authorization level of users, or intended usage.

This resource is based on the [OBO Foundry principles](http://www.obofoundry.org/principles/fp-000-summary.html), and developed using the [W3C Web Ontology Language](https://www.w3.org/OWL/). It is used in production by the [European Genome-phenome Archive](https://ega-archive.org) (EGA) at EMBL-EBI as well as the Broad Institute for the [Data Use Oversight System](https://duos.broadinstitute.org/#/home) (DUOS).

<!---Here is a hierarchical view of the DUO: -->
<!---![alt tag](https://github.com/EBISPOT/DUO/blob/master/doc/figs/DUO_hierarchy.png "DUO hierarchy") -->

## Versions

### Stable release versions

The latest version of the ontology can always be found at:

http://purl.obolibrary.org/obo/duo.owl


### Editors' version

Editors of this ontology should use the edit version, [src/ontology/duo-edit.owl](src/ontology/duo-edit.owl)

## Contact
Please use this GitHub repository's [Issue tracker](https://github.com/EBISPOT/duo/issues) to request new terms/classes or report errors or specific concerns related to the ontology.

## DUO - users
Several projects have now implemented DUO in production pipelines:
- the Broad Institute’s Data Use Oversight System, [DUOS](https://duos.broadinstitute.org/#/home)
- the European Genome-phenome Archive (EGA). See [here](https://ega-archive.org/datasets/EGAD00001000002) for example.
- the Data Information System, [DAISY](https://github.com/elixir-luxembourg/daisy) 

[Contact](#contact) us to tell us about your implementation!
  
# DUO - Full documentation

## What is DUO?
The (GA4GH) Data Use Ontology (DUO) includes terms describing data use conditions, particularly for research data in the health/clinical/biomedical domain. 

Human subjects datasets often have restrictions such as “only available for cancer use” or “only available for the study of pediatric diseases,” based on the original participant consent, which must be respected when sharing and studying these datasets. 

A current challenge in sharing such datasets for further research is that unique language is used in each informed consent form to describe the secondary use conditions. 
The lack of a standard universal system to categorize these conditions makes it difficult for data access committees (DACs) and researchers to interpret the conditions in a consistent, structured way.

The goal of this resource is to allow large genomics and health data repositories to share the same terminology when describing data use conditions. In addition, we envision a future where web services would submit queries to these repositories such as “return all datasets that can be used to study melanoma by a commercial entity” that will help researchers find relevant data that is compatible with their research purpose. DUO includes ontology terms needed to represent such queries as well as the ontology hierarchy necessary for algorithms to determine whether a research purpose is compatible with the dataset restrictions.  

A further goal is to encourage the authors of new consent forms to align consent language with the terms used by DUO; this would eliminate the need for subsequent review of consent forms to classify data use and speed the availability of data for secondary use.

## How did DUO come about?
Some of the challenges in standardizing and introducing automation to the process of sharing human health and genomics data is that clinical research studies each use unique language in the informed consent form. This means that the written free text is often difficult to translate into a clear data use conditions.  This severely limits the ability to reuse vast stores of data in a timely fashion.

Currently, there is no common ontology to which consent forms can be translated for researchers or DACs to interpret the free text conditions in a structured way. 

The lack of such an ontology is a missed opportunity to guide/inform the writing of consent form language.

DUO represents data use terms from three evolving efforts to standardize data use restrictions in the biomedical and genomics research domain:

**The NIH’s dbGaP data use categories**. The NIH database of Genotype and Phenotype is one of the largest public repositories of genomics data in the world. While ingesting data to the system depositors are asked to use a controlled vocabulary (see [Points to Consider in Drafting Effective Data Use Limitation Statements](https://osp.od.nih.gov/wp-content/uploads/NIH_PTC_in_Drafting_DUL_Statements.pdf))  to represent the conditions for secondary use of the deposited datasets. For example, classify a dataset as General Research Use (GRU), or Health/Medical/Biomedical research only (HMB). This controlled vocabulary was defined in 2011-2012 and has been the foundation for this ontology. There are over 1000 studies labelled with data use conditions using these terms. Some of the challenges with the way the controlled vocabulary is currently being applied: (1) it doesn’t encode the hierarchy between terms; (2) it was often coupled to free text describing disease types.  Both of these aspects make it difficult for algorithms to make logical inference on this information.  

**Consent Codes** A global team effort led by Stephanie OM Dyke (McGill University) and the Regulatory and Ethics Work Stream to define ‘codes’ for specific categories of data use restrictions based on the datasets of the main public genome archives (NCBI dbGaP and EMBL-EBI/CRG European Genome-Phenome Archive (EGA)). The ‘codes’ extend the controlled vocabulary and classification approach of dbGAP and define a hierarchy and approachable classification rules. Read more here: https://doi.org/10.1371/journal.pgen.1005772

**The Automated Data Access Matrix (ADA-M)**. A global team effort led by Anthony Brookes and a GA4GH workstream to define a matrix of data use categories that can be used to define both: (a) the data use restrictions on a dataset, and (b) a research purpose. The ADA-M is a complementary approach for classifying data use conditions and permissions with greater granularity than consent codes and can address an expanded set of use cases. Read more here: [Woolley & Brooks et al. NPJ Genomic Medicine, 2018](https://www.nature.com/articles/s41525-018-0057-4) 

## Evolution of DUO
DUO is an evolving effort to provide digital ontological representation for all the data use categories defined by the efforts mentioned above. Its evolution is driven by driver projects of the Global Alliance for Genomics and Health (GA4GH) such as the EMBL-EBI/CRG EGA, the All Of Us research program and the NIH Data Commons Pilot. 

The first version of DUO described the original terms from the Dyke et al. 2016 publication on [Consent Codes](https://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1005772).  The second version has evolved to include additional terms as described at the  Woolley et al. 2018 publication on [ADA-M](https://www.nature.com/articles/s41525-018-0057-4) as well as updates to definitions based on input from the GA4GH driver projects and the GA4GH Data Access Product line, Data Use Ontology workstream.

We welcome the community’s input and contributions. 

Please contact DURI@ga4gh.org if you are interested in adopting DUO in your organization, would like to suggest changes, or to submit a request under the issue tracker.

## Examples of use
### Tagging with ‘data use restrictions/conditions’
DUO is used by multiple services to tag datasets with data use restriction terms and categories.  For example, the European Genome-phenome Archive (EGA), a service for permanent archiving and sharing of all types of personally identifiable genetic and phenotypic data under controlled access and jointly hosted by European Bioinformatics Institute (EMBL-EBI) and the Centre for Genomic Regulation (CRG), is now supporting the use of DUO to indicate the data use conditions applied to their datasets. The EGA has been working with the Wellcome Trust Sanger Institute to apply DUO to existing datasets, which are now tagged at EGA. To access data at EGA an application is made to the associated Data Access Committee (DAC), which for the Sanger Institute can be accessed via an electronic Data access Mechanism ([eDAM](https://www.sanger.ac.uk/legal/DAA/MasterController)).
  
### Powering dataset access screening queries
DUO is instrumental in supporting services that allow advanced search options by matching a research purpose to datasets tagged with compatible data use restrictions terms.  

For example, the query: find all datasets that can be used to study cancer within a commercial entity. Such queries to discover datasets are enabled by algorithms that reason on the ontology’s hierarchical structure to match the query represented by ontology terms with datasets tagged with terms from the same ontology. 

One such algorithm-based service is the Broad Institute’s Data Use Oversight System ([DUOS](https://duos.broadinstitute.org/#/home)). DUOS is piloting a trial in which a data access committee comprised of experts in data use oversight evaluate data access requests in parallel with the algorithm. This trial leverages the experts’ feedback to improve the algorithm and the ontology and has been contributing to the evolution of DUO.  As an example, here is a description of how the DUOS matching algorithm (and public APIs , see https://api.firecloud.org/#!/Library/duosResearchPurposeQuery) work.

The following figure illustrates how DUO terms can be used to represent data use restrictions on datasets (left) as well as a research purpose query (right) using the DUO ontology terms.  

![alt tag](https://github.com/EBISPOT/DUO/blob/master/doc/figs/DUO_matching.png "DUO matching")

### DUO Webinar
[Watch a webinar here](https://www.youtube.com/watch?v=8ZyU34xpi4M&t=1s) with an explanation of the DUO as well as several global users describing how they integrate it into their systems.

[![](http://img.youtube.com/vi/8ZyU34xpi4M/0.jpg)](http://www.youtube.com/watch?v=8ZyU34xpi4M "")

## Automated data access requests
In the long term, we envision DUO coupled with matching algorithms such as DUOS to empower services that automatically determine if a user’s research purpose is compatible with data use restrictions on datasets and in turn determine whether to give a researcher access to the data. 

### How does querying work when using DUO?

How would an algorithm use DUO ontology to match research purposes and data use restrictions? 
*This is a deep dive into the algorithm’s matching function for those interested, feel free to skip!*
 
The request for a dataset needs to be matched against the existing data use restrictions on stored datasets. These assessments could be run against either 
1. the person making the request (e.g., do they belong to a for-profit/non-profit organization?) or 
2. their specific research purpose itself (e.g. can I use this dataset for cancer research?)

An important aspect of using DUO in automated matching systems is that the query is **ALWAYS** expected to be made at the most specific level. This means that:

- A query for datasets consented for cancer research **WILL NOT** retrieve datasets consented for lung cancer, because lung cancer is a subtype of cancer in a disease hierarchy and the ontology needs to ensure the datasets will only be used to study specifically lung cancer.
- A query for datasets consented for lung cancer research **WILL** retrieve datasets consented for cancer, as lung cancer is a subtype of cancer in a disease hierarchy.

The image below illustrates an example of matching a query and how studies labeled with Data use categories/ Data Use Ontology terms  can be mapped to the data use ontology tree. 

1. A researcher describes he would like to study Melanoma and find all datasets compatible with this research purpose.  
2. A matching algorithm will start by detecting Melanoma research in the ontology hierarchy (dotted circle) and will return every datasets that is labeled with PARENT NODES, going up in the hierarchical ontology tree/ directed acyclic graph. 

![alt tag](https://github.com/EBISPOT/DUO/blob/master/doc/figs/DUO_hierarchy_matching.png "DUO hierarchy matching")

Examples of queries and results as implemented by the DUOS algorithm
Provided by David An, Greg Rushton, Andrea Haessly & Moran Cabili

### Research Purpose : Data Use Limitation Matching
The following table lists the questions presented to a curator when cataloging a dataset in the A repository. For each question, we illustrate how data use ontology codes should be applied to the dataset according to the curator’s choices.

| DUL question in catalog wizard | Answer | DUL |
| --- | --- | --- | 
| Data is available for future general research use [GRU] (required) | Yes | GRU |
||No|||
|Future use is limited for health/medical/biomedical research [HMB] (required)|Yes|HMB|
||No|||
|Future use is limited to research involving the following disease area(s) [DS]|Ontology autocomplete|DS={node}|
|Future commercial use is prohibited [NCU] (required)|Yes|NCU|
||No|||
|Future use by for-profit entities is prohibited [NPU] (required)|Yes|NPU|
||No|||
|Future use for methods research (analytic/software/technology development) outside the bounds of the other specified restrictions is prohibited [NMDS] (required)|Yes|NMDS|
||No|||
|Future use of aggregate-level data for general research purposes is prohibited [NAGR] (required)|Yes|NAGR|
||No|||
||Unspecified|||
|Future use as a control set for diseases other than those specified is prohibited [NCTRL] (required)|Yes|NCTRL|
||No|||
|Future use is limited to research involving a particular gender [RS-G] (required)|Male|RS-M|
||Female|RS-FM||
||N/A|||
|Future use is limited to pediatric research [RS-PD] (required)|Yes|RS-PD|
||No|||
|Future use is limited to research involving a specific population [RS-POP]|Free text input|RS-POP-XX|
|Future use is limited to data generated from samples collected after the following consent form date|Date input||

### Research Purpose to Query
The following describes queries by research purpose and which datasets with DU restrictions would they match when applying the DUOS search using DUO

| If my Research Purpose has... | Related DUL question in catalog wizard | I should see ... |
| --- | --- | --- |
| Disease focused research | Future use is limited to research involving the following disease area(s) [DS] | Any dataset with GRU=true Any dataset with HMB=true. Any dataset tagged to this disease exactly. Any dataset tagged to a DOID ontology Parent of disease X |
| Methods development/Validation study | Future use for methods research (analytic/software/technology development) outside the bounds of the other specified restrictions is prohibited [NMDS] | Any dataset where NMDS is false Any dataset where NMDS is true AND DS-X match |
| Control set | Future use as a control set for diseases other than those specified is prohibited [NCTRL] | Any dataset where NCTRL is false and is (GRU or HMB) Any DS-X match, if user specified a disease in the res purpose search |
| Study population origins or ancestry | Future use is limited to research involving a specific population  [POA] | Any dataset tagged with GRU |
| Commercial purpose/by a commercial entity | Future commercial use is prohibited [NCU]  Future use by for-profit entities is prohibited [NPU] | Any dataset where NPU and NCU are both false |
<!-- |  | |  | -->

## The Data Use Ontology (DUO) & The European General Data Protection Regulation
### Can DUO handle data privacy/data protection law compliance?
- DUO terms describe permitted data use purposes and conditions, mainly focused on research uses of data. These terms are derived from a review of international data sharing practices and ethical principles, and not from a systematic review of applicable legal requirements. 
- DUO is not validated as a compliance tool for any particular legal framework, such as the European General Data Protection Regulation (GDPR). 
- Organizations implementing DUO to inform decisions to release or re-use data remain fully responsible for ensuring those decisions comply with applicable laws and regulations. 
- In the future, DUO might be adapted and validated for a particular legal compliance context, or integrated with a data protection compliance ontology.  
### Is Use of DUO GDPR Compliant?
- DUO terms describe generic conditions for which a dataset (or other scientific resource) may be used. The terms are not intended to contain any personal data about sequenced individuals or data users (e.g. researchers). It is the responsibility of DUO adopters to ensure DUO is implemented in a manner that respects applicable data privacy laws. 
### Does the DUO have any relationship with data privacy/data protection law? 
- DUO terms describe permitted research uses and conditions. DUO terms are similar to the European GDPR concept of “purposes” of processing personal data. For example, data subjects may be permitted to provide their consent for the further processing of their genomic and health-related data for one or more research purposes (e.g., rare disease research). Some DUO terms are also analogous to the GDPR concept of “technical and organizational measures”, such as the condition for research ethics review. However, as mentioned above, DUO terms have not be validated against the GDPR. There are also many other data protection concepts that are not covered by DUO, such as data subjects rights. 


## Versions

The latest version of the ontology is always available at http://purl.obolibrary.org/obo/duo.owl
DUO is versioned by date, e.g., http://purl.obolibrary.org/obo/duo/releases/2017-10-16/duo.owl. Each release is tagged on Github and a corresponding Permanent URL is created. This ensure versions remain accessible and can be uniquely referred to.
A list of all releases is avaialble at https://github.com/EBISPOT/DUO/releases/.

We have a strict deprecation policy compliant with the OBO Foundry principles: once created, IDs are never deleted. If changes altering the meaning of a term are required, the term is deprecated and a new one is created, for which a new ID is minted.

## Contributions
- Consent codes : Dyke et al. Plos Genetics, 2016 , https://doi.org/10.1371/journal.pgen.1005772. 
Stephanie O. M. Dyke ,Anthony A. Philippakis, Jordi Rambla De Argila, Dina N. Paltoo, Erin S. Luetkemeier, Bartha M. Knoppers, Anthony J. Brookes, J. Dylan Spalding,Mark Thompson, Marco Roos,Kym M. Boycott, Michael Brudno, Matthew Hurles, Heidi L. Rehm, Andreas Matern, Marc Fiume,Stephen T. Sherry

- Automated Discovery and Access Materics (ADA-M): Woolley et al. NPJ Genomic Medicine, 2018 , https://www.nature.com/articles/s41525-018-0057-4   
J. Patrick Woolley, Emily Kirby, Josh Leslie, Francis Jeanson, Moran N. Cabili, Gregory Rushton, James G. Hazard, Vagelis Ladas, Colin D. Veal, Spencer J. Gibson, Anne-Marie Tassé, Stephanie O. M. Dyke, Clara Gaff, Adrian Thorogood, Bartha Maria Knoppers, John Wilbanks , Anthony J. Brookes

## Data Use Ontology Workstream (in alphabetical order)
- Ayad Aliomer (Optum)
- Pinar Alper (Luxembourg Centre for Systems Biomedicine)
- George Alter (University of Michigan)
- Tiffany Boughtwood (Australian genomics)  
- Sarion Bowers (Wellcome Sanger Institute)  
- Anthony Brookes (University of Leicester)
- Moran Cabili (Broad Institute of MIT and Harvard)  
- Hayley Clissold (Wellcome Sanger Institute)  
- Melanie Courtot (EMBL-EBI)  
- Stacey Donnelly (GA4GH/Broad)  
- Stephanie Dyke (Mc Gill)  
- Melissa Haendel (OHSU)
- Francis Jeanson (IAMOPEN)
- Giselle Kerry (EMBL-EBI, EGA)  
- Melissa Konopko (Wellcome Sanger Institute)  
- Bartha Maria Knoppers (McGill University)
- Jonathan Lawson (Broad)  
- Greeshma Neglur (NCI Commons/U chicago)  
- Soichi Ogishima (ToMMo, GEM Japan)
- Laura Paglione (Spherical Cow)
- Ravi Pandya (Microsoft Research)
- Anthony Philippakis (Broad Institute of MIT and Harvard) 
- Jordi Rambla (Centre for Genomic Regulation, EGA)
- Greg Rushton (Broad Institute of MIT and Harvard)
- Kathy Reinold (Broad Institute of MIT and Harvard)
- Laura Rodriguez (NHGRI)  
- Andrea Saltzman (Broad)  
- Amanjeev Sethi (CanDIG, UHN)  
- Heidi Sofia (NIH)
- Dylan Spalding (EMBL-EBI, EGA)  
- Anne-Marie Tasse (McGill University)
- Adrian Thorogood (McGill University)
- Illia Tulchinski (Google)
- Marcio von Muhlen (HCA/CZI)  
- John Wilbanks (Sage Bionetworks)
- Chisato Yamasaki (Osaka Univ., GEM Japan)

## Other contributors (in alphabetical order)
ADA-M workstream  
[Consent codes](https://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1005772) authors   
Neil Otte    
Cooper Stansbury  

## Funding
Wellcome Trust-EBI grant 201535/Z/16Z

NIH/NHGRI 5U01HG009454-03

## DUO logos

DUO logos are available in 2 versions (click for larger versions)

<a href="https://github.com/EBISPOT/DUO/blob/master/doc/figs/DUO_logo_white_background.png"><img src="https://github.com/EBISPOT/DUO/blob/master/doc/figs/DUO_logo_white_background.png" height="100"></a>

<a href="https://github.com/EBISPOT/DUO/blob/master/doc/figs/DUO_logo_dark_background.png"><img src="https://github.com/EBISPOT/DUO/blob/master/doc/figs/DUO_logo_dark_background.png" height="100"></a>

DUO logos were designed by Spencer Phillips - EMBL-EBI, 2019.

## DUO pictograms

<img src="https://github.com/EBISPOT/DUO/blob/master/doc/figs/pictograms/DUO_overall_pictograms.png">


DURI working group of [GEM Japan](https://www.amed.go.jp/en/aboutus/collaboration/ga4gh_gem_japan.html) proposes the DUO pictograms for eight representative DUO codes, as a contribution to GA4GH.  The colors of the pictograms for the five DUO codes for “data limitation” are inspired by the hierarchy of the DUO codes and the colors of the DUO icons.  Those pictograms are originally designed by Akio Nagano ([PENQE](http://penqe.com/)).

DUO pictograms are available in [SVG](https://github.com/EBISPOT/DUO/blob/master/doc/figs/pictograms/duo_svg) or [PNG](https://github.com/EBISPOT/DUO/blob/master/doc/figs/pictograms/duo_png) format.
