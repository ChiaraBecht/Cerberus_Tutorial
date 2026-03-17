# Intro 
Cerberus will allow you, to identify Genetic Interactions (GIs) from systematic combinatorial CRISPR screens. Cerberus will support you in choosing the appropriate strategy for your dataset, by prodviding tight QC and multi-modular runs that allow checking for consistency of the GI signal. Furthermore, it is deployed in a docker container to facilitate accessibility.  
The input data for Cerberus is a read count table. If you do not have a read count table yet, but sequencing data from this screen you can use [ReCo!](https://github.com/MaWeffm/ReCo) to generate read count tables. Minimal columns in the dataset need to be a library read count (or early timepoint) and end point read count.

## Dataset Designs
- fixed pair screen
- query screen
- multiplex screen

## Defining GIs
find unexpected phenotype given the single phenotypes or other baseline assumption.  
Nullmodels that are implemented in Cerberus
- multiplicative model
- median polishing
- loess fitting

## Objectives 📍
- Learn how to run Cerberus to identify GIs
 
- get the necessary software  
- Ask and answer questions


## Prerequisities

- working with linux or OS command line
