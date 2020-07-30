# Literature 

## On using ML to investigate gene expression patterns:



## On looking for traits in photos that are too subtle for the human eye (e.g. leaf shape patterns):



## On identifying metabolites with metabolomics data:

# What can ML do? 

## Can ML be used to identify patterns in images?

Serena Ghantous Lotreck : Yes! The types of tasks we’ll discuss in this workshop relate to numerical or categorical data, but there are many approaches that can be applied to image analysis
samantha.neeno : Hi Ira---yes, it is possible. That can be done with Deep Learning models (for example), but then we get into data quality/labeling discussions

## Can I use ML to predict enzyme function (substrate specificity and product prediction), especially in large plant gene families?

Disclaimer: we are not expertise in this area. Nonetheless, if there are high quality labels of which enzyme catalyze what substrates AND there are structural features (primiary, secondary, and tertiary) available, then one can attempt to build one.

## Can ML be used to score plants as alive/dead? Does this provide more accurate results compared to manual scoring?

If you are able to provide a dataset where you have plant images scored for “live” or “dead”, you’d definitely be able to distinguish. I’m unaware of efforts to use this on plants life/death, but for example, AI systems trained to identify cancer in pathology slides are better able to detect cancer than human pathologists

# Supervised vs. Unsupervised Learning

## Why isn’t clustering a supervised algorithm? Isn’t the grouping (clustering) itself be a label?

You can associate labels with groups, but the algorithm isn’t learning how to label the groups, it merely uses patterns in the data to group instances 

## In my lab, I've used data from experiments with multiple predictors to try to find a regression model that best explains the data. Is this machine learning? Or would machine learning be applying this model to predict the outcome of future experiments based on known predictors? 

Linear regression is absolutely a type of machine learning! But it’s using the regression that you’ve found to make predictions for new instances that would constitute machine learning - finding the best regression is what we call fitting the model

## What is the best way to identify patterns of gene expression that predict the treatment that was imposed?  For example: do plants that were exposed to weeds exhibit different patterns of expression than those that weren’t?

# I’m just getting started 

## I’m just getting started with ML. What are your recommendations to get started?

## I am working on completing my PhD in wet lab research. What can I do to also study machine learning in an efficient but effective way?

The most efficient way to learn is to work with real data as you follow along with books or tutorials. If you have a question and a dataset you’d like to use, we’d recommend flexing your new skills this way.

## How much programming do I need to use ML?

You don’t need much! You can use our machine learning pipeline, https://github.com/ShiuLab/ML-Pipeline, which is an end-to-end pipeline that runs on the command line. Additionally, if you have basic skills in Python, scikit-learn provides many tools to do machine learning in a fairly streamlined way

## What options are available on the command line for your ML pipeline tool? 

# Data selection 

## There are a lot of biological data online, but the culture and treatment conditions are different: Can I still use these data to train one ML model?

## Do all features have to be numerical? 

You can also have categorical features! There are a few differences in how we preprocess categorical data, which we’ll mention further on, but perfectly able to incorporate them!

# Data pre-processing and feature selection 

## How do I split my data between training and test? 
there are two main ways: one is to randomly split the data between training and test, and the other is called stratified sampling, which tries to make sure the test and training sets are representative of the true data

You’ve said that we must use the same training and test sets in order to reproduce our results. If using a different split gives different results, doesn’t that call into question the quality of the analysis? 

## How can I impute missing values? 
 for numerical features, it’s common to use the median of the training instances to fill in missing values for features, and for categorical features it’s common to use the most common feature value. There are other options as well!
Julissa Ek Ramos : @MIn-Yao…I am new in ML, but when I am doing some predictions, I use bootstrapping to find the best fitted missing data.

## Does imputation skew the distribution of my original data?

## Can one-hot encoding be done automatically?

At what point is one-hot encoding my categorical features too much? For example, a categorical feature with 10 possible values would result in 10 very sparse features. 

# Feature selection 

## Will having redundant or similar data affect the final model quality?

Yes! having several highly correlated features can actually negatively impact model performance, and makes model interpretation more difficult That’s what makes feature selection/engineering so important!

## Is there a threshold for removing correlated features? 

There’s no universal threshold for removing correlated features, it will depend on what you want and also how they effect model performance

## In ecology, we know that several environmental variables (features) are highly correlated: for example rainfall and temperature. How we can choose the most useful of these correlated features, and how machine learning can help us?

Song Li : You do PCA to reduce the correlated features to smaller number of features.we typically just use the PC1, PC2 etc as your features

Serena: ne thought is that you could train models with just one and combinations of the correlated group and evaluate performance to see which are the most useful. Random Forest also outputs overall feature importances, so you could take a look at those

Serena: using the PC’s as features does make model interpretation more difficult

## During feature selection, is it best practice to include or exclude information (e.g. experimental blocking, biological replicate) that I know influence the outcome/measured variable?

Song Li : For Brianne, you do a regression to remove those confounding factors from your data before machine learning

## Is it good to use the same ML algorithm (for example, Random Forest) for both feature selection and regression?

In this case we think that the random forest may have superior performance because we also used it to do feature selection - that the features selected were optimal for random forest but not for the others. However, there isn’t a rule about whether you should or shouldn’t do that! You should test many algorithms and choose the highest-performing one

# Performance evaluation 

## How can I determine how different algorithms perform on my data?
in this case, r2 is our performance measure, so the value of r2 from different algorithms allows us to evaluate which algorithms perform best

In terms of applications of ML in biology, is the general problem model underfitting or model overfitting? 
 we typically do 5 or 10 cross-validations. In my own experience, overfitting is more of the problem, as we have highly dimensional data that’s extremely information rich

Is there an accepted value for performance measures (e.g. r2) in cross-validation? 

What does the r2 value during cross-validation tell us? What is the impact of sample size on the conclusions we can draw from looking at r2?
The cutting edge 
Are you guys applying methods of transfer learning?
we’re just dipping our toes in the water!
















