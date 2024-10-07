# Titanic-Survival-Prediction

## **1. Problem Background** 

The main task of this project is to build a classifier to distinguish ADHD from healthy subjects using data collected by the 5L eye tracker. However, the dataset provided was recorded using the older Tobii – x230 eye tracker, which Braingaze previously utilized.

### *Differences between the Eye Trackers:*
 - Tobii x230: During data collection, subjects were required to remain still using a chinrest.
 - Tobii 5L: In contrast, subjects are allowed to move their heads freely, as the data is recorded without a chinrest.

The goal is to classify data recorded by the 5L eye tracker, for which we have the following datasets:
1. Eye and head movement logs from 5L for 30 subjects, saved as text files (one log file per subject).
2. Eye data for the same 30 subjects collected using the x230 eye tracker. This is intended to validate the classifier's performance.

This project will leverage both the eye movement logs and the head movement logs to ensure accurate ADHD classification.

## **2. Create a conda Environment** 
If you haven't installed Conda on your PC, please install it by following this [link](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html).

Once successfully installed, you can proceed to create a Conda environment to run the project.
Let's say name of the environment is 'synchronyClassifier'. 

> conda create --name synchronyClassifier

Next, activate the conda environment by calling the below command. 

## **3. Clone the GitHub Repository**
Next clone the github repo by running the following command in your terminal after navigating into a preferred location. Or download the zip from github repo. 

> git clone https://github.com/BGunofficial/ADHD

## **4. Install required libraries**
Make sure your Conda environment is activated. If not, activate it using the command mentioned earlier. Then, navigate to the project folder:

> cd synchronyClassifier

Once you are in the correct directory and activate the conda environment run this command to install the required libraries

> pip install -r requirements.txt




> conda activate synchronyClassifier

