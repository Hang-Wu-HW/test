## Overview

This repository contains replication files for Cao, Lu and Wu (2020), "Synthetic Control Inference for Staggered Adoption: Estimating the Dynamic Effects of Board Gender Diversity Policies."

There are two main parts to the replication

1.  Data cleaning
2.  Replication of tables and figures, including Table 1, Table 3 and all the figures in the main text and appendix.

## Date availability

All data sources are publicly available. See below for the details.

1.  Data on trade of intermediates and machinery from COMTRADE \[appears in comtrade_1990_2015, comtrade_1996_2015, comtrade_robots_1996_2015\] These data can be downloaded from <https://comtrade.un.org/>

## Folder content

This replication package is organized according to the following structure:

```         
.
├── README.md                           The file you are reading right now.
└── replication_files/
    ├── data cleaning/                  
    │   ├── EIGE board gender data/    Raw and cleaned gender quota data.
    │   ├── LFS full time employment data/ Labor Force Survey full-time data.
    │   └── LFS work hours data/       LFS working hours data.
    ├── Figure 1/                       scripts and datasets uesed to create Figure 1
    │   ├── data_boardgendereige.csv    Input data for Figure 1.
    │   ├── event_time_att.m            MATLAB script for event-time ATT estimation with our method
    │   ├── functions/                  Core MATLAB functions for our synthetic control method (SSC).
    │   │   ├── synthetic_control.m         Classic synthetic control weights algorithms for one treated unit.
    │   │   ├── synthetic_control_batch.m   Our synthetic control weights algorithms for multiple treated unit.
    │   │   ├── ssc.m                       Estimation
    │   │   ├── ssc_inference.m             Inference
    │   │   ├── att_event_ci.m              ATT confidence intervals.
    │   │   ├── vline.m, vline_license.txt  Plot helper and license.
    │   ├── graph1a.png, graph1b.png   Output plots for Figure 1.
    ├── Figure 2–6/                     Same structure as Figure 1, using different datasets and scripts.
    ├── Figure A1/                       scripts and datasets uesed to create Figure A.1
    │   ├── jasa graphA1.do             Stata script for Figure A1.
    │   ├── jasa_boardgendereige.dta    Input stata data file.
    │   └── figureA1.png                 Output plot for Figure A1.
    ├── Figure A2/                       scripts and datasets uesed to create Figure A.2
    │   ├── FigureA2.png                 Output plot for Figure A.2.
    │   ├── results_staggered_did.R, results_staggered_did.csv R code and results for ATT estimation with staggered DID
    │   ├── results_staggered_synthetic_control.m MATLAB script for ATT estimation with our method
    │   ├── data_boardgendereige.csv     Input dataset.
    │   └── functions/                   Core MATLAB functions for our method (same as in ./replication_files/Figure 1/functions).
    ├── Table 1/                         
    │   ├── jasa table1.do, jasa_*.dta  Stata scripts and data for Table 1.
    │   ├── *.tex, *.txt                 Exported LaTeX and text tables.
    └── Table 3/                         
        ├── data_boardgendereige.csv, table3.csv Input and output data.
        └── event_time_att.m + functions/       MATLAB scripts for estimation.

```

## Replication instructions

To replicate the cleaned data , one has to navigate to the corresponding folder and run the appropriate cleaning files by Stata 14.2

Tables and figures can be immediately replicated by navigating to the corresponding folder and running the relevant code as below:

| Figure/Table # | Software                  | Relevant code                                                     |
|----------------|---------------------------|-------------------------------------------------------------------|
| Figure 1       | MATLAB R2018b             | replication_files/Figure 1/event_time_att.m                     |
| Figure 2       | MATLAB R2018b             | replication_files/Figure 2/event_time_att_comparison.m          |
| Figure 3       | MATLAB R2018b             | replication_files/Figure 3/event_time_att_comparison_other.m    |
| Figure 4       | MATLAB R2018b             | replication_files/Figure 4/event_time_att_comparison_other.m    |
| Figure 5       | MATLAB R2018b             | replication_files/Figure 5/event_time_att_comparison_other.m    |
| Figure 6       | MATLAB R2018b             | replication_files/Figure 6/event_time_att_comparison_other.m    |
| Figure A.1     | Stata 14.2                | replication_files/Figure A1/jasa graphA1.do                     |
| Figure A.2[^*] | R 4.5.1 and MATLAB R2018b | replication_files/Figure A2/results_staggered_did.R <br> replication_files/Figure A2/results_staggered_synthetic_control.m |
| Table 1        | Stata 14.2                | replication_files/Table 1/jasa table1.do                        |
| Table 3        | MATLAB R2018b             | replication_files/Table 3/event_time_att.m                      |


[^*]: To replicate Figure A.2, first run the R code *results_staggered_did.R* to produce results using the staggered DID method. Then, run the Matlab code *results_staggered_synthetic_control.m* to produce results using our method and perform the comparison.
