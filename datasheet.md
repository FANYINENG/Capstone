# Datasheet: Black Box Optimization & Query Dataset

This datasheet provides documentation on the structure, collection, preprocessing, and lifecycle of the optimization query data generated during this Capstone project.

---

## Motivation
This data set is part of a Black Box Optimization problem. There are 8 functions in total and each function has a starting dataset. The project consists of submitting a single query every week for each function which outputs one extra datapoint to help discover and maximize the performance of each function. 

The purpose of this data is educational and meant as a learning exercise. 

## Composition
The data's raw format is npy (standard binary for Numpy), for the initial data it's broken into two files initial_inputs.npy and initial_outputs.npy 

The first step in the notebook loads the data and stores them as a single pd dataframe, where the features are given x1, x2, x3...xN column names and "target" as the name for the output.

A sample datapoint looks like this:          

x1   | x2  | target

0.665800 | 0.123969 | 0.538996

The initial data composition is as follows:
* Function 1: 2D , 10 datapoints
* Function 2: 2D , 10 datapoints
* Function 3: 3D , 15 datapoints
* Function 4: 4D , 30 datapoints
* Function 5: 4D , 20 datapoints
* Function 6: 5D , 20 datapoints
* Function 7: 6D , 30 datapoints
* Function 8: 6D , 40 datapoints

## Collection Process
The new data pipeline was as follows:
1. Fit existing data to a Bayesian Optimisation model 
2. Submit query (into the capstone portal)
3. Receive the new datapoint (via email)
4. Update the dataset by adding the new datapoint
5. Repeat process 

The models would change gradually over the weeks, hyperparameters would be tuned (using different kernels) and the overall strategy is a mix of exploration and exploitation. Each week's progress and decision-making is documented in the notes inside the functions' notebooks. 

## Preprocessing and Uses
All the data both the original dataset and the incremental datapoints added every week through the query mechanism would be standardized before fitting into a model. 

I used the StandardScaler function from sklearn.preprocessing library. 

The data is intended to apply different techniques and strategies in a black box function problem, there's a short description of the overall function and objective, but there's no labels for the features, there's no context about intended ranges for outputs. The dataset here is very small, so it's not a good fit for techniques that require larger datasets. 

## Distribution and Maintenance
The data is available in this Github repository. Open to all to use freely and publicly. 

Maintained by Yineng.  
