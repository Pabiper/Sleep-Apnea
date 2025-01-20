# Long-Range Interdependencies Aware Signal Analysis (LRIA)

This repository hosts the code for the paper manuscript "Long-Range Interdependencies Aware Signal Analysis for Rapid and Accurate Obstructive Sleep Apnea Prediction".

## Long-Range Interdependencies Aware Signal Analysis (LRIA)

The `LRIA` folder contains the code to extract and select the inner coupling information (coupling matrices) from the raw data.

The code package is written by Matlab.

## Model training and testing on SHHS dataset

From this Google drive link, you can see the sample data: https://drive.google.com/drive/folders/1-JiQKihFVLfssGcDizrpFCd1lpB_VfeD?usp=sharing

The `visit_1` folder contains the sample raw data from SHHS dataset visit_1. The patients' ID are: 77, 81, 82, 83, 84.

The `aout` folder contains the corresponding coupling matrices with the raw data using LRIA.

"shhs1_ahi_pruebas.xlsx" file contains the AHI level of total patients in SHHS dataset.

In this work, we used an environment of Python 3.11.3. "dataprocess.ipynb" contains the code to extract files from the folder and generate the inputs and labels.

We provide two models for comparison: naive transformer model in "train_transformer.ipynb" and proposed two-tower transformer in "train_twotower.ipynb". 

The code package is achieved in Python. Of note, each epoch needs 4-5 hours for the whole dataset in model training.

## Results

The `Figures` folder shows some result figures of our experiments. "plot.ipynb" is used to generate them.
