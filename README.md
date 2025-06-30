# pull-test-analysis
This repository is a workflow using Rmarkdown to perform feature analysis on the pull test as published in the IEEE Transactions on Neural Systems and Rehabilitation Engineering, Volume 3-2025, article "Detecting Postural Instability in Parkinson’s Disease From IMU-Based Objective Measures". [link here](https://ieeexplore.ieee.org/document/11015623) 

The raw data cannot be released due to constraints with the ethical committee; however, a sample data file showing the structure of the data has been provided, and the full feature data has also been provided.

The file groups in this repository are:

### <u>Model evaluation files</u>

- `model-evaluation.Rmd`: The notebook containing the pipelines for all feature and model performance evaluation. The core notebook for this repository.
- `features.csv`: Generated from the `feature-production.Rmd`, the feature file contains the features needed for model evaluation.
- `p_values.csv`: Generated from the `feature-production.Rmd`, the feature Mann-Whitney U test p-values are needed throughout the model evaluation process.
- `feature_outliers.csv`: Generated from the `feature-production.Rmd`, this includes the subject outlier counts per feature needed for outlier evaluation.
- `subjects.csv`: Amended from original subject data to exclude sensitive information, includes columns needed for the model evaluation.

### <u>Feature production files</u>

- `feature-production.Rmd`: The integral feature production and analysis pipeline for this repository. Needed only if features in the `features.csv` need to be re-produced for any reason.
- `subjects.csv`: (same file as above) Amended from original subject data to exclude sensitive information, includes columns needed for the model evaluation.
- `axis_points.csv`: The primary segment indices for beginning the data extraction for the pull test - automatically utilised by the pipeline.
- `segments_manual.csv`: The segmentation indices for portioning each of the three pulls into one timeseries - automatically utilised by the pipeline.
- `sample_lumbar_capp.csv`: This file shows the file layout of the raw data, it is not real data. The columns are VT, ML, AP, Yaw, Pitch, Roll, MagX, MagY, MagZ, temperature. Units m/s^2, rad/s, µT, and degrees C.


## How to Run

Follow these steps to run the project:

1. **Initial setup**
   - Ensure R and RStudio are installed on your system.
   - Install necessary R packages. This step is automatically included in the Rmd notebook files.
   - Create a new project in RStudio and store all Rmd notebooks and csv files in this location (alternatively store files where desired and update the respective R code chunks to point to the correct directory).
   - For any R troubleshooting issues, see last section of this README for full version information. If issues arise, exact versions can resolve these issues.

2. **Download the repository**
   - Clone the repository to your local machine or download it as a ZIP file and extract it to the desired directory.

3. **Data preparation**
   - Place your raw data files in the correct directory

4. **Open notebooks**
   - Open the notebooks (for best results, ensure a new project file is created and opened in RStudio before opening the notebook .Rmd files)

6. **Run model evaluation**
   - Open `model-evaluation.Rmd` in RStudio.
   - Run the RMarkdown file to perform the analysis. This can be done by clicking the "Knit" button in RStudio or simply running the chunks without Knitting.
   - Evaluate results.

7. **Produce features**
   - Open `feature-production.Rmd` in RStudio.
   - Run the RMarkdown file to perform the analysis. This can be done by clicking the "Knit" button in RStudio or simply running the chunks without Knitting.
   - This is only required to generate the appropriate files for `model-evaluation.Rmd`, for example changing H&Y Classes or amending/changing features.
   - To produce features the raw csv files are needed (approx 6 GB of data) and stored at "E:/PD_csvs". To change this, CTRL+F in the notebook and change all the directory to desired directory
  

---

### Version info

RStudio 2023.09.1+494 "Desert Sunflower" 
Release (cd7011dce393115d3a7c3db799dda4b1c7e88711, 2023-10-16) for windows
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) RStudio/2023.09.1+494 Chrome/116.0.5845.190 Electron/26.2.4 Safari/537.36

#### R version:
                                               
platform       x86\_64-w64-mingw32        
arch           x86\_64                           
os             mingw32                  
crt            ucrt             
system         x86\_64, mingw32           
status                                       
major          4                           
minor          3.2                            
year           2023                          
month          10                           
day            31                              
svn rev        85441                           
language       R                              
version.string R version 4.3.2 (2023-10-31 ucrt)
nickname       Eye Holes \cite{baseR} 

#### R Library versions:

base, version: 4.3.2  
tidyverse, version: 2.0.0   
signal, version: 1.8.0  
pracma, version: 2.4.4  
mgcv, version: 1.9.0  
entropy, version: 1.3.1  
Hmisc, version: 5.1.1  
zoo, version: 1.8.12   
EMD, version: 1.5.9    
corrplot, version: 0.92   
pROC, version: 1.18.5   
tidymodels, version: 1.1.1     
rstatix, version: 0.7.2     
