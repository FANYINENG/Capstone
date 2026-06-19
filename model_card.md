# Model Card: Sequential Black Box Optimization Strategy

## Overview
* Approach: Bayesian Optimisation 
* Type: Sequential Search
* Version: 1

## Intended Use
The models contained in each function file are suited for black box function problems, i.e. there's a dataset with n number of features and an output, but you have no information about the underlying function. 

The models contained in this repo are applied on very small datasets, the setup of the problem provides between 10 and 40 dapoints in total. The project allows every week to submit a query which will return one extra data point every round. The models here are not suitable for models and projects that require a lot of training data e.g. a neural network. 

## Details
Phase 1: Setting up a basic search function that used surrogate model that was tuned for exploration. I specifically implemented a beta sweep across a range of values for beta (higher = exploration and lower = exploitation) and from that output selected the points to query. 

Phase 2: Changed to exploitaion strategy, in the first rounds there was a mix of success. Some functions showed outputs which improved the initial dataset (the objective is to maximize the output in all functions). During this phase most functions saw a significant improvement in the end goal. 

Phase 3: Tuned hyperparameters and applied new techniques such as dimension freezing. Towards the end of phase 2 I observed the outputs starting to plateau across some functions, I implemented new techniques specially for the higher dimension functions where there's more data. I applied data masking, so the model would only fit for the higher performing dataset, similar to zone in on a particular part of the search space to apply the optimisation. 

## Performance Summary
The evaluation applied on the models was purely based on beating the best point of the dataset. The models are not evaluated based on fit or error using for example a cross validation method, because the models were not designed in their inception to capture the underlying function, but rather output the best query possible. 

| Function | Dimensions | Best Y | New Best Y Instances |
| :--- | :---: | :---: | :--- |
| **Function 1** | 2 | 7.710875e-16 (original) | 0 |
| **Function 2** | 2 | 0.656438 (round 3) | 1 |
| **Function 3** | 3 | -0.011060 (round 7) | 2 |
| **Function 4** | 4 | 0.634426 (round 8) | 7 |
| **Function 5** | 4 | 8662.482500 (round 5) | 5 |
| **Function 6** | 5 | -0.286888 (round 8) | 4 |
| **Function 7** | 6 | 1.685017 (round 9) | 2 |
| **Function 8** | 8 | 9.964198 (round 7) | 4 |

## Assumptions and Limitations
The main limitation from my models is that they are not suited to understand the underlying function. For example, it's not a good prediction model because it might perform poorly in a space of low performance, the models (specially the higher dimension functions) are fitted with a subset of dataset which is the higher values, that are generally clustered in a very small space compared to the rest of the datapoints. 

## Ethical Considerations
To support transparency, all the the process and design process has been documented in this model card, the data sheet and within the notebooks themselves where there's notes containing reflections, tests and leave behinds after every round of query. 

The notebooks are also uploaded with reproducibility in mind, the notebooks load all the relevant libraries at the top and the data is self contained in this repo.