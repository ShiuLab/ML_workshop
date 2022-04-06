# Synopsis

Below are the questions raised during the Plant Biology 2020 workshop session on Wednesday 7/29/20.

## Literature 

### On using ML to investigate gene expression patterns:

Depend on what specific questions one want to ask, there are quite a few papers out there using ML to investigate gene expression. Here are some examples:

* [Statistical and Machine Learning Approaches to Predict Gene Regulatory Networks From Transcriptome Datasets](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6281826/)
* [The identification of cis-regulatory elements: A review from a machine learning perspective](https://pubmed.ncbi.nlm.nih.gov/26499213/)
* [The DNA binding landscape of the maize AUXIN RESPONSE FACTOR family](https://pubmed.ncbi.nlm.nih.gov/30375394/)
* [Cis-Regulatory Code for Predicting Plant Cell-Type Transcriptional Response to High Salinity](https://pubmed.ncbi.nlm.nih.gov/31551359/)

### On looking for traits in photos that are too subtle for the human eye (e.g. leaf shape patterns):

Couple interesting studies:

* [Automated classification of tropical shrub species: a hybrid of leaf shape and machine learning approac](https://pubmed.ncbi.nlm.nih.gov/28924506/)
* [Computer vision cracks the leaf code](https://pubmed.ncbi.nlm.nih.gov/26951664/)

### On identifying metabolites with metabolomics data:

In the Plant Biology meeting 2020, [Gaurav Moghe from Cornell gave a talk on this](https://www.eventscribe.com/2020/ASPB/fsPopup.asp?Mode=presInfo&PresentationID=742044&query=gaurav%20moghe). He will be a much better person to answer this qusetion!

## What can ML do? 

### Can ML be used to identify patterns in images?

Serena Ghantous Lotreck : Yes! The types of tasks we’ll discuss in this workshop relate to numerical or categorical data, but there are many approaches that can be applied to image analysis

samantha.neeno : Hi Ira---yes, it is possible. That can be done with Deep Learning models (for example), but then we get into data quality/labeling discussions

### Can I use ML to predict enzyme function (substrate specificity and product prediction), especially in large plant gene families?

We are not expert in this area. Nonetheless, if there are high quality labels of which enzyme catalyze what substrates AND there are structural features (primiary, secondary, and tertiary) available, then one can attempt to build one.

### Can ML be used to score plants as alive/dead? Does this provide more accurate results compared to manual scoring?

If you are able to provide a dataset where you have plant images scored for “live” or “dead”, you’d definitely be able to distinguish. I’m unaware of efforts to use this on plants life/death, but for example, AI systems trained to identify cancer in pathology slides are better able to detect cancer than human pathologists

## Supervised vs. Unsupervised Learning

### Why isn’t clustering a supervised algorithm? Isn’t the grouping (clustering) itself be a label?

You can associate labels with groups, but the algorithm isn’t learning how to label the groups, it merely uses patterns in the data to group instances 

### In my lab, I've used data from experiments with multiple predictors to try to find a regression model that best explains the data. Is this machine learning? Or would machine learning be applying this model to predict the outcome of future experiments based on known predictors? 

Linear regression is absolutely a type of machine learning! But it’s using the regression that you’ve found to make predictions for new instances that would constitute machine learning - finding the best regression is what we call fitting the model

### What is the best way to identify patterns of gene expression that predict the treatment that was imposed?  For example: do plants that were exposed to weeds exhibit different patterns of expression than those that weren’t?

Given the amount of transcriptome data available, this is feasible. You need carefully curated treatment labels for the experiments. Once you have that, you can use all genes where expression levels are available as features to make predictions. For the example you mentioned, perhsps you can take an unsupervised approach clustering the gene expression patterns based on experiments - then you can see if the weed-related experiments stands out on its own or whether it is related to some other treatments.

## I’m just getting started 

### I’m just getting started with ML. What are your recommendations to get started?

0. Find a colleague who known machine learning already - in stat, math, and engineering, they are quite a few people with expertise.
1. Find a question relevant to your research that can be solved by building a statistical model.
2. Start with online resources like this workshop to get a basic understanding of the terms and processes.
3. Check out introductory books like [this one])(https://www.cs.waikato.ac.nz/ml/weka/book.html) that does not require programming experiences or, if you have some Python background, check [this one](https://www.oreilly.com/library/view/hands-on-machine-learning/9781492032632/) out.
4. Follow the books and, in addition to practice on the examples provided by the book, use your own data to see if you can use the approaches in the books to solve your own problems.
5. If at all possible, take one of the many [online courses](https://www.freecodecamp.org/news/every-single-machine-learning-course-on-the-internet-ranked-by-your-reviews-3c4a7b8026c0/).

### I am working on completing my PhD in wet lab research. What can I do to also study machine learning in an efficient but effective way?

The most efficient way to learn is to work with real data as you follow along with books or tutorials. If you have a question and a dataset you’d like to use, we’d recommend flexing your new skills this way.

Also see the answer to the previous question.

### How much programming do I need to use ML?

You don’t need much at all if you use [Weka](https://www.cs.waikato.ac.nz/ml/weka/index.html) a powerful machine learning software that only require that you put data in.

If you have experiences working with command-line interface, you can use [our machine learning pipeline](https://github.com/ShiuLab/ML-Pipeline), which is an end-to-end pipeline that runs on the command line. 

Additionally, if you have basic skills in Python, scikit-learn provides many tools to do machine learning in a fairly streamlined way.

### What options are available on the command line for your ML pipeline tool? 

I'd suggest that you check it out in our Github repository:

https://github.com/ShiuLab/ML-Pipeline

It is rather extensive and is our code-base for multiple ML-related publications in the last five years.

## Data selection 

### There are a lot of biological data online, but the culture and treatment conditions are different: Can I still use these data to train one ML model?

The short answer is yes! Longer version: it is rarely the case that the environment and development stages match among the dataset one want to use. The mismatch is expected to reduce the performance of your models but you should always try. Invariably, they will provide SOME information and ML algorithms are very good at picking relevant information out. If you are worried that you got junky info out of the model, you just need to apply the model to the test set to see if good predictions can be made. If so, it is useful.

### Do all features have to be numerical? 

You can also have categorical features! There are a few differences in how we preprocess categorical data, which we’ll mention further on, but perfectly able to incorporate them!

## Data pre-processing and feature selection 

### How do I split my data between training and test? 

There are two main ways: one is to randomly split the data between training and test, and the other is called stratified sampling, which tries to make sure the test and training sets are representative of the true data

### You’ve said that we must use the same training and test sets in order to reproduce our results. If using a different split gives different results, doesn’t that call into question the quality of the analysis? 

Here "gives different results" I take it to means that the model performance changes depend on the test set. I don't think this call into the quality of the analysis but is an inevitable consequence of sampling. In the best case senario, one would want to use a test set that is representative of the unknowns out there. This is not trivial since we only have a limited amount of test cases. So what you will see is that, given the training samples are fixed, different test sets will give you somewhat different model performance values. But if you look at enough testing sets, then you will find that the averge of the perofrmance is a good estimate of the true performance. 

### How can I impute missing values? 

One practice is simply drop any columns or rows with missing values. If there is little missing data, this practice is fine. IF not imputation is necessary.

For numerical features, it’s common to use the median of the training instances to fill in missing values for features, and for categorical features it’s common to use the most common feature value. There are other options as well!

Julissa Ek Ramos : @MIn-Yao…I am new in ML, but when I am doing some predictions, I use bootstrapping to find the best fitted missing data.

### Does imputation skew the distribution of my original data?

If there are a lot of missing values, for example if median is used, then the distribution will look tighter than it really is.

### Can one-hot encoding be done automatically?

In Scikit-Learn, there is the OneHotEncoder class that you can call to do it.

### At what point is one-hot encoding my categorical features too much? For example, a categorical feature with 10 possible values would result in 10 very sparse features. 

On one hand, such practice increases the number of features, makes the model more complicated, and leads to overfitting. On the other hand, one cannot rule of the possibility that they can be useful. Paricularly considering some ML algorithms are really good at using features with little, but useful infromation, we tend to keep them unless they are too sparse (e.g. only a few percentages of the data is 1 and the rest is zero or vice versa). In those case, we'd drop those.

## Feature selection 

### Will having redundant or similar data affect the final model quality?

Yes! having several highly correlated features can actually negatively impact model performance, and makes model interpretation more difficult That’s what makes feature selection/engineering so important!

### Is there a threshold for removing correlated features? 

It's hard to define a threshold for removing correlated features. One approach is to "merge" correlated features using principle componenet analysis (see [this post](https://medium.com/towards-artificial-intelligence/training-a-machine-learning-model-on-a-dataset-with-highly-correlated-features-debddf5b2e34)).

### In ecology, we know that several environmental variables (features) are highly correlated: for example rainfall and temperature. How we can choose the most useful of these correlated features, and how machine learning can help us?

Song Li : You do PCA to reduce the correlated features to smaller number of features. We typically just use the PC1, PC2 etc as your features

Serena: ne thought is that you could train models with just one and combinations of the correlated group and evaluate performance to see which are the most useful. Random Forest also outputs overall feature importances, so you could take a look at those

Serena: using the PC’s as features does make model interpretation more difficult

### During feature selection, is it best practice to include or exclude information (e.g. experimental blocking, biological replicate) that I know influence the outcome/measured variable?

Song Li : For Brianne, you do a regression to remove those confounding factors from your data before machine learning

### Is it good to use the same ML algorithm (for example, Random Forest) for both feature selection and regression?

In this case we think that the random forest may have superior performance because we also used it to do feature selection - that the features selected were optimal for random forest but not for the others. However, there isn’t a rule about whether you should or shouldn’t do that! You should test many algorithms and choose the highest-performing one

## Performance evaluation 

### How can I determine how different algorithms perform on my data?

In our example, r2 is our performance measure, so the value of r2 from different algorithms allows us to evaluate which algorithms perform best

### In terms of applications of ML in biology, is the general problem model underfitting or model overfitting? 

We typically do 5 or 10 cross-validations. In my own experience, overfitting is more of the problem, as we have highly dimensional data that’s extremely information rich

### Is there an accepted value for performance measures (e.g. r2) in cross-validation? 

This depends on:

1. If there is a model established previously, if the performance measure is better than the previous one.
2. If there is no previous model, is it signfiicantly better than random expectation.

### What does the r2 value during cross-validation tell us? What is the impact of sample size on the conclusions we can draw from looking at r2?

It tells us what the average r2 is after splitting the data 10 times and train 10 differnt models using the training data.

Sample size will impact the interpretation of r2 signfiicantly. In our case there are over 6,000 data points, so even with an r2 of 0.1, the p-value will be extremely small so we did not worry about it. But if the sample size is small, the one should also consider what the p-value is.

## The cutting edge 

### Are you guys applying methods of transfer learning?

We are currently working on transfer learning methods. A manuscript following the general idea of transfer learning using Arabidopsis metaoblic gene annotation to help predicting tomato ones has recently been accepted in [In Silico Plants](https://doi-org.proxy2.cl.msu.edu/10.1093/insilicoplants/diaa005).
















