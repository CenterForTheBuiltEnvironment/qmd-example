# A reproducible journal article template in RMarkdown

### Overview
This repository contains work in progress on an template for journal articles (eg for *Energy and Buildings*,  *Buildings and Environment*, or other journals that use the Elsevier format) along with examples for beginners. This example is slightly modified from the template from the `elsevier_article` template from the`rticles` package [here](https://github.com/rstudio/rticles). 


### How to use this repo
- This repository contains all the code and data to recreate the PDF file (`Manuscript.PDF`) in the `Paper` directory
- To re-run the code to reproduce all of the text and figures in this template paper:
    - Fork this repository (press the green button on the right side of this page)
    - Create a new RStudio project using the url for your new copy of the repository, which will download all of the files locally to the computer you are working on
    - Knit the file `Manuscript.Rmd` (you can do this by navigating to it in the `Files` pane, under `/Paper`, and clicking the "knit" button on the top left of the RStudio pane)
        - You may need to install some additional error packages if prompted to do so by errors during the knit. 
        - The packages used in this template are `tidyverse`, `here`, `knitr`, `ggpmisc`, `grateful`, `gt`
            - Most of the above packages can be installed using `install_packages()`, or the "Packages" tab in RStudio. 
            - However two of the above packages have not been published to CRAN yet, and require special installation by running:
```
install.packages("devtools")
remotes::install_github("rstudio/gt")
remotes::install_github("Pakillo/grateful")
```
        
### Contents of this repository
The key contents are organized as follows:

- rmd-example
    - Readme.Rmd
    - .here
    - LICENSE
    - Paper
        - Bibliography.bib 
        - Manuscript.PDF
        - Manuscript.Rmd
   
    - SupplementaryMaterial
        - Data
        - Images
        - Software_citations
        - src
        
    - Manuscript_files
        - figure_latex

The top-level directory contains a`Paper` directory where most of the files for this project are stored. The `.here` file designates this location as the starting point for all file paths executed within this project. It is important to have a 'LICENSE' file to make it clear if other people have the right to reuse and build on your code, and under what conditions. See the interactive ["Choose a license"](https://choosealicense.com/) guide for help selecting one. 

There are also additional files under `/Paper`:

- `Bibliography.bib` containing the BibTeX file with all the references used in this paper
- `Manuscript_files`, an automatically-created folder containing a separate .jpg image of each plot created in the manuscript
- `elsarticle.cls` for formatting the PDF 
- `elsevier-with-titles.csl` and `advances-in-building-energy-research.csl` for formatting citations with Zotero
- Some files created by the process of converting an Rmarkdown document to a PDF via LaTeX, such as `Manuscript.tex`, `Manuscript.fff`, `Manuscrpt.spl`, `Manuscript.ttt`. You do not need to edit these files. 

Under `SupplementaryMaterial`:

 - `Images` contains graphics that are not created programmatically 
 - `src` is the convention for a folder that contains additional .R scripts
 - `Software_citations` contains the output of the `greatful` package for all the software cited in this template
 - `Data` is a convention for a folder containing the data used in this analysis, since this dataset is relatively small and something that can be made publicly avalible. 
 
 