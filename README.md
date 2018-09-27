[![Build Status](https://travis-ci.org/EBISPOT/DUO.svg?branch=master)](https://travis-ci.org/EBISPOT/DUO)



Table of Contents
=================

   * [DUO - the Data Use Ontology](#duo---the-data-use-ontology)
      * [Availability](#availability)
      * [What is DUO?](#what-is-duo)
      * [Versions](#versions)
         * [Stable release versions](#stable-release-versions)
         * [Editors' version](#editors-version)
      * [Contact](#contact)
# DUO - the Data Use Ontology - the essentials

## Availability

The latest version of the ontology can always be found at: http://purl.obolibrary.org/obo/duo.owl

DUO can be browsed online via the [Ontology Lookup Service](http://www.ebi.ac.uk/ols/ontologies/duo/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FDUO_0000001) or [Ontobee](http://www.ontobee.org/ontology/DUO). 

It has been registered with the [OBO Foundry](http://obofoundry.org/ontology/duo.html).

## What is DUO?

An ontology based on the consent codes decsription from the Dyke et al. paper at http://dx.doi.org/10.1371/journal.pgen.1005772

It allows to semantically tag datasets with restriction about their usage, making them discoverable automatically based on the authorization level of users, or intended usage.

This resource is based on the OBO Foundry principles, and its use is under review by the [European Genome-phenome Archive](https://ega-archive.org) (EGA) at EMBL-EBI as well as the Broad Institute for the [Data Use Oversight System](https://duos.broadinstitute.org/#/home) (DUOS).

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

# DUO - Full documentation

## What is DUO?
The (GA4GH) Data Use Ontology (DUO) includes terms describing data use conditions and restrictions, particularly for research data in the health/clinical/biomedical domain. 

Human subjects datasets often have restrictions such as “only available for cancer use” or “only available for the study of pediatric diseases,” deduced from the original biospecimen collection informed consent form, which must be respected when sharing and studying these datasets. 

A current challenge in sharing such datasets for further research is that unique language is used in each informed consent form to describe the secondary use restrictions/conditions. 
The lack of a standard universal system to categorize these conditions makes it difficult for data access committees and researchers to interpret the conditions in a consistent, structured way.

The goal of this resource is to allow large genomics and health data repositories to share the same terminology when describing data use restrictions/conditions. In addition, we envision a future where web services would submit queries to these repositories such as “return all datasets that can be used to study melanoma by a commercial entity” that will help researchers find relevant data that is compatible with their research purpose. DUO includes ontology terms needed to represent such queries as well as the ontology hierarchy necessary for algorithms to determine whether a research purpose is compatible with the dataset restrictions.  

A further goal is to encourage the authors of new consent forms to align consent language with the terms used by DUO; this would eliminate the need for subsequent review of consent forms to classify data use and speed the availability of data for secondary use.

## How did DUO come about?
Some of the challenges in standardizing and introducing automation to the process of sharing human health and genomics data is that clinical research studies each use unique language in the informed consent form. This means that the written free text is often difficult to translate into a clear data use restriction/conditions.  This severely limits the ability to reuse vast stores of data in a timely fashion.

Currently, there is no common ontology to which consent forms can be translated for researchers or DACs to interpret the free text restrictions in a structured way. 

The lack of such an ontology is a missed opportunity to guide/inform the writing of consent form language.

DUO represents data use terms from three evolving efforts to standardize data use restrictions in the biomedical and genomics research domain:
The NIH’s dbGaP data use categories. The NIH database of Genotype and Phenotype is one of the largest public repositories of genomics data in the world. While ingesting data to the system depositors are asked to use a controlled vocabulary (see ,  Points to Consider in Drafting Effective Data Use Limitation Statements https://osp.od.nih.gov/wp-content/uploads/NIH_PTC_in_Drafting_DUL_Statements.pdf)  to represent the restrictions for secondary use of the deposited datasets. For example, classify a dataset as General Research Use (GRU), or Health/Medical/Biomedical research only (HMB). This controlled vocabulary was defined in 2011-2012 and has been the foundation for this ontology. There are over 1000 studies labelled with data use restrictions using these terms. Some of the challenge with the way the controlled vocabulary is currently being applied: (1) it doesn’t encode the hierarchy between terms; (2) it was often coupled to free text describing disease types.  Both of these aspects make it difficult for algorithms to make logical inference on this information.  
Consent Codes by Dyke et al. A global team effort led by Stephanie OM Dyke to define ‘codes’ for specific categories of data use restrictions based on the datasets of the main public genome archives (NCBI dbGaP and EMBL-EBI/CRG EGA). The ‘codes’ extend the controlled vocabulary and classification approach of dbGAP and define a hierarchy and approachable classification rules. Read more here: https://doi.org/10.1371/journal.pgen.1005772
The Automated Data Access Matrix (ADA-M). A global team effort led by Anthony Brooks and a GA4GH workstream to define a matrix of data use categories that can be used to define both: (a) the data use restrictions on a dataset, and (b) a research purpose. The ADA-M is a complementary approach for classifying data use restrictions and permissions with greater granularity than consent codes and can address an expanded set of use cases. Read more here: Woolley & Brooks et al. NPJ Genomic Medicine, 2018, https://www.nature.com/articles/s41525-018-0057-4 

## Evolution of DUO
DUO is an evolving effort to provide digital ontological representation for all the data use categories defined by the efforts mentioned above. Its evolution is driven by driver projects of the Global Alliance for Genomics and Health (GA4GH) such as the EMBL-EBI/CRG EGA, the All Of Us research program and the NIH Data Commons Pilot. 

The first version of DUO described the original terms from the Dyke et al. 2016 publication on Consent Codes (https://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1005772).  The second version has evolved to include additional terms as described at the  Woolley et al. 2018 publication on ADA-M  (https://www.nature.com/articles/s41525-018-0057-4) as well as updates to definitions based on input from the GA4GH driver projects and the GA4GH Data Access Product line, Data Use Ontology workstream.

We welcome the community’s input and contributions. 

Please contact DURI@ga4gh.org if you are interested in adopting DUO in your organization, would like to suggest changes, or to submit a request under the issue tracker.

## Examples of use
### Tagging with ‘data use restrictions/conditions’
DUO is used by multiple services to tag datasets with data use restriction terms and categories.  For example, the European Genome-phenome Archive (EGA), a service for permanent archiving and sharing of all types of personally identifiable genetic and phenotypic data under controlled access and jointly hosted by European Bioinformatics Institute (EMBL-EBI) and the Centre for Genomic Regulation (CRG), is now supporting the use of DUO to indicate the data use conditions applied to their datasets. The EGA has been working with the Wellcome Trust Sanger Institute to apply DUO to existing datasets, which are now tagged at EGA. To access data at EGA an application is made to the associated Data Access Committee (DAC), which for the Sanger Institute can be accessed via an electronic Data access Mechanism.
  
### Powering dataset discovery queries
DUO is instrumental in supporting services that allow advanced search options by matching a research purpose to datasets tagged with compatible data use restrictions terms.  

For example, the query: find all datasets that can be used to study cancer within a commercial entity. Such queries to discover datasets are enabled by algorithms that reason on the ontology’s hierarchical structure to match the query represented by ontology terms with datasets tagged with terms from the same ontology. 

One such algorithm-based service is the Broad Institute’s Data Use Oversight System (DUOS). DUOS is piloting a trial in which a data access committee comprised of experts in data use oversight evaluate data access requests in parallel with the algorithm. This trial leverages the experts’ feedback to improve the algorithm and the ontology and has been contributing to the evolution of DUO.  As an example, here is a description of how the DUOS matching algorithm (and public APIs) work.

The following figure illustrates how DUO terms can be used to represent data use restrictions on datasets (left) as well as a research purpose query (right) using the DUO ontology terms.  

![alt tag](https://github.com/EBISPOT/DUO/blob/master/doc/figs/DUO_matching.png "DUO matching")

## Automated data access requests
In the long term, we envision DUO coupled with matching algorithms such as DUOS to empower services that automatically determine if a user’s research purpose is compatible with data use restrictions on datasets and in turn determine whether to give a researcher access to the data.  
How does querying work when using DUO?
So, how would an algorithm use DUO onotology to match research purposes and data use restrictions? 
This is a deep dive into the algorithm’s matching function for those interested, feel free to skip!
 
The request for a dataset needs to be matched against the existing data use restrictions on stored datasets. These assessments could be run against either 1) the person making the request (e.g., do they belong to a for-profit/non-profit organization?) or 2) their specific research purpose itself (e.g. can I use this dataset for cancer research?)

When using DUO-powered automated matching systems, its important to note the query is ALWAYS expected to be made and the most specific level. This means that:

An important aspect of using DUO in automated matching systems is that the query is ALWAYS expected to be made at the most specific level. This means that:

A query for datasets consented for cancer research  WILL NOT retrieve datasets consented for lung cancer, because lung cancer is a subtype of cancer in a disease hierarchy and the ontology needs to ensure the datasets will only be used to study specifically lung cancer.
A query for datasets consented for lung cancer research WILL retrieve datasets consented for cancer, as lung cancer is a subtype of cancer in a disease hierarchy.

The image below illustrates an example of matching a query and how studies labeled with Consent Codes/ Data Use Ontology terms  can be mapped to the data use ontology tree. 

A researcher describes he would like to study Melanoma and find all datasets compatible with this research purpose.  
A matching algorithm will start by detecting Melanoma research in the ontology hierarchy (dotted circle) and will return every datasets that is labeled with PARENT NODES , going up in the hierarchical ontology tree/ directed acyclic graph. 


