# Titanic-Survival-Prediction

## **1. Problem Background** 

The main task of this project is to build a classifier to distinguish ADHD from healthy subjects using data collected by the 5L eye tracker. However, the dataset provided was recorded using the older Tobii – x230 eye tracker, which Braingaze previously utilized.

### *Differences between the Eye Trackers:*
 - Tobii x230: During data collection, subjects were required to remain still using a chinrest.
 - Tobii 5L: In contrast, subjects are allowed to move their heads freely, as the data is recorded without a chinrest.

The goal is to classify data recorded by the 5L eye tracker, for which we have the following datasets:
 - Eye and head movement logs from 5L for 30 subjects, saved as text files (one log file per subject).
 - Eye data for the same 30 subjects collected using the x230 eye tracker. This is intended to validate the classifier's performance.

This project will leverage both the eye movement logs and the head movement logs to ensure accurate ADHD classification.

## **2. Create a conda Environment** 
If you haven't installed Conda on your PC, please install it by following this [link](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html).

Once successfully installed, you can proceed to create a Conda environment to run the project.
Let's say name of the environment is 'synchronyClassifier'. 

``` 
conda create --name synchronyClassifier
```

Next, activate the conda environment by calling the below command. 

## **3. Clone the GitHub Repository**
Next clone the github repo by running the following command in your terminal after navigating into a preferred location. Or download the zip from github repo. 

``` 
git clone https://github.com/BGunofficial/ADHD
```

## **4. Install required libraries**
Make sure your Conda environment is activated. If not, activate it using the command mentioned earlier. Then, navigate to the project folder:

```
cd synchronyClassifier
```

Once you are in the correct directory and activate the conda environment run this command to install the required libraries

```
pip install -r requirements.txt
```

## **5. Running Inference on New Subjects**
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
   - `sessionID`: The log file name of the subject.
 	 - `probability`: The probability that the subject belongs to the predicted class (ADHD or healthy).
   - `pred_class`: The class predicted by the model (adhd or healthy).
     
   Assign the output path to the variable `output_csv`.
   
   Example:
   `output_csv = 'path/to/your/output/results.csv'`

6. Special Note:
   
**If a subject has less than 30 trials after all preprocessing steps, they will not be included in the output CSV file**.

7. After setting up the paths correctly, run the inference script by using the following command:

```
python inference.py
```
   
