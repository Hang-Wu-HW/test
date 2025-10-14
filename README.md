<div align="center">
# README
</div>
## Overview

This repository contains replication files for Cao, Lu and Wu (2020), "Synthetic Control Inference for Staggered Adoption".

There are two main parts to the replication:

1.  Data cleaning
2.  Replication of all the table and figures in the main text.

## Data availability

All data sources are publicly available. Data used are listed below:

1.  Data on corporate board’s female representation across EU countries from European Institute for Gender Equality: this data is stored in *wmidm_bus_bus\_\_wmid_comp_compbm.xlsx* and can be downloaded from <https://eige.europa.eu/gender-statistics/dgs/indicator/eustrat_ges_lead_bus__wmid_comp__ind53_top/datatable>.
2.  Labor outcome variables across EU countries from the EU Labor Force Survey (“LFS”): (1) full-time employment data is stored in \*lfsq_epgais.xlsx\* and can be downloaded from <https://ec.europa.eu/eurostat/databrowser/view/LFSQ_EPGAIS__custom_6036320/default/table>. (2) working hours data is stored in *lfsq_ewhuis.xlsx* and can be downloaded from <https://ec.europa.eu/eurostat/databrowser/view/lfsq_ewhuis/default/table>.
3.  Announcement dates of the board gender policies: this data is stored \*policy.dta\* and is hand-collected from each EU country’s official website, with additional guidance from Seierstad et al. (2017).

## Folder content

This replication package is organized according to the following structure:

```         
.
├── README.md                               
└── replication_files/
    |── data cleaning/
    |   |── EIGE board gender data/                
    |   |   |── policy.dta                  Raw dataset of policy announcement data
    |   |   |── wmidm_bus_bus__wmid_comp_compbm.xlsx  Raw datasets for corporate board’s female ratio
    |   |   |── jasa board gender clean.do  Stata script for cleaning board’s female ratio
    |   |   |── jasa_boardgendereige.dta    Cleaned Stata dataset.
    |   |   └── data_boardgendereige.csv    Cleaned stata dataset stored as csv file
    |   |── LFS full time employment data/
    |   |   |── policy.dta                  Raw dataset of policy announcement data
    |   |   |── lfsq_epgais.xlsx            Raw dataset of full-time employment
    |   |   |── jasa ft employment clean.do  Stata script for cleaning full-time employment data.
    |   |   |── jasa_ft.dta                 Cleaned Stata dataset.
    |   |   └── data_ft.csv                 Cleaned dataset stored as csv file.
    |   └── LFS work hours data/
    |       |── policy.dta                  Raw dataset of policy announcement data
    |       |── lfsq_ewhuis.xlsx            Raw dataset of working hours
    |       |── jasa work hours clean.do    Stata script for cleaning working hours data.
    |       |── jasa_hr.dta                 Cleaned Stata dataset.
    |       └── data_hr.csv                 Cleaned dataset stored as csv file
    ├── Figure 1/                           
    │   ├── data_boardgendereige.csv        Board gender ratio as input data for Figure 1.
    │   ├── event_time_att_comparison.m                MATLAB script for policy comparison with our method (Figure 1)
    │   ├── functions/                      Core MATLAB functions for our synthetic control method (SSC).
    │   │   ├── synthetic_control.m         Classic synthetic control weights algorithms for one treated unit.
    │   │   ├── synthetic_control_batch.m   Our synthetic control weights algorithms for multiple treated unit.
    │   │   ├── ssc.m                       Estimation
    │   │   ├── ssc_inference.m             Inference
    │   │   ├── att_event_ci.m              ATT confidence intervals.
    │   │   └── vline.m, vline_license.txt, legendflex-pkg/  Plot helper and license.
    │   └── graph1.png        Output plot for Figure 1.
    ├── Figure 2/                         Same structure as Figure 1, using different datasets and scripts.
    └── Table 1/                         
        ├── data_boardgendereige.csv        Board gender ratio as input data
        ├── event_time_att.m                MATLAB scripts for estimation of synthetic control weights (Table 1)
        ├── functions/                      Core MATLAB functions for our method (same as./replication_files/Figure 1/functions).
        └── table1.csv                      Output data for Table 1
```

## Software requirements

The codes for data cleaning are run in Stata 14.2.

The codes for the table and figures are run in MATLAB R2018b with the Optimization Toolbox.

## Replication instructions

To replicate the data cleaning, one can navigate to the *replication_files/data cleaning/* folder and run the appropriate cleaning files (see above).

To replicate the Table and Figures, one can navigate to the corresponding folder in *replication_files/* and run the relevant codes as shown below:

| Figure/Table \# | Relevant code                       |
|-----------------|-------------------------------------|
| Figure 1 | Figure 1/event_time_att_comparison.m       |
| Figure 2 | Figure 2/event_time_att_comparison_other.m |
| Table 3  | Table 3/event_time_att.m                   |

[^1]: To replicate Figure A.2, first run the R code *results_staggered_did.R* to produce results using the staggered DID method. Then, run the Matlab code *results_staggered_synthetic_control.m* to produce results using our method and perform the comparison.

## Data Reference

Seierstad, Cathrine, Patricia Gabaldón, and Heike Mensi-Klarbach. 2017. Gender diversity in the boardroom. Volume 1, The use of different quota regulations. Palgrave Macmillan.