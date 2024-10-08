# Titanic-Survival-Prediction

## **Problem Background** 

The main task of this project is to build a classifier to distinguish ADHD from healthy subjects using data collected by the 5L eye tracker. However, the dataset provided was recorded using the older Tobii – x230 eye tracker, which Braingaze previously utilized.

### *Differences between the Eye Trackers:*
 - Tobii x230: During data collection, subjects were required to remain still using a chinrest.
 - Tobii 5L: In contrast, subjects are allowed to move their heads freely, as the data is recorded without a chinrest.

The goal is to classify data recorded by the 5L eye tracker, for which we have the following datasets:
 - Eye and head movement logs from 5L for 30 subjects, saved as text files (one log file per subject).
 - Eye data for the same 30 subjects collected using the x230 eye tracker. This is intended to validate the classifier's performance.

This project will leverage both the eye movement logs and the head movement logs to ensure accurate ADHD classification.

## **Create a conda Environment** 
If you haven't installed Conda on your PC, please install it by following this [link](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html).

Once successfully installed, you can proceed to create a Conda environment to run the project.
Let's say name of the environment is 'synchronyClassifier'. 

``` 
conda create --name synchronyClassifier
```

Next, activate the conda environment by calling the below command. 

## **Clone the GitHub Repository**
Next clone the github repo by running the following command in your terminal after navigating into a preferred location. Or download the zip from github repo. 

``` 
git clone https://github.com/BGunofficial/ADHD
```

## **Install required libraries**
Make sure your Conda environment is activated. If not, activate it using the command mentioned earlier. Then, navigate to the project folder:

```
cd synchronyClassifier
```

Once you are in the correct directory and activate the conda environment run this command to install the required libraries

```
pip install -r requirements.txt
```

## **Running Inference on New Subjects**
The inference code allows you to test whether a subject has ADHD or is healthy based on a pre-trained model. The script provides the probability of the subject belonging to either class and saves the results in a CSV file.

#### Steps to Run Inference:
1. Create a CSV file containing the list of subjects you want to test. This file should have a single column:
   - Column Name: `sessionID`(the name of the log file for each subject)
     
   ```
     Example CSV file format:
   
     |   sessionID   |  
     | ------------- | 
     | subject1_log  | 
     | subject2_logl |
   ```
     
3. Setup the CSV file path where the `sessionID` information is stored:
   - Assign this path to the variable `csv_file` in the code

     Example:
     `csv_file = 'path/to/your/test_subjects.csv'`

4. Set the log files folder path where the logs of subjects are stored. These log files contain the data that will be used for inference.
   - Assign the path to the `logs_folder` variable.

     Example:
     `logs_folder = 'path/to/your/logs/folder'`

5. Model path and scaler path are already set up in the code:
   - The model path points to the pre-trained classifier.
   - The scaler path refers to the weights used for standard scaling.
     
   You do not need to modify these paths unless you're using different models or scalers.

5. Setup the output CSV file path where the tested results will be saved. This new CSV file will contain three columns:
   + `sessionID`   : The log file name of the subject.
 	 + `probability` : The probability that the subject belongs to the predicted class (ADHD or healthy).
   + `pred_class`  : The class predicted by the model (adhd or healthy).
     
   Assign the output path to the variable `output_csv`.
   
   Example:
   `output_csv = 'path/to/your/output/results.csv'`

6. After setting up the paths correctly, run the inference script by using the following command:

```
python inference.py
```

**If a subject has less than 30 trials after all preprocessing steps, they will not be included in the output CSV file**.


## **Generating Feature, Label, and ID Vectors**
You can generate .npy files for feature vectors (X), label vectors (Y), and patient ID vectors (id_pat) for training, validation, and testing datasets. This process involves several Python scripts that are set up for data processing, feature extraction, and training.

### *Steps to Generate .npy Files:*

1. Data Cleaning and Feature Extraction:
 - The file `BrainGaze_class.py` contains necessary functions to clean the log data and create a DataFrame.
 - The file `get_gaze_features.py` includes functions to calculate features from the cleaned DataFrame, specifically calculating synchrony (the cosine of the angle between left and right eye gaze vectors).

2. Preprocessing the Data:
 - Use the `pre_processing_synchrony.py` script to generate the `.npy` files for training, validation, and testing datasets.
 - The feature vector, label vector, and patient ID vector will be saved as `.npy` files in the `Using_synchrony` folder.
   
   **Running Preprocessing:**
   Run the following commands to generate `.npy` files for different datasets:
   
   ```
   # For Training Set:
   python pre_processing.py --set training
   ```

   This will generate the following files:
   - `X_training.npy` (Feature vector)
   - `Y_training.npy` (Label vector)
   - `id_pat_training.npy` (Patient ID vector)


   ```
   # For Validation Set:
   python pre_processing.py --set validation
   ```

   This will generate the following files:
   - `X_validation.npy` (Feature vector)
   - `Y_Validation.npy` (Label vector)
   - `id_pat_Validation.npy` (Patient ID vector)


   ```
   # For Testing Set:
   python pre_processing.py --set testing
   ```

   This will generate the following files:
   - `X_testing.npy` (Feature vector)
   - `Y_testing.npy` (Label vector)
   - `id_pat_testing.npy` (Patient ID vector)


## **Training and Testing the Model**

Once you have generated the `.npy` files, you can move on to training and testing the model.
The `data_utils.py` script includes functions to load the `.npy` files into the model. Each function has docstrings and comments explaining its purpose.
The `model_utils.py` file includes functions to:
 - Train the model.
 - Test the model on unseen data.
 - Calculate performance metrics.
 - Plot results.

The `main.py` file includes the best hyperparameters found during hyperparameter tuning. Run the following command to train the model:

```
python main.py
```

### **Outputs:**

Once you run the model, the following plots and metrics will be generated and saved in the `results` folder:

 - AUC Curve: Displays behavior of the model during training.
 - Probability Plot: Shows predicted probabilities for each subject, separated into ADHD and healthy classes.
 - ROC Curve: Receiver Operating Characteristic curve for both training and testing datasets.
 - Confusion Matrix: Displays model performance in terms of correctly and incorrectly classified subjects.
 - Precision-Recall Curve: Graph of precision vs recall.
 - Precision-Recall-Accuracy vs Threshold: Shows performance metrics at different classification thresholds.
 - 
Additionally, the results will be printed in the command line for both training and testing datasets.


   
   









