# DL4H Paper Reproduction Project: An Extensive Data Processing Pipeline for MIMIC-IV

### Introduction:
In this project I aim to replicate the main experiment of the paper "An Extensive Data Processing Pipeline for MIMIC-IV". The original paper provides a configurable framework for data extraction, cleaning and pre-processing pipleine which is extendible, flexible, processes both ICU and non-ICU data thereby filling the gap of a standardized, flexible, customizable data pipeline to extract and pre-process the data available in MIMIC-IV dataset.

Original Paper:
>Mehak Gupta, Brennan Gallamoza, Nicolas Cutrona,Pranjal Dhakal, Raphael Poulain, and Rahmatollah Beheshti. 2022. An Extensive Data Processing
Pipeline for MIMIC-IV. In Proceedings of the 2nd Machine Learning for Health symposium, volume 193 of Proceedings of Machine Learning Research,
pages 311–325. PMLR https://proceedings.mlr.press/v193/gupta22a/gupta22a.pdf

Original Paper Repo:
>https://github.com/healthylaife/MIMIC-IV-Data-Pipeline

### Dependencies
Software: Python: 3.7 import_ipynb:0.1.3 ipywidgets:7.5.1 numpy:1.18.5 pandas:1.0.5 tqdm:4.47.0

### Data download instruction
The original paper uses MIMIC-IV dataset present at https://physionet.org/content/mimiciv/1.0/.This is a restricted-access resource. 
To access the files, I completed the the below requirements:
- Became a credentialed user by filling up the application for Credentiated Access using illinois email id and getting the request approved
- Completed required training:CITI Data or Specimens Only Research and submitting the result at \url{https://physionet.org/settings/training}
- Signed the data use agreement for the project
- After receiving the access to data, the files can be downloaded from the terminal using below cmd:
wget -r -N -c -np --user nitaa2 --ask-password https://physionet.org/files/mimiciv/1.0/

### Data Extraction and Processing 
To run data extraction and pre-processing from scratch the steps are as follows:
- Clone the repository
- Launch jupyter notebook from the root directory of the cloned repo: `jupyter notebook .`
- Open the jupyter notebook `projectPipeline.ipynb`
- In the Preliminary Step cell
  1. Set the cpath to the local path of the code and MIMIC-IV dataset
  2. If the code resides on the google drive, ensure that the mounting of the code is completed
  3. The software dependencies are installed
- In Step 0 select if you want to Create a new cohort or Reuse existing cohort for feature extraction and other data pre-processing activities
- Based on the option selected in Step 0, please follow the instructions given before each code block.
- Based on the user inputs the data will be extracted and pre-processed from MIMIC-IV dataset
- Output data will be saved to 'data' folder in the local path (or google drive based on the local setup)

### Training, evaluation & pretraining code: 
Not-applicable for this project as it involves Data Extraction and Processing pipeline 

### Bonus Initiatives:
- Pyhealth Contribution: I was able to successfully contribute by adding hcpcsevents table in MIMIC4 dataset. Approved PR link https://github.com/sunlabuiuc/PyHealth/pull/134 . File modified **mimic4.py**, function added **parse_hcpcsevents()**
- Notebook: projectPipeline.ipynb

### Original Pipeline Enhancement
- I have successfully added feature for extraction logic for hcpcs events.The data records from MIMIC-IV (https://physionet.org/content/mimiciv/1.0/hosp/hcpcsevents.csv.gz) are extracted and merged with the cohort based on user selection inputs.
File modified: **preprocessing/hosp_module_preproc/feature_selection_hosp.py** ,Function added  **feature_hcpcs()** on line 31 
- I have added the code in projectPipeline.ipynb (between step 4 & 5) to take any disease as input from the user for refining the cohort selection
- Ablation code added as Step 0 in projectPipeline.ipynb. It takes the user inputs for the existing cohort to be reused. User can then directly go to step 5 by skipping the interim steps.

### Table of results
Reproduced the below claims by the original paper
- Pipleline can extract cohort features from MIMIC-IV based on user input of feature and on specific condition of the disease chosen by the user.
- Pipleline can extract cohort for prediction task of mortality in ICU patients.
- Pipleline can pre-process cohort from MIMIC-IV dataset for clinical grouping  and conversion based on user input along with providing summary of the resultant cohort.
- Pipleline can pre-process cohort for outlier removal,imputation,and selection of feature based on user inputs.
- Pipleline can pre-process cohort by binning the sequential data into time intervals based on the timeseries length according to user inputs
![image](https://user-images.githubusercontent.com/109548683/233741340-59f14053-67c4-4d48-a781-deca5cc9d1b7.png)
