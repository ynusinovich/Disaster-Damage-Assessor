# Dude, Where's My House?
  Authors:
  1. Aman Hafez
  2. Kavan Pandya
  3. Yan Nusinovich

Readme drafted by Aman Hafez

## Contents:
- [Overview and Problem Statement](#Overview-and-Problem-Statement)
    1. [Overview](#Overview)
    2. [Problem Statement](#Problem-Statement)
- [Summary of Dataset](#Summary-of-Dataset)
    1. [Brief Description of Dataset](#Brief-Description-of-Dataset)
    2. [Brief Data Dictionary](#Brief-Data-Dictionary)
- [Data Cleaning and EDA Process](#Data-Cleaning-and-EDA-Process)
- [Model Evaluation](#Model-Evaluation)
- [Executive Summary](#Executive-Summary)
- [Next Steps](#Next-Steps)

---
## Overview and Problem Statement

### <u>Overview</u>

During a disaster, it is important to model and estimate the damage caused to residential properties.

To assure an accurate estimate of the damage, the user can upload an image of the affected structure, and then the program will retrieve an image of the structure from Google Street View. Based on the user's uploaded image, the model will classify the structure's condition into either good, damaged, or destroyed.

The program will use the location of the uploaded image, or an address input by the user, and will then estimate the monetary damage to the affected house using the prices published on the Zillow real-estate website.

The program provides value by allowing a user affected by a natural disaster to quickly see the original value and appearance of their property, and thus expedite insurance claims and repairs.

### <u>Problem Statement</u>

1. Based on an uploaded photo of the user’s house, and the location of the uploaded image, the program should find an image of the original condition of the structure.

2. Based on the uploaded photo of the user’s house, the program should assess the value of the affected structure and the damage to it.

---
## Summary of Dataset

### <u>Brief Description of Dataset</u>

Our dataset is based on image scraping from Google Images by searching for "good houses," "damaged houses," and "destroyed houses," and variations thereof combined with "fire," "floods," or "hurricanes." All search terms were scraped for approximately 200 images each by using the Google Chrome webdriver and downloading the image into the folder_path using the Selenium package in Python. In total, we used about 1,200 images.

### <u>Brief Data Dictionary</u>

1. Good Houses:<br>
    These houses showed no damage. Some were experiencing a natural disaster but left undamaged, and some were houses in good condition and not experiencing a natural disaster.
2. Damaged Houses:<br>
    These houses showed some damage, but they were not a total loss. The damage ranged from holes in the walls to a destroyed section of the house.
3. Destroyed Houses:<br>
    These houses were completely destroyed. They were either rubble laying on the ground, or collapsed walls and roof with just a skeleton of a home remaining.

---
## Data Cleaning and EDA Process

After the image scraping process, we removed identical images using Python code. We then visually sorted the remaining images into the categories listed in the data dictionary. We removed images that didn't show houses, images from a helicopter or a satellite, and images that didn't show a house in profile. We then ran a Python code to separate the house images into training and validation folders organized by categories.

---
## Model Evaluation

We chose an optimal convolutional neural network model based on validation accuracy, and we built in options to keep the weights from the best run of the model. We then evaluated the model on 39 test images of houses that the model had not seen before. The model had an accuracy of 58.97%, compared to a baseline accuracy of 38.46%. We then created a confusion matrix and a classification report to check whether the model misclassified good, damaged, or destroyed houses most often, but all of the misclassification were about equally common.

---
## Executive Summary

This tool would help someone affected by a natural disaster evaluate the damage to their house and get their insurance money. The user can upload a photo of their damaged house to instantly get a damage estimate and an original photo of their undamaged house. They can show the original photo, the new photo, and the estimate to their insurance company to file their claim. The program provides the flexibility to allow the user to input their address if their uploaded photo doesn't have location information, or to input their house condition if they don't have a photo of their damaged house.

---
## Next Steps

There are several possible next steps that would make this program more effective:
1. Creating a standalone web app or phone app, so people can access it right after a disaster.
2. Crowdsourcing house destruction data, to increase the number of images by one or two orders of magnitude and make the model generalize to new data better.
3. Adding more categories, such as "Partially Damaged," "Heavily Damaged," and "Water Damaged but Not Physically Damaged."
4. Expanding the code to include additional APIs for house valuation (https://www.cleveroad.com/blog/real-estate-apis).
5. Training the model on on images of other types of buildings, e.g., stores, schools, and places of worship.
6. Adding more images of houses with objects in front, so that the model is less likely to confuse objects for damage.
7. Adding images flipped left-to-right, to increase the size of the dataset.
8. Testing a model with more layers on a faster computer.
