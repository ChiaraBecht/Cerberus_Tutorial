# Intro 
Cerberus will allow you, to identify Genetic Interactions (GIs) from systematic combinatorial CRISPR screens. Cerberus will support you in choosing the appropriate strategy for your dataset, by prodviding tight QC and multi-modular runs that allow checking for consistency of the GI signal. Furthermore, it is deployed in a docker container to facilitate accessibility.  
  
The input data for Cerberus is a read count table. If you do not have a read count table yet, but sequencing data from this screen you can use [ReCo!](https://github.com/MaWeffm/ReCo) to generate read count tables. Required columns are:
- 2 columns with Guide ids
- 2 columns with Gene ids
- 1 or several early time points / library timepoint /plasmid pool read count columns
- 2 or more end point read count columns

## Theoretical background on combinatorial CRISPR Screens and their analysis
Monogenetic CRISPR screens are a commonly used tool to study the function of genes. As the figure below shows. We can induce knockouts of different genes in cells. The fate of the cell in terms of cell fitness / viability allows conclusions about the gene's function. If a cell has low viability post-knockout, we can conclude, that the gene is essential for cell survival. This phenotype of the gene we classify as essential. If the cell viability remains unchanged through the knockout, we classify this gene as neutral phenotype. Is a cell prliferating a lot upon knockout, we assign the phenotype proliferator, since the knockout removed functionality in terms of controlling cell proliferation. Cell fitness /viability is more of a spectrum than distinct classes.  
placeholder figure: [Studying single genes' functin through perturbations]() 

Screening for function of genes systematically, we can conduct whole genome monogenetic CRISPR screens. That requires to design several guide RNAs (gRNAs) for all described genes in the genome. Then a cell population will be transduced with the CRISPR Cas system as well as the gRNAs. In the starting population of transduced cells, each gRNA should be represented similarly. Therefore, a high quality start population has an as uniform as possible gRNA-distribution. A representative fraction of this startpopulation is sequenced and gRNAs are counted to be used as library timepoint read count sample. The other cells are monitored over a timespan. At the end time point cells are harvested and DNA is extracted to again sequence gRNAs and count cells per knockout. This will result in the end time point samples. Over time cells, that have an essential gene knocked out, will be less represented, while cells with proliferator gene knocked out will be more represented. Therefore comparing end time points with library timepoint will assign a cell fitness score to each gene. Based on score and statistics (how reproducible this is among several gRNAs for a gene), relevant essential and proliferator genes can be identified.  
placeholder figure: [uniform start timepoint vs. biological effect end timepoint]()  

Due to genetic redundancy, buffering pathways, and other biological strategies to maintain cell function, genes can interact to carry out a shared task or buffer each others function. So far, this seems to be a rare phenomen, but it is quite intersting from a therapeutic perspective. To study whether genes interact with each other to carry out cell function, we can conduct combinatorial CRISPR screens. In this experimental set up, 2 genes per cells get edited. More on different design options are covered in a later section. Similar to the monogenetic screen, we can measure again cell fitness of this double knockout cells. Similar to the monogenetic screen we again aim for a uniform distribution of guide pairs transduced to the cell population, and we have a different distribution at the end timepoint, based on the function of the gene pairs. We again can compute a viability phenotype comparing end timepoint and start time point. 
placeholder figure: [combinatorial screen start vs endtimepoint]()

However, we are not intersted in the viability per se, but how this is different to what we would expect the phenotype to be. This expectation originates from what we know about the genes that are part of this pair to behave in a cell on their own. If our expectation and the observed combinatorial phenotype diverge, we call this a genetic interaction. The phenotype of these genes is due to something shared, that cannot be explained by the function of one of the genes alone. To identify GIs in a systematic way, we need to formulate a Nullmodel, that tells us what the baseline assumed phenotype for each gene pair in our screen is. More details on Nullmodels, and how they are implemented and applied in Cerberus can be found in a later chapter.  
placeholder figure: [combinatorial screen + nullmodel]()
  
## Why Cerberus
- Easy to use tool, that can be run with one command from the command line
- implemented different nullmodels, to accomodate most common dataset designs
- addressing runtime, data managment issues
- providing QC measures for every processing step
- guidance on best analysis method and therefore analysis outcome

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
