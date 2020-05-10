# Deep Learning Image Classification Model for Pneumonia Cases

<p align="center">
  <img src="https://github.com/matteomm/imageclassification_pneumonia_deeplearning/tree/master/images/cover.png" width=550>
</p>

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

<a name="#dataset_info"></a>
###  Dataset information 

The original dataset can be found at this link [here](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia) from Kaggle. Initially the dataset was divided into three sub-folders, respectively for training, validation and test. Each of these folders contain example of both healthy and unhealthy patients affected by pneumonia. All images were in different size but the average was in the region of 1100x1100.

<a name="#data_cleaning"></a>
###  Image pre-processing

Images were first converted to grayscale since having RGB layers for x-rays did not make any difference. Also, we performed two separate line of testing with progressive resizing. The first with all images sized to 200x200 and then a second one with double the pixels (500x500). This was done in order to see whether excessive shrinking of the images would compromise overall performance.

<a name="#modelling"></a>

###  Modelling

As baseline we introduced a simple Dense neural network on which we applied some minor changes in order to improve initial performance. Some of the tweaks included, changing the optimiser from stochastic gradient descent to adam, increasing the number of nodes, increasing the number of layers. Best performance for node was stationary at around 70% accuracy, probably due to the Dense network stumbling upon a local minima. 

The second half of the modelling focused on producing several iterations of Convolutional Neural Networks, well more suited for image classification problems as opposed to their simple Dense counterpart. As mentioned earlier, the CNN section has two sub-sections in which we perform optimisations on different image sizes and also by shuffling the number of images across the training and validation datasets. 

We tried different combinations but the best performing NN seemed to be the one with 2 convolutional layers with 40/20 nodes respectively and 2 max pool layers with a final Dense with sigmoid activation function due to the binare nature of the problem. For simplicity sake, we kept the activation function for the convolutional layers as only the 'relu' type without playing around with other different types.

The winning model had an overall accuracy of 71% and roc_score of 88% across the 600 test set. Attaching below a graph of our roc_cruve for training and test set:

<p align="center">
  <img src="https://github.com/matteomm/imageclassification_pneumonia_deeplearning/tree/master/images/roc_curve_final.png" width=550>
</p>


<a name="#insights"></a>
###  Costs Evaluation and Performance

In the final section, we concentrated on evaluating possibles costs associated to our model off some expenses report related to US pneumonia cases. One of the undelrying assumptions here is that the Chinese market faces similar costs to the US one in terms of pneumonia related cases. Off ours stats (references available in the folder 'references') we have estimated that false negatives, resulting in hospitalization would be quantified in the region of $ 10,800 per patient. Apart from True Negatives incurring in $0 cost, the remaining cases were assessed to be in the region of $480 covering teh costs of medical supplies. Our threshold selection was thrown off by a significanty small prevalence since there are roughly 2 millions and a half pneumonia cases in China over the total population. We arbitrarily set the threshold at around .35 in order to minimise the instance of false negatives, being the costliest of outcomes and also potentially incurring in death.

Below there's an image of our final confusion matrix on the test set:

<p align="center">
  <img src="https://github.com/matteomm/imageclassification_pneumonia_deeplearning/tree/master/images/confusion.png" width=550>
</p>


The model has a relatively high accuracy and roc_score. However, precision took the hit in this scenario since we are proritising the least amount possible of false negatives. A better precision rate could be achieved by playing around our final threshold selection in order to strike a more reasonable balance between type I and type II errors.

