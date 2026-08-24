# Freight Rate Prediction

This repository contains my solution for the Spotter freight-rate machine-learning assessment.

The labeled data was divided chronologically:

- Training data: January through August 2025
- Internal validation data: September and October 2025
- Final prediction data: November and December 2025

The preprocessing includes negative-weight repair, same-city coordinate repair, median imputation, one-hot encoding, calendar features and market-context features.

The final model combines a daily-context boosted-residual model, a histogram gradient-boosting model and a random-forest model.

After model selection, the final model is trained again using all 48,000 labeled rows before predicting the 12,000 final validation rows.

## Run instructions

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1PFYmouB2mzpTwdZfoQCp-v2NGkHZ6ADM#scrollTo=q5WQxpCIdIVR)

1. Click the Open in Colab button above.
2. Open the input_files folder in this GitHub repository.
3. Download these six files:

   - train-test.csv
   - validation.csv
   - validation-predictions-template.csv
   - december-chart-inputs.csv
   - requirements.txt
   - score.py

4. In Google Colab, click the folder icon on the left to open the Files section.
5. Upload all six files directly into the Files section. Upload the files themselves, not the input_files folder.
6. Select Runtime and then Run all.
7. Wait for preprocessing, model training, evaluation and prediction to finish.

The notebook displays the internal validation metrics and diagnostic plots.

When execution finishes, it automatically downloads:

- validation_predictions.csv
- december_outputs.zip

The december_outputs.zip file contains:

- december_predictions.csv
- candidate_december.png

The final validation_predictions.csv file contains the load_id and predicted_rate columns.

Alternatively, download the IPYNB file and run it locally using Jupyter Notebook, JupyterLab, VS Code, Anaconda or another application that supports IPYNB files, with the six required files placed in the same directory.

## Internal validation results

- September MAE: $79.411
- October MAE: $94.991
- Combined MAE: $87.351
- Combined MAE with both market signals hidden: $99.473
