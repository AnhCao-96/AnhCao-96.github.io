---
title: "Machine Learning: How Would The Sale Price of A Toyota Be Predicted?"
date: 2020-04-17
tags: [Machine Learning]
header:
  image: "/images/Toyota/toyotabrand.png"
excerpt: "Data Mining, SAS Enterprise Miner, Decision Tree, Neural Network, Toyota"
---

# INTRODUCTION

This data mining project is to predict the sale price of the Toyota Corolla brand cars based on different predictors:

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/indicators.PNG)

The project was ran in the SAS Enterprise Miner software using two different methods such as Decision Tree and Neural Network to output the optimal predictive model that includes the most important variables for sale price prediction.

You can find the full project description and the data set [here](https://github.com/AnhCao-96/Lending-Club-Project)

# DECISION TREE METHOD

## DATA PROCESSING AND FINDINGS

### THE FLOW DIAGRAM & DESCRIPTION

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/flowdiagram.PNG)

In the diagram, the File Import node was used to import the file into SAS as it was an excel file. The Data Partition node was assigned with a breakdown of 60% train, 30% validation, 10% test. Then two decision tree models were ran to compare the simplicity and the fit of the models. Since the Price target was a continuous variable, there were two different splitting methods offered in SAS EM such as F-statistics and Variance. At the same time, Average Squared Error (ASE) was chosen to be the assessment measure for both of the models. Thus, for the first decision tree, F-statistic for splitting and Average Squared Error (ASE) as the assessment measure, and for the second decision tree, we used Variance for splitting and ASE as the assessment measure. Finally, the Model Comparison was used to examine the two model and select the better one.

Note: Decision Tree node was also used for variable selection step.

### DECISION TREE USING F-STATISTICS (MODEL 1)

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/probf.PNG)

**Subtree Assessment Plot**

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/subtreeprobf.PNG)

**Variable Importance In Descending Order**

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/importantprobf.PNG)

### DECISION TREE USING VARIANCE (MODEL 2)

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/variance.PNG)

**Subtree Assessment Plot**

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/subtreevariance.PNG)

**Variable Importance In Descending Order**

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/importantvariance.PNG)

The decision tree in model 1 was pruned at the 26th leave node based on the cutoff value whereas the decision tree in model 2 has 30 leaves after pruning based on the best split to minimize the variance. The default settings were used for tree pruning in both of the models.

### MODEL OUTPUTS AND FINDINGS

**Score Rankings Overlay: Price**

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/meanpredictedchart.PNG)

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/meanpredictedtable.PNG)

By looking at the score rankings overlay plot, the Mean Predicted curves of both of the models seem very close to each other, meaning that the differences of the predicted means between the models are minor.

**Fit Statistics**

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/fitstatistics.PNG)

In order to choose the best model, it is always better and more clear to look at several metrics. Based on the Fit Statistics table, in terms of RMSE, the decision tree using Variance fitting method is better. It indicates the absolute fit of the model to the data, which is how close the observed data points are to the model's predicted values. The RMSE is lower therefore produces a better fit in the Variance model.

**Validation Record Example**

![alt]({{ site.url }}{{ site.baseurl }}/images/Toyota/validrecord.PNG)

With the same record, the two decision trees above give different predicted prices. Based on the decision tree in model 1, the predicted price for the specific car model was $14,903 while the decision tree in model 2 predicted higher price, which was $15,277. Therefore once again, the Variance model is concluded to be the better model for the company to predict the car price.
