# Cerberus workflow overview
## Cerberus Modules overview
In a later chapter and also in the docs, all Modules and functions are described in more detail. This chapter is meant to provide an overview on the pipeline steps that will be needed in order to compute GIs, leaving out all the modules that are run internally in order to run the main pipeline steps. 

- GeneticInteractionSample module: process and store user input to provide to the other modules
- DataPreparation module: computing phenotypes from the read counts (LFCs)
- 3 gRNA level GI scoring modules:
  - multiplicative model (most simplistic way, adding up the single phenotypes of the genes and comparing this to the observed combinatorial phenotype)
  - Median Polishing (fitting a linear model to the data, residuals are the GIs)
  - LOESS fitting (choosing genes as context, and do local linear fitting through context to detect GIs)
- Gene level GI scoring module: aggregate gRNA scores to gene level and estimate their significance

*replace this with a scheme*

All modules are written in python except the Gene level GI scoring module, which is based on limma, an R package. Each module can be executed via python scripting. The communication between python and R modules is managed internally.

*elaborate on decision making maybe*

# Nullmodels Deep Dive
## Defining GIs
find unexpected phenotype given the single phenotypes or other baseline assumption.  
Nullmodels that are implemented in Cerberus
- multiplicative model
- median polishing
- loess fitting
  
# Supported Dataset Designs
## Dataset Designs
- fixed pair screen
- query screen
- multiplex screen

# Whick Nullmodel for which Dataset Design
