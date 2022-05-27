# GeneLab Summer Internship: Microarray Data Processing Pipeline Development Project

- [GeneLab Summer Internship: Microarray Data Processing Pipeline Development Project](#genelab-summer-internship-microarray-data-processing-pipeline-development-project)
  - [Reading List](#reading-list)
  - [Software](#software)
    - [All Operating Systems](#all-operating-systems)
    - [Windows Only](#windows-only)
  - [Conda Environment Setup](#conda-environment-setup)
    - [How To Install Internship Conda Environments](#how-to-install-internship-conda-environments)
  - [Project Roadmap](#project-roadmap)

## Reading List

These articles should be reviewed before starting the internship.

Programming:
- placeholder

Microarray:
- placeholder

## Software

These should be preinstalled on your machine.
If they are not, reach out to your intern mentor.

### All Operating Systems

- [Anaconda](https://www.anaconda.com/products/distribution)
  - How will we use this?
    - Anaconda (often colloquially referred to as conda) will be used to access bioinformatics libraries and tools.
  - How to install?
    - Install via OS specific installer obtained from this [page](https://www.anaconda.com/products/distribution).

- [VSCode](https://code.visualstudio.com/)
  - How will we use this?
    - This integrate development environment (IDE for short) includes a powerful editor, version control, automatic code formatting and other features that enhance the programming experience within a GUI.
  - How to install?
    - Install via OS specific installer obtained from the VSCode downloads [page](https://code.visualstudio.com/download).

### Windows Only

- [MobaXterm](https://mobaxterm.mobatek.net)
  - How will we use this?
    - This provides a better command line experience especially useful for interacting with remote systems.
  - How to install?
    - Install using the 'Installer Edition' .msi file found [here](https://mobaxterm.mobatek.net/download-home-edition.html)

## Conda Environment Setup

Conda allows one to install tools in isolated environments.  This is often much simpler that installing tools through other means (assuming of course that tools exist on Anaconda)

### How To Install Internship Conda Environments

The following environments will be needed during the internship.

``` bash
conda env create -f <file.yml>
```

All files are located in the 'condaEnv_yamls' directory contained in this packet.

Below the tools installed in each environment are listed:

- glds_microarrays_nf
  - [python](https://www.python.org/)
  - [r](https://www.r-project.org/)
  - [pandoc](https://pandoc.org/)
  - Key R Libraries
    - [knitr](https://github.com/yihui/knitr)
    - [bioconductor](https://www.bioconductor.org/)
    - [limma](https://bioconductor.org/packages/release/bioc/html/limma.html)
    - [oligo](https://bioconductor.org/packages/release/bioc/html/oligo.html)

- nextflow
  - [nextflow](https://nextflow.io/)


## Project Roadmap

This project will seek to further develop and test GeneLab's Microarray Data Processing Pipeline.

Additionally, creating a V&V program for validating and verifying Microarray processed data.

Timeline:

1. Week 1 (6/8 - 6/10): Review of Literature and Existing Pipelines
    1. Tasks
        1. Review Literature: Microarray Processing Best Practices
            - Some questions to consider: 
              - What major steps are performed?
              - What tools/libraries exist for Microarray processing?
    2. Deliverables
        1. Questions about material reviewed
        1. Annotated Bibliography for reviewed articles
            - [What is an annotated bibliography?](https://www.youtube.com/watch?v=R0Hsnx0l1q4)

1. Week 2(6/13 - 6/17): Development Setup
    1. Tasks
        1. Setup Github Account 
        1. Install Software
            - [See above](#software)
        1. Select 3 test GLDS datasets that meet the one of the following criteria (Both platforms will need to be covered so please coordinate with your colleague):
            - Platform: Affymetrix 1 Channel, at least 2 organisms, ideally 3
            - Platform: Agilent 1 Channel, least 2 organisms, ideally 3
    2. Deliverables
        1. Collaboration invite to your internship Github repo
        1. Installed Software Demonstration
        1. List of Datasets

3.  Week 3 (6/20 - 6/24): Using R/RMarkdown To Process Data
    1. Tasks
        1. Create and render rmarkdown
        1. Importing raw data into R
        1. Add placeholder chunks for all processing steps
    2. Deliverables
        1. Source code and rendered RMarkdown files importing all test datasets with all placeholder chunks
        1. Slide deck for detailing each processing step and planned tool.

1.  Week 4 (6/27 - 7/1): Documenting A Pipeline in Markdown / V&V in Python
    1. Tasks
        1. Begin GitHub Repository documenting all pipeline steps including input and output data and all options used (see https://github.com/nasa/GeneLab_Data_Processing/blob/master/RNAseq/GL-DPPD-7101-C.md for an example)
        1. Implement raw data V&V functions

    1.  Deliverables
        1. Start of Documentation Github Repository
        1. Fork and Pull Request raw data V&V functions to dp_tools repository
            - Doesn't need to be all raw data V&V but at least one fully implemented check function as follows:
                1. check function returns a FlagEntry style dict
                1. check function includes a unittest
                1. unittest test data included 

5.  Week 5 (7/4 - 7/8): QA for Raw Data
    1. Tasks
        1. Review Literature: QA for microarray raw data
            - Questions to consider:
                - What platform specific QA exists? e.g. known control probes
                - What plots exist for microarray QA and how are they interpretted?
        1. Implement raw data QA into the pipeline
            - Add as additional chunks on the rmarkdown that imports the raw data
        1. Implement V&V check functions for additional QA related data assets

    1.  Deliverables
        1. Questions about material reviewed
        1. Annotated Bibliography for reviewed articles about microarray QA
        1. Updated rmarkdown source and renders pushed to repo.
        1. Pull Request raw data QA V&V functions to dp_tools repository
            - Notice, you won't need to fork again, use the existing repo fork you created last week

6.  Week 6 (7/11 - 7/15): Generating Normalized Gene Expression
    1. Tasks
        1. Review Literature: Generating Normalized Gene Expression
            - Questions to consider:
                - What platform specific normalization methods exist?
                - How should duplicate probes be handled?
        1. Implement raw data to normalized gene expression into the pipeline
            - Add as additional chunks on the rmarkdown file or as a separate rmarkdown file
                - Note: a separate rmarkdown file will likely require usage of [rdata files](https://bookdown.org/ndphillips/YaRrr/rdata-files.html)
        1. Implement V&V check functions for normalized gene counts data assets

    1.  Deliverables
        1. Questions about material reviewed
        1. Annotated Bibliography for reviewed articles about Generating Normalized Gene Expression
        1. Updated rmarkdown source and renders pushed to repo.
        1. Pull Request normalized gene counts check functions to dp_tools repository


7.  Week 7 (7/18 - 7/22): QA Normalized Data / Differential Gene Expression
    1. Tasks
        1. Implement QA on normalized **probe** data into the pipeline
            - Note: QA for the normalized **probe** data, not gene counts. This will share commonalities with raw data QA so certain functions/approaches will likey be reused here.
        1. Implement Differential Gene Expression on Normalized Gene Counts
        1. Implement V&V check functions for QA on normalized probe data and differential gene expression output

    1.  Deliverables
        1. Updated rmarkdown source and renders pushed to repo.
        1. Pull Request new V&V check functions to dp_tools repository

8.  Week 8 (7/25 - 7/29): Adding Gene Annotations / Workflow Tooling
    1. Tasks
        1. Implement Gene Annotation of Differenential Gene Expression Tables
        1. Implement V&V check functions on Gene Annotation Added Gene Expression Tables
        1. Write bash script to run entire workflow
            - This means running your notebooks in sequence in one script
        1. Write sbatch script to run entire workflow
        1. Wrap entire workflow into one-process Nextflow

    1.  Deliverables
        1. Updated rmarkdown source and renders pushed to repo.
        1. Pull Request new V&V check functions to dp_tools repository
        1. Document Nextflow invocation and test data on Github
  
9.  Week 9 (8/1 - 8/5): Finalize Github / Preparing For Final Presentations
    1. Tasks
        1. Finalize slide deck for GeneLab presentation detailing project methods, results, and conclusions
        1. Finalize Github repository detailing the pipeline used including all analyses, input and output data, tools used, and all parameters used for each tool/rmarkdown document

    1.  Deliverables
        1. Final GeneLab project slide deck
        1. Final Github repository

10. Week 10 (8/8 - 8/12): Final Presentations / Writeups
    1. Tasks
        1. Give final GeneLab presentation (~25min + 5min Q&A)
        1. If time permits:
            - Add additional check functions for different stages of the workflow
            - Test additional GLDS datasets
            - Incorporate your check functions into an automated protocol (*I have a framework for this we may use; however, creating your own can be useful practice in writing larger software*)

    1.  Deliverables
        1. Final GeneLab Presentation
