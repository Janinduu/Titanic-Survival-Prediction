# Titanic-Survival-Prediction
# **1. Problem Background** 

## The main task of this project is to build a classifier to distinguish ADHD from healthy subjects using data collected by the 5L eye tracker. However, the dataset provided was recorded using the older Tobii – x230 eye tracker, which Braingaze previously utilized.

# Differences between the Eye Trackers:
## Tobii x230: During data collection, subjects were required to remain still using a chinrest.
## Tobii 5L: In contrast, subjects are allowed to move their heads freely, as the data is recorded without a chinrest.
### The goal is to classify data recorded by the 5L eye tracker, for which we have the following datasets:

## 1. Eye and head movement logs from 5L for 30 subjects, saved as text files (one log file per subject).
## 2. Eye data for the same 30 subjects collected using the x230 eye tracker. This is intended to validate the classifier's performance.
## This project will leverage both the eye movement logs and the head movement logs to ensure accurate ADHD classification.
