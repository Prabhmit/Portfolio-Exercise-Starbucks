# Portfolio Excercise: Starbucks

# Table of Contents

1. Installations and package requirement
2. Project Motivation
3. Project Components and File Descriptions
4. Instructions
5. Licensing, Authors and Acknowledgments

# Installations and package requirement

The code is in Python 3.7.6. The Starbucks.ipynb is a Jupyter notebook. The Python libraries applied are numpy, pandas, scipy, matplotlib, seaborn and sklearn. 

# Project Motivation

The dataset was originally used as a take-home assignment provided by Starbucks for their job candidates. The data for this exercise consists of about 120,000 data points split in a 2:1 ratio among training and test files. In the experiment simulated by the data, an advertising promotion was tested to see if it would bring more customers to purchase a specific product priced at $10. Since it costs the company $0.15 to send out each promotion, it would be best to limit that promotion only to those that are most receptive to the promotion. Each data point includes one column indicating whether or not an individual was sent a promotion for the product, and one column indicating whether or not that individual eventually purchased that product. Each individual also has seven additional features associated with them, which are provided abstractly as V1-V7.

## Optimization Strategy

The goal is to use the training data to understand patterns in V1-V7 that indicate that a promotion should be provided to a user. Specifically, the goal is to maximize the following metrics:

### Incremental Response Rate (IRR)

IRR depicts how many more customers purchased the product with the promotion, as compared to if they didn't receive the promotion. Mathematically, it's the ratio of the number of purchasers in the promotion group to the total number of customers in the purchasers group (treatment) minus the ratio of the number of purchasers in the non-promotional group to the total number of customers in the non-promotional group (control).

$$ IRR = \frac{purch_{treat}}{cust_{treat}} - \frac{purch_{ctrl}}{cust_{ctrl}} $$

### Net Incremental Revenue (NIR)

NIR depicts how much is made (or lost) by sending out the promotion. Mathematically, this is 10 times the total number of purchasers that received the promotion minus 0.15 times the number of promotions sent out, minus 10 times the number of purchasers who were not given the promotion.

$$ NIR = (10\cdot purch_{treat} - 0.15 \cdot cust_{treat}) - 10 \cdot purch_{ctrl}$$

# Project Components and File Descriptions

The datasets are training.csv and Test.csv. The Starbucks.ipynb is a Jupyter notebook which included the relevant Python code for this excercise. test_results.py is a script that uses the Test.csv to test the model output. 

The project has four components: 

## Inspecting promotion distribution and calculating IRR and NIR

In this component group counts of the train data were calculated and the distribution of customers who were sent the promotion was inspected. IRR and NIR values of the train data were calculated. 

## Hypothesis testing for IRR 

In this component hypothesis testing using simulation approach for IRR was conducted. As there are two measures (IRR and NIR), the level of significane (5%) was 0.05/2 = 0.025 for both tests under Bonferroni Correction. The p-value for the test on IRR is 0.0. Therefore there is sufficient evidence to prove with 97.5% confidence that IRR is different from 0.

## Hypothesis testing for NIR 

In this component hypothesis testing using simulation approach for NIR was conducted. The p-value for the test on NIR is 0.0. Therefore there is sufficient evidence to prove with 97.5% confidence that NIR is different from 0. 

## Building promotion strategy model 

X(V1-V7) and y('purchase) variables were created and the training data was split into test and train sets with a 2:1 ratio. A pipeline was build using Random Forest and hyper-parameters were tuned using GridSearch. The model was fit to train data following which predictions were made using test data and the model output was evaluated and reported.
The model output was tested with Test.csv using test_results.py. 

# 4. Instructions

1. Run the cells in the Starbucks.ipynb notebook.

# 5. Licensing, Authors and Acknowledgments

Introduction to Data Science, Data Scientist Nanodegree Program, Udacity, https://www.udacity.com/course/data-scientist-nanodegree--nd025

Portfolio Exercise: Starbucks, Udacity, https://www.udacity.com/course/data-scientist-nanodegree--nd025

scikit-learn - sk.learn.ensemble.RandomForestClassifier, https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html
