---
title: "Regression Analysis Project: The Lending Club"
date: 2020-01-28
tags: [Statistics]
header:
  image: "/images/lending-club/lendingclub1.png"
excerpt: "Statistics, Linear Regression, Interaction, Personal Loan"
---

# INTRODUCTION

This is a group project in my Data Analytics I class. Through this project, our group was able to understand what factors determine the interest rate that borrowers pay.

The data set was provided from the Lending Club platform that matches borrowers to lenders. Lending Club determines an interest rate for a loan based on a number of characteristics of the borrower.

The project included 3 parts: 1) Comparing Populations, 2) Manipulating Data, 3) Regression Analysis.
The regression models were run in either SAS Studio or SPSS.

You can find the full project description and the data set [here](https://github.com/AnhCao-96/Lending-Club-Project)

# DATA PROCESSING AND FINDINGS

This post will include the outputs for Part 3 to predict the interest rate and the loan amount for Louise Card.

**SCENARIO:**
Louise Card became the director of alumni relations with College of Business. She is looking for a $20,000 loan to build her dream outdoor kitchen so that she can entertain alums at her house on football game days. She would like to pay the loan off over 36 months. Her income is verified at $150,000. Her credit is very good (A) and credit history goes back to 2003. Having graduated not too long ago, she does have an outstanding mortgage on it. As of now, she has open credit cards with a revolving balance of $4000.

## INTEREST RATE PREDICTION

### MODEL 1

In this model, we included all the variables that have values available to us: loan amount, annual income, revolving balance, newterm (a dummy variable for 36 month or 60 month term), loan grade (A,B,C,D,E,F), and ownership (OWN, MORTGAGE, RENT). Since all the information available was important, we would like to utilize all the information we had from Louise to get the closest interest rate estimate.

![alt]({{ site.url }}{{ site.baseurl }}/images/lending-club/Interest Rate Model 1.PNG)

*	Loan amount makes a theoretical sense that high-principal loans many have higher rates than lower loan amounts.
*	Annual income may be a factor to consider the borrower’s ability to pay back the loan.
*	A high revolving balance may cause a chance for a default.
*	Loan grade is important since there is a higher chance for a default for a higher perceived risk loan.
*	Ownership means that if the borrower has at least an outstanding mortgage, the loan would result in additional monthly fixed payment.

### MODEL 2

In the second model, to make it more general, we would like to include another variable dti (debt to income ratio) which was considered critical to estimate the loan interest rate. This variable is to show how much of a person's monthly gross income is for debt payments. The higher the ratio is, the less spare cash left, which could be a risk as there could be a chance for a default.

![alt]({{ site.url }}{{ site.baseurl }}/images/lending-club/IR Model 2.PNG)

**INTERPRETATION:**

* None of the independent variables are highly correlated to one another.
* Holding everything else constant, an increase of $1 in loan amount decreases the interest rate by 2.85E-06%.
* Holding everything else constant, a 1 unit increase in dti results in a 0.004% increase in interest rate.
* Annual income does not have a significant relationship with interest rate, but we included it in the model because it would make intuitive sense for it to affect interest rate, so including it tells a more complete story.
* The TermDummy variable means that when going from a 36 month[0] loan to a 60 month[1], the interest rate increases by .17%.
* For loan grade, we used Grade A as my base group, so as compared to Grade A, the interest rate is increased by 4%, 7.9%, 12.5%, 18.2%, 22.2% for Grade B,C,D,E,F respectively.
* We used RENT as my base group for my ownership dummy variable, so compared to renting, owning a home increases the interest rate by 0.001% and having a mortgage decreases the interest rate by 0.081%.

## LOAN AMOUNT PREDICTION

### MODEL 1

In the data set, loan amount refers to the particular dollar amount loan customers applied for. However, we would like to use this information as the maximum amount a customer may be eligible for. Therefore, based on the model, we were able to determine how much loan Louise could get approved for.

We first included the interest rate variable in the model. However, when we ran the collinearity diagnosis (VIF), we found that interest rate and loan grade were every highly correlated. Therefore, we decided to exclude the interest rate.

In addition to the loan grade variable, we did include other variables while running the analysis in order to take out the effect of those variables on loan amount. In fact, all the variables explained up to 97% of the variability.

![alt]({{ site.url }}{{ site.baseurl }}/images/lending-club/LM Model 1.PNG)

* The loan grade is included to see how the loan grade would affect the max loan amount that Louise could apply for. The TermDummy shows how the term would affect the loan amount. Theoretically, a longer loan would include a higher risk.
* When borrowers wanted to apply for a high loan amount, it may be used to pay for their outstanding balance of all accounts. Thus, the lender will need to consider if they have outstanding mortgages, credit balances (revolving balances), and installments.
* Then in order to check the ability of the borrow to make payments, the lender should consider his/her annual income. Also, the dti variable may show if there could be a chance for a default, since if the ratio is too high, the borrower would not have a lot of spare money to make a higher payment once the loan originates.
* Last but not least, payment history is critical for consideration because it shows if the borrower has failed to make required payments in the past.

**INTERPRETATION:**

Keep everything constant, treating Grade B as the baseline group:

* The loan amount for Grade A would be increased by approximately $747
* The loan amount for Grade C would be decreased by approximately $1056
* The loan amount for Grade D would be decreased by approximately $2447
* The loan amount for Grade E would be decreased by approximately $4213
* The loan amount for Grade F would be decreased by approximately $5961

### MODEL 2

![alt]({{ site.url }}{{ site.baseurl }}/images/lending-club/LM Model 2.PNG)

In this model, we included the interest rate variable instead of loan grade. In order to determine if Louise's loan amount would be higher if she pays more money in each installment at a higher interest rate, we need to include an interaction variable between installment and interest rate.

![alt]({{ site.url }}{{ site.baseurl }}/images/lending-club/interaction.png)

Based on the interaction term, as you pay a higher installment at a higher interest rate, loan amount decreases. So this would not be a good strategy for her.

**INTERPRETATION:**

* The above model ran with loan amount as the dependent variable is a very good model fit because ANOVA shows a good fit as well as the Standard error compared to the dependent mean.
* Holding everything else constant, a $1000 increase in annual income, increases the loan amount by 80 cents.
* The TermDummy variable means that when going from a 36 month loan to a 60 month, the loan amount increases by $6922.
* Holding everything else constant, a 1 unit increase in dti results in a 0.442 increase in interest rate.
* Holding everything else constant, every 1 more delinquency in the last 2 years would decrease the loan amount by 28.
* Holding everything else constant, a $1000 more in revol_bal would increase the loan amount by 4 cents.
* We used RENT as our base group for the ownership dummy variable, so compared to renting, owning a home increases the loan amount by 29 and having a mortgage increases the loan amount by 75.
