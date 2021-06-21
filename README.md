# ASPECT: wind energy v**A**riable**S** **P**aramet**E**rs and **C**ons**T**ants
This repository is meant for maintaining and updating the taxonomy (i.e. controlled vocabulary) of v**A**riable**S** **P**aramet**E**rs **C**ons**T**ants (ASPECT) used in wind energy community. In general, controlled vocabularies such this one allow an accurate and controlled approach in describing assets such datasets.

We use `sheet2rdf` and `OntoStack` to build and serve ASPECT taxonomy. 

# sheet2rdf

This repository hosts automatic workflow, executed by means of Github actions, and underlying shell and python scripts which:

- [Fetches Google Sheet](https://docs.google.com/spreadsheets/d/1IzJ9cCVmoU2tcZ-P4xr405LE36aqhleiL6rvibAsCEo/edit#gid=1472229997) from Google Drive, which contains definitions of concepts (i.e., variables, parameters and constants), and converts it to `xlsx` and `csv` and stores these files to this repository
- Converts fetched sheet to machine-actionable and FAIR RDF vocabulary using [xls2rdf](https://github.com/sparna-git/xls2rdf)
- Tests the resulting RDF vocabulary using [qSKOS](https://github.com/cmader/qSKOS/)
- Commits conversion results and tests logs to this repository
- and deploy RDF vocabulary to OntoStack to be served to humans and machines

# OntoStack

OntoStack is a set of orchestrated micro-services configured and interfaced such that they can intake vocabularies and resolve their terms and RDF properties upon requests either by humans or machines.

Some of OntoStack micro-services are:

- [Jena Fuseki](https://jena.apache.org/documentation/fuseki2/) a graph database
- [SKOSMOS](http://www.skosmos.org/) a web-based SKOS browser acting as a front-end for the vocabularies persisted by the graph database
- [Træfik](https://doc.traefik.io/traefik/) an edge router responsible for proper serving of URL requests

**ASPECT** is served by DTU Wind Energy instance of `OntoStack`:
https://data.windenergy.dtu.dk/ontologies/view

