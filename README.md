# Deep Learning Image Classification Model for Pneumonia Cases


Despite the availability of safe and effective antibiotics and vaccines for treatment and prevention, pneumonia is a leading cause of death worldwide and the leading infectious disease killer. This disease has a particularly high mortality rate especially amongst children of age 5 and younger. 

Most of the times it is crucial to effectively identify the first sympotms of pneumonia as early as possible in order to prevent the disease to worsen and eventually become reason for hospitalisation and even death. Deep learning algorithms and their computational power can be of help for medical staff when it comes to the interpretability and detection of possible signs of pneumonia in x-rays.

In this project, we have built a convolutional network trained on a dataset of 5,852 x-rays images collected by a number of hospitals in the region of Guangzhou. Although the dataset was relatively small and the CNN final structure used quite simple, the final model performance is very effective in identifying people affected by pneumonia with an overall accuracy and roc score respecively of 71% and 88%. 


# Project Structure

1. [ File Description ](#file_descriptions)
2. [ Technologies Used ](#technologies_used)
3. [ Executive Summary ](#executive_summary)
    * [ Dataset Information ](#dataset_info)
    * [ Image pre-processing ](#data_cleaning)
    * [ Modelling ](#modelling)
    * [ Costs Evaluation and Performance ](#insights)
  


<a name="file_descriptions"></a>
## File Descriptions

File Descriptions
- ipynb_checkpoints: different notebooks version going from preprocessing to modelling
- eda_index_final.ipynb: notebook where the models were made, tuned and evaluated
- data instructions: contains directions to download the dataset of images used for this project
- references: links to the source material referenced in the notebook
- images: jpg images taken from the jupyter notebook
- pneumoniadeep_presentation: pdf format of a presentation with key insights for non-tecnhical stakeholders


<a name="#technologies_used"></a>

## Technologies Used
- Python
- Pandas
- Numpy
- Keras
- Matplotlib


<a name="##executive_summary"></a>

## Executive Summary

The main goal of this project was to create a deep learning algorithm with convolutional neural networks and tuning of its features. Given the binary nature of this issue and also presence of class imbalance in our dataset, we have chosen roc score as the main metric to measure success. Our winning model is capable of correctly identifying 7 over 10 people affected by pneumonia.


# Dataset information 
