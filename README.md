# First steps

## Introduction

The SqueezeMeta pipeline automatically analyses a metagenomic/metatranscriptomic project and generates a large number of tables containing useful information. The SQMtools package for R parses that information and includes a number functions to plot, subset and export all that data into visual graphs and tailor-made tables.

The SQMtools package makes all calculations and plotting adjustments transparent to the user, who just needs to write the parameters to select the plotted data. Still, this process requires from a minimum of programming experience.

The objective of the SqueezeMeta project was to make metagenomic/metatranscriptomic analyses accessible to all users, even those with no programming experience. This includes the data visualisation step.

The SQMxplore package solves this need to create a user-friendly interface to explore the results of a SqueezeMeta project. SQMxplore is an interactive data visualisation tool integrated in the SqueezeMeta environment, based on the Shiny package for R.

## Installation

The easiest way to install SQMxplore from GitHub using `devtools`. First open an R session or Rstudio, and run the following commands:
```
if(!require(devtools)) { install.packages("devtools"); library(devtools) }
install_github("redondrio/SQMxplore")
```

To install SQMxplore without the `devtools` package, download SQMxplore using the "Download ZIP" option at the GitHub repository.
Then open a terminal window at the directory where the package was downloaded and run the following commands (changing the file names if necessary):
```
unzip SQMxplore-tfm.zip
R CMD build SQMxplore
```
If everything runs correctly, the a .tar.gz file should appear in the directory.
Next step is to open an R session in that directory and run the line:
```
install.packages("./SQMxplore_0.2.tar.gz", repos = NULL, type="source")
```

Now the SQMxplore package can be loaded into an R environment using `library(SQMxplore)`.

## Project preparation

SQMxplore requires a SqueezeMeta project and the tables generated by the SQMtools package.
To prepare a project that can be loaded into SQMxplore, some previous steps must be run:

* **Generate a project with SqueezeMeta**

Plase refer to the [SqueezeMeta documentation](https://github.com/jtamames/SqueezeMeta "SqueezeMeta documentation") for this step. Any project created with SqueezeMeta can be loaded into SQMxplore, including reads and longreads projects.

* **Generate the SQMtools tables**

Plase refer to the [SQMtools documentation](https://github.com/jtamames/SqueezeMeta/wiki/Using-R-to-analyze-your-SQM-results "SQMtools documentation") for this step. These tables are automatically generated when a project is loaded into R with the `loadSQM()` or `loadSQMlite()` functions. For `sqm_reads` and `sqm_longrads` projects, please refer to the use of `sqmreads2tables.py` script.

Once these tables are generated, SQMxplore will have all needed data to start working.

## Launching the app

Before the app can be launched, it might be the case that your computer asks you to specify the web browser to use. In that case, you will see the following error when trying to launch the app:
```
Error in utils::browseURL(appUrl) :
'browser' must be a non-empty character string
```

To solve this, all you need to run is the following command:
`options(browser="/path/to/browser")`
where `/path/to/browser` must be the absolute path to your preferred browser executable.

Once the package is installed and loaded (using `library(SQMxplore)`) and all data is ready, you will just need to run the command `SQMxplore()` to launch the app from your R or Rstudio console. Please bare in mind that SQMxplore will take as its working directory the same path as the R session it is launched from.

## Loading a project

When the app is loaded, the first tab will show a directory selector.

SQMxplore accepts two types of input. First, an SQM project can be directly loaded as an SQMlite object with the "Load directly from SQM project" option. In this case, your must choose the parent directory to your project.
Second, an .rds file containing an SQM or SQMlite object can be loaded with the "Load from pre-saved RDS file" option.
After selecting the type of input (SQM project or .rds file) and choosing your project name among the list of available projects, you can click on the "Load project" button.

# The app
## Summary tab
The summary tab will only show information when an SQM project is directly loaded.
This tab shows all information contained in the .stat files that are generated when running SqueezeMeta, including reads, ORFs, contigs, bin and taxonomy stats. These sections may vary among projects run with different parameters.
Two barplots are displayed to visualise the number of reads and bases in the samples. In the ORFs section, two custom barplots are available for the user to select and compare two of the variables associated with ORFs.

## Tables tab
This tab is meant for the user to explore the numeric tables and extract any desired data into .csv format.
Two section selectors are available to access all the tables in an SQMlite object. A third selector is available for sections with multiple tables containing the data in different units.
The selected table can be exported into a .csv file using the "Download table" button.

## Plot Taxonomy and Plot Functions tabs
These tabs automatically generate plots with the functions `plotTaxonomy()` and `plotFunctions()` form the SQMtools package.
All available parameters are available for the user to set. The plots automatically update when any parameter is changed.

![Taxonomy tab](https://github.com/redondrio/SQMxplore/blob/master/data/.SQMx_tax_tab.png "Taxonomy tab")
![Functions tab](https://github.com/redondrio/SQMxplore/blob/master/data/.SQMx_fun_tab.png "Functions tab")

For any questions on the meaning or the underlying code, please refer to the [SQMtools documentation](https://github.com/jtamames/SqueezeMeta/wiki/Using-R-to-analyze-your-SQM-results "SQMtools documentation")
The plots can be saved locally into .pdf format using the "Download button" below the plot.


