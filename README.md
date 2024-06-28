# Neural Networks Data Analysis Project

Team Name: Baseball Savants

Team Members: Doruk Ozar, Connor Vucovich, and Taylor Lamantia

This project utilizes existing pitch data from the MLB (2023), Major League Baseball, to determine which pitch will be most effective in a given situation for a particular pitcher. The project creates 2 types of machine learning models (neural network and decision tree) to classify the result of of pitch based on various predictor variarbles. 


The dataset can be found at: https://baseballsavant.mlb.com/statcast_search

# DataPrep_EDA.ipynb
This file discusses the problem being worked on, describes the data involved in the problem, and handles the preprocessing/data exploration (EDA). The metrics determined most valuable to use to predict are:
The metrics used to predict are:
* pitch type
* handedness of the pitcher
* velocity of the pitch toward home
* extension the pitcher gets off of the mound toward home upon release
* amount of spin on the ball as it is released by the pitcher
* direction of the spin on the ball as it leaves the pitchers hand
* horizontal movement on the ball as it approaches the batter in feet
* vertical movement on the ball as it approaches the batter in feet
* effective speed which takes the extension the pitcher into account and adjusts the perceived velocity that the batter would see based on this distance reduction

The result of the pitch is binned into 4 classes from 24 original classes in the data:
* ball
* strike
* hit
* field out

Strike is the most frequently occurring result, then ball, and field_out and hit occur significantly less frequently.

The analysis done here shows:

Strike is highly correlated with fastball and correlated with cutter, slider, and sinker. There is a moderate correlate with strike and changup, curveball, and sweeper. 

Ball is also correlated with fastball,  correlated with sinker, and has moderate correlations with slider, changeup, curveball, cutter, and sweeper.

There are no strong correlations between field_out and hit with any of the pitches.


# Modeling.ipynb
This notebook explores the development of predictive models. In this case, a neural network and decision tree (both with cross validation and grid search for parameter optimization) are trained and tested. The neural network performs better with an 86.22% accuracy.

The model performs well overall with high precision and recall for "ball," "field_out," and "strike" classes (precision all >0.84 and recall >0.82). However, it struggles with the "hit" class, showing lower precision (0.67), recall (0.49), and F1-score (0.57), indicating that it has difficulty correctly identifying hits. This indicates that the model may be falsely predicting hits as other results, which is important to consider when using the results to determine the best pitch.

The model rarely mispredicts field out but sometimes mispredicts strike as a ball and ball as a strike.

# Final_Report.ipynb
This notebook includes the final most important results received from the data. It includes the most important results from the initial EDA, the neural network training, and the performance results of the model. The model is then used to predict the results for each pitch type that a particular pitcher uses. We can use these results to determine which pitch is best suitable for a pitcher to achieve desired results.
