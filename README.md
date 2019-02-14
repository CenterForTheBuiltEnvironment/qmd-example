A reproducible journal article template in RMarkdown
================

-   [](#section)
    -   [Overview](#overview)
    -   [How to use this repo](#how-to-use-this-repo)
        -   [1. Short-term and in the cloud (no installation required)](#short-term-and-in-the-cloud-no-installation-required)
        -   [2. Longer term and on your own computer (may require installing some additional R packages and also LaTeX if you don't have it installed already)](#longer-term-and-on-your-own-computer-may-require-installing-some-additional-r-packages-and-also-latex-if-you-dont-have-it-installed-already)
    -   [Contents of this repository](#contents-of-this-repository)
    -   [Troubleshooting](#troubleshooting)
        -   [Installing MikTex on Windows](#installing-miktex-on-windows)

[![Binder](http://mybinder.org/badge_logo.svg)](http://mybinder.org/v2/gh/CenterForTheBuiltEnvironment/rmd-example/master?urlpath=rstudio)

### Overview

This repository contains work in progress on an template for journal articles (eg for *Energy and Buildings*, *Buildings and Environment*, or other journals that use the Elsevier format) along with examples for beginners. This example is slightly modified from the template from the `elsevier_article` template from the`rticles` package [here](https://github.com/rstudio/rticles).

### How to use this repo

**This repository contains all the code and data to recreate the PDF file (`Manuscript.PDF`) in the `Paper` directory, including re-creating all the figures. **

There are two ways to use this template:

1.  Short-term and in the cloud (no installation required, suitable for short demonstrations or exploration, will time out after 10 minutes of inactivity)

2.  Longer term and on your own computer (may require installing some additional R packages)

#### 1. Short-term and in the cloud (no installation required)

-   Click the "launch Binder" button at the top of this page to open all of the code and data in this repository in an RStudio session where all of the required software is already installed.

-   In the lower right corner, click on the `Paper` folder, click on `Manuscript.Rmd`, and press the "knit" button (on the top left). You may be prompted to update some packages the first time you knit the document - click 'yes' to accept

-   When the newly-regenerated PDF document appears on the lower right version of the screen (you will see the timestamp is newer), click on it to open it. Congrats - you just re-ran this entire template!

-   If you want to explore making some changes, you can edit the `Manuscript.Rmd` file and re-knit the document to create an updated PDF.

#### 2. Longer term and on your own computer (may require installing some additional R packages and also LaTeX if you don't have it installed already)

-   Fork this repository (press the green button on the right side of this GitHub page)
-   On your computer, open RStudio and create a new RStudio project using the url for your new copy of the repository, which will download all of the files locally to the computer you are working on
-   Check if you have a version of LaTex installed on your computer. You can check this by typing `Sys.which(pdflatex)` in the R console. If the output is blank, you will need to install LaTeX.
    -   The recommended way to install a small version for LaTeX customized for RMarkdown is to use the TinyTex package (Mac/Windows/Linux), per the instructions [here](https://yihui.name/tinytex/)
    -   If for some reason TinyTeX doesn't work for you, there is a larger LaTeX version for Windows called MikTeX. *See the more detailed instructiosn + troubleshooting for MikTeX at the bottom of this page*
-   Knit the file `Manuscript.Rmd` (you can do this by navigating to it in the `Files` pane, under `/Paper`, and clicking the "knit" button on the top left of the RStudio pane) - You may need to install some additional error packages if prompted to do so by errors during the knit. - The R packages used by this template are `tidyverse`, `here`, `knitr`, `ggpmisc`, `grateful`, `gt`, `bookdown`,`rticles`, `devtools`, `rmarkdown` - Most of the above packages can be installed using `install_packages()`, or the "Packages" tab in RStudio. - However two of the above packages have not been published to CRAN yet, and require special installation by running:

<!-- -->

    install.packages("devtools")
    remotes::install_github("rstudio/gt")
    remotes::install_github("Pakillo/grateful")

### Contents of this repository

The key contents are organized as follows:

-   rmd-example
    -   Readme.Rmd
    -   .here
    -   LICENSE
    -   Paper
        -   Bibliography.bib
        -   Manuscript.PDF
        -   Manuscript.Rmd
    -   SupplementaryMaterial
        -   Data
        -   Images
        -   Software\_citations
        -   src
    -   Manuscript\_files
        -   figure\_latex

The top-level directory contains a`Paper` directory where most of the files for this project are stored. The `.here` file designates this location as the starting point for all file paths executed within this project. It is important to have a 'LICENSE' file to make it clear if other people have the right to reuse and build on your code, and under what conditions. See the interactive ["Choose a license"](https://choosealicense.com/) guide for help selecting one.

There are also additional files under `/Paper`:

-   `Bibliography.bib` containing the BibTeX file with all the references used in this paper
-   `Manuscript_files`, an automatically-created folder containing a separate .jpg image of each plot created in the manuscript
-   `elsarticle.cls` for formatting the PDF
-   `elsevier-with-titles.csl` and `advances-in-building-energy-research.csl` for formatting citations with Zotero
-   Some files created by the process of converting an Rmarkdown document to a PDF via LaTeX, such as `Manuscript.tex`, `Manuscript.fff`, `Manuscrpt.spl`, `Manuscript.ttt`. You do not need to edit these files.

Under `SupplementaryMaterial`:

-   `Images` contains graphics that are not created programmatically
-   `src` is the convention for a folder that contains additional .R scripts
-   `Software_citations` contains the output of the `greatful` package for all the software cited in this template
-   `Data` is a convention for a folder containing the data used in this analysis, since this dataset is relatively small and something that can be made publicly avalible.

### Troubleshooting

-   If you have knitted this document on your computer, opened the PDF (eg in Adobe Acrobat), and then try to re-knit the PDF while the file is open, the process will fail. Close the PDF, re-knit it, then re-open

#### Installing MikTex on Windows

[TinyTeX](https://yihui.name/tinytex/) is great, please try it first if you haven't already.

If you're not able to use TinyTex, then:

##### 1. Install MikTeK

<https://miktex.org/download>

To mamage your settings with MikTeX, open the newly-installed MikTeX Console, and - Under Settings --&gt; General, select " Always install missing packages on-the-fly" - Under Settings --&gt; Directories, copy the file path for "Links to the executables have been installed in", which might look like `C:\Users\YourName\AppData\Local\Programs\MiKTeX 2.9`

If you get "pdflatex not found" error when compiling .tex file on knit, check if the environment variable set:

``` r
Sys.which("pdflatex")
pdflatex 
#Source: https://tex.stackexchange.com/questions/398218/pdflatex-not-found-windows
```

##### 2. Create and edit an .Renviron file to provide path to pdflatex.exe in the MiKTeX directory listed above

``` r
#to programmatically create an Renviron file, uncomment lines below (commented out for knit)
#install.packages("usethis")
library(usethis)
#usethis::edit_r_environ("rticles_test") # This creates an .Renviron file
```

Now, edit the .Renviron file to contain the file path to `pdflatex` (adjust for your file path as needed) and save it

    #pdflatex
    PATH=C:\\Users\\Dana\\AppData\\Local\\Programs\\MiKTeX 2.9\\miktex\\bin\\x64;"${PATH}"

Reference: <https://community.rstudio.com/t/how-to-set-a-variable-in-renviron/5029/3> <https://stackoverflow.com/questions/33650869/how-can-i-set-the-latex-path-for-sweave-in-r>

##### Now try to knit the .Rmd file to a PDF!

More references:

<https://stackoverflow.com/questions/48224162/knitr-wont-compile-pdf-error-in-toolsfile-path-as-absoluteoutput-file>

<https://medium.com/@sorenlind/create-pdf-reports-using-r-r-markdown-latex-and-knitr-on-windows-10-952b0c48bfa9>

<https://rickpackblog.wordpress.com/2017/10/04/miktex-install-for-r-windows-pdf-output-r-markdown/>

If you experience an error like this: "Error in tools::file\_path\_as\_absolute(output\_file)" it may be resolved by changing the miktex settings to install required packages automatically on the fly.

Reference: <https://stackoverflow.com/questions/48224162/knitr-wont-compile-pdf-error-in-toolsfile-path-as-absoluteoutput-file>
