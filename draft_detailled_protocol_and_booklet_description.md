
# Short description of the practical

P12	Data handling and visual exploration of the processed and scored data from P3 / P9
(ATC, Flex Lab B)


Staff: Andrzej Oles, Mike Smith, Bernd Klaus

Work:
1. Importing the data into R, the concept of "tidy data", introduction 
to data handling strategies 
2. Visual exploration of data using quality-control related plots, e.g. heatmaps,
and PCA plots




# Short description of the practical


High-throughput microscopy screens with technologies such as RNAi, CRISPR-Cas
and libraries of drug compounds typically generate large quantities of data that
are potentially rich in biological information. Typically thousands of gene or
drug targets are screened and tens or even hundreds of image features are
extracted. Exploring these large datasets is challenging. R packages from
the "tidyverse" will lead the way here.


In the tutorial we will fist introduce the concept of "tidy data" that provides
a practically useful way of organizing big experimental datasets
and show how turning the initial data in to a "tidy" representation.

We will then demonstrate how to perform large-scale visualization of the screen 
results and show how to use this to explore patterns in the data. 

Methods such as Principal component analysis (PCA)  and clustering will be
employed and the participants will be introduced to the advanced graphical 
capabilities of R.

We will work on the cell-classification results from labs P3 / P9, so this 
this lab will lead the way to hit calling
strategies and comprehensive downstream analyses.

We will perform all analyses using open source R/Bioconductor software. 


Software:
R: http://www.r-project.org/ 
Bioconductor: http://www.bioconductor.org/
Tidyverse: https://blog.rstudio.org/2016/09/15/tidyverse-1-0-0/




--------------------------------------------------------------------------------

# Mail from Thomas, Sep 28th 
 
 found 2 plates from previous courses. The data contains two channels:
H2B, informative about chromosomes and tubulin, informative about the
spindle.

Segmentation and feature extraction in each of these channels allows us
in principle to :
- classify each "object" (chromosome or microtubule conformation,
respectively) separately into one out of several predefined
morphological classes
- make a joint classifier by concatenating features from the two channels.

As a result we obtain thus for each time point one or several
classification results per cell.

Now, in practice: I did not find classifiers for the two channels from
the previous years. For this reason, I made a new classifier for these
data on Friday and yesterday (so I annotated a number of cells), but as
this takes a bit of time I only made one classifier in the H2B channel.

I now run the analysis, as I understand that you would like to have
representative data as soon as possible. We will see what we will do
with the second channel afterwards, but at least you can start working
on this.

The analysis is now running, and I will send you results as soon as they
are ready.

Best,

Thomas.


# background on the experiments extracted from book on practicals from last years

* ref: http://www.nature.com/nature/journal/v464/n7289/full/nature08869.html

## Practical 3 will generate the data:

In this practical we will learn how to set up automated time-lapse imaging of
a multi-well plate. Specifically, we will image HeLa cells stably 
expressing H2B-mcherry and tubulin-GFP, plated on 96-well plates that
are coated with siRNAs causing mitotic phenotypes. 

## siRNA scoring scheme

To summarize the siRNA scoring: for each (TECHNICAL) replicate, we calculated one score in each
morphological class (and joint classes) as the maximal difference over time between the time
series in that class and the average negative control time series. The siRNA score was defined
as the upper median of the corresponding replicate scores, and a gene was considered as a
“potential hit” if at least one targeting siRNA had a score above the threshold. A gene was
considered as a “validated hit” if two or more siRNAs resulted in a consistent phenotype.
