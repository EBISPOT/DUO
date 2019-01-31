## GA4GH DURI onboarding

Status: DRAFT!

Author: [nmcabili@broadinstitute.org](mailto:nmcabili@broadinstitute.org),  [nyronen@csc.fi](mailto:nyronen@csc.fi) , 

Modified 14.11.2018

Welcome to the GA4GH Data Use and Researcher Identity (DURI) product line!


### Vision (draft)

There are restrictions on the use of human genomics data that are derived from ethical requirements including participants' research consent. For example: "Data can only be used for breast cancer research with non-commercial purpose". The current process to request access to data to ensure studies are consistent with these restrictions is inefficient and slows down science.

**We envision a world where biomedical researchers will be able to efficiently discover genomics and health data, and then apply and get access automatically based on their digital identity and, if required, a machine readable research purpose.**

 To achieve this, researchers need to have a reliable global electronic identity that is recognised for data access. In collaboration with the data authorities who are responsible for proper data use, this researcher identity would be authorised to access restricted data. We envision this type of access could be allowed for this use across a federated network of data repositories for researchers who have a trust attribute on their identities.  For example: researchers would be able to query a network of repositories across country borders and _find the genomes and phenotypes of all females of the age of 20-40 that have a BRCA mutation and can be used to study cancer_; once they found that data they would be able to apply  to access the data in an easy fashion and could often also instantly  get access to research the data based on a digital assessment of appropriate claims, trust credentials and agreed policy. 



### Insert Diagram 1
**--->** 

### Insert diagram 2


                                                                                   


### Mission (draft)

Our group's mission is to create the standards that will enable automated data discovery and access and drive their evolution. We do this in partnership with driver projects that support our standard creation and promote their adoption.

Specifically, we:



1.  Establish a globally recognised researcher identity standard that human data service providers can rely on, and create a model to decorate these electronic identities with trusted claims/attributes.
1.  Develop a Data Use Ontology (DUO) that supports algorithm-based automated matching between a research purpose and data use restrictions on datasets. 
1.  Establish a researcher Library Card/Access Passport standard, a digital identity that describes claims about the "bonafide" researcher status of an individual enabling:
    1.  A user to enter a 'registered access' environment in which they make exploratory discovery queries without stating their research purpose
    1.   An automated data access process where access decision can be made based on a codified research purpose, the digital identity and ethics approval claims.


### How to contribute

To become a member please email: [melissa.konopko@ga4gh.org](mailto:melissa.konopko@ga4gh.org)

Or [CLICK HERE](https://groups.google.com/a/ga4gh.org/forum/#!forum/ga4gh-data-use-subgroup) and choose "Apply for membership".


### Product line leads


### Background reading

[The mandate of  of the Data Access Product line & 2018 roadmap](https://docs.google.com/document/d/1D7-CJc5GI-m2LUnnBqHgcTBUH04yQcKB64UgN5rprEc/edit#heading=h.4k2yyo8a2zek)

[What is the Data Use Ontology](https://github.com/EBISPOT/DUO)? (read the Readme on the Github page, scroll down)

[The Library Card concept ](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5851345/) (the Library Card paper)

[Registered Access data access policy model](https://www.nature.com/articles/s41431-018-0219-y) (the Registered Access paper)

[DURI definitions](https://docs.google.com/spreadsheets/d/1jlXvkjYrg8KbHBfr6AsfzYwaSAnk5PkDDmsBqfWCGdk/edit#gid=0) 


#### Reference papers

This set of papers describe the foundational standard work and the motivation for the standards DURI is creating.

Consent codes - Dyke et al.  [https://doi.org/10.1371/journal.pgen.1005772](https://doi.org/10.1371/journal.pgen.1005772)

ADA-M - Woolley & Brooks et al. [https://www.nature.com/articles/s41525-018-0057-4](https://www.nature.com/articles/s41525-018-0057-4)

Library Card- Cabili & Pandya et al. [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5851345/](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5851345/) 

Registered access model- Dyke et al.  [https://www.nature.com/articles/s41431-018-0219-y](https://www.nature.com/articles/s41431-018-0219-y)

Federated identity management for research collaborations [https://zenodo.org/record/1307551](https://zenodo.org/record/1307551#.W-xc-OgzYuU) 

ELIXIR Authentication and Authorisation [https://f1000research.com/articles/7-1199/v1](https://f1000research.com/articles/7-1199/v1) 


#### Product design documents - work in progress

[GA4GH research identity claims (RFC)](https://docs.google.com/document/d/1jvMpHmCWqcigqy1FuEzqXzHlaGeNP2mClOU2Ui4Djhg/edit)

[DUO github repo](https://github.com/EBISPOT/DUO)

[Meeting minutes ](https://drive.google.com/open?id=0B09Q6AWnrBnScGR2VmJ3OHNicWs)(directory)


#### Presentations- Basel 2018

[Researcher Identity product](https://docs.google.com/presentation/d/1H9p0rbnYUx64mFWO_iHBYchxs6lBGHJyJ1bm5flcztg/edit#slide=id.p) 2018

[Data Use Ontology](https://docs.google.com/presentation/d/1B4jsqnZIqwxLjL8Y1q41kYFNN8BsmmiEC6I9_WZZPt0/edit#slide=id.p) 2018


### Dictionary


### 2019 Proposed Goals

[Draft goals (Basel Plenary 2019)](https://docs.google.com/document/d/1b6_gb6ysz45-KCCjsneZFa5oSUMHLUO0vCOKDPAFfiM/edit#bookmark=id.1h4svh42j3io)

DUO:



*   Release DUO V2
    *   Resolve GRU vs. GRU-CC controversy based on driver project data stewards input. 
        *   Input from: dbGaP (NIH Data Sharing Council), TOPMED (Kathy Laurie), AoU (Laura R, Pearl O'rourke), Sanger DAC for EGA, Australian genomics, someone from THL?,   who else?
*   Have 2-3 software products adopt DUO for data discovery (e.g. an algorithm will match DUO terms  describing research purpose and restrictions on data)
    *   Groups that have expressed interest
        *   DUOS for TOPMED/ANVIL (moran)
        *   REMS (Tommi, Mikael)
        *   Google cloud data access test bed  (Aleksandra, Craig) 
        *   EGA? (Melanie)
        *   Datadex (Francis Jeanson)

RI:



*   Find 2 (or more) driver projects and  **data steward **that would like to enable controlled access or registered access decisions based on a library card
*   Develop the RI claims to ensure they address the requirements of the >2 stewards
*   Implement a test bed for the implementation (google team expressed interest)
*   Implement an alpha version of 2 driver project that pilot this library card for sharing
*   Implement a project where ana EU and US identities are accepted (Elixir and eRA Commons?)
    *   Suggested projects
        *   TOPMED: automated discovery for NHLBI DataSTAGE pilot with a "data passport " issued on top of eRA identities
        *   Elixir + THL? (which dataset and stewards can we engage for this pilot? ) 
        *   CANDIG 
        *   EGA registered access beacon
        *   NHGRI AnVIL data environment with [DUOS](https://duos.broadinstitute.org/#/home)


### 2019 roadmap

