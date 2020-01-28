---
title: "Regression Analysis Project: The Lending Club"
date: 2020-01-28
tags: [statistics, SAS/SPSS, regression, interactions]
header:
  image: "/images/about.jpg"
excerpt: "Statistics, Linear Regression, Personal Loan"
---

# Introduction:

This is a group project in my Data Analytics I class. Through this project, our group was able to understand what factors determine the interest rate that borrowers pay.

The data set was provided from the Lending Club platform that matches borrowers to lenders. Lending Club determines an interest rate for a loan based on a number of characteristics of the borrower.

The project included 3 parts: 1) Comparing Populations, 2) Manipulating Data, 3) Regression Analysis.
The regression models were run in either SAS Studio or SPSS.

You can find the full project description and the data set [here](https://github.com/AnhCao-96/Lending-Club-Project)

# Data Processing and Findings:

This post will include the outputs for Part 3 to predict the interest rate and the loan amount for Louise Card.

## Interest Rate Prediction

### Model 1:

In this model, we included all the variables that have values available to us: loan amount, annual income, revolving balance, newterm (a dummy variable for 36 month or 60 month term), loan grade (A,B,C,D,E,F), and ownership (OWN, MORTGAGE, RENT). Since all the information available was important, we would like to utilize all the information we had from Louise to get the closest interest rate estimate.

o	Loan amount makes a theoretical sense that high-principal loans many have higher rates than lower loan amounts.

o	Annual income may be a factor to consider the borrower’s ability to pay back the loan.

o	A high revolving balance may cause a chance for a default.

o	Loan grade is important since there is a higher chance for a default for a higher perceived risk loan.

o	Ownership means that if the borrower has at least an outstanding mortgage, the loan would result in additional monthly fixed payment.

image: "/images/lending-club/Interest Rate Model 1/png"

### Model 2:

In the second model, to make it more general, we would like to include another variable dti (debt to income ratio) which was considered critical to estimate the loan interest rate. This variable is to show how much of a person's monthly gross income is for debt payments. The higher the ratio is, the less spare cash left, which could be a risk as there could be a chance for a default.

image: "/images/lending-club/IR Model 2.png"
