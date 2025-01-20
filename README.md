# **Long-Range Interdependencies Aware Signal Analysis (LRIA)**

This repository hosts the code for the paper manuscript "Long-Range Interdependencies Aware Signal Analysis for Rapid and Accurate Obstructive Sleep Apnea Prediction".

## Dataset and Sample data

You can access sample data via this Google Drive link: https://drive.google.com/drive/folders/1-JiQKihFVLfssGcDizrpFCd1lpB_VfeD?usp=sharing

`visit_1/` contains sample raw data from the SHHS dataset visit 1, including the following patient IDs: 77, 81, 82, 83, 84.

`aout/` contains the corresponding coupling matrices generated using LRIA from the raw data.

`shhs1_ahi_pruebas.xlsx` provides the AHI levels for all patients in the SHHS dataset.

## Code Details

`LRIA/` contains the MATLAB code to extract and select the inner coupling information (generate coupling matrices) from raw data.

### Data Processing and Model training on SHHS dataset

Environment: Python 3.11.3. 

`dataprocess.ipynb` processes raw files to generate input features and labels. 

`train_transformer.ipynb` implements the naive transformer model

`train_twotower.ipynb` implements the proposed two-tower transformer model.

Training the full SHHS dataset takes approximately **4-5 hours per epoch** for both models.

## Results and Visualizations

`Figures/` folder contains result figures from the experiments.  

Use `plot.ipynb` to reproduce the visualizations.  
