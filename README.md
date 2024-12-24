# Bayesian A/B Testing for Mobile Gaming Data
### Developed by A. C. Sanders | 2024

# Project Overview
This project demonstrates the use of Bayesian A/B Testing to evaluate the effectiveness of different variants in a mobile game, Cookie Cats. Specifically, I analyze the metric, *retention_1*, (whether players return the day after signing up) to determine the success of the test variant over the control group. The test group is labeled gate_40 and the control group is labeled gate_30 in the dataset.

Using Bayesian statistics, I apply Monte Carlo simulations to compute posterior distributions for test and control, calculate the probability that the test variant improves retention, and calculate a 95% credibility interval for the estimated lift (test - control). Additionally, I perform conditional risk analysis to estimate the possible downside risk of releasing the test variant if the control group is actually better.

**Key Highlights**
Custom Python Functionality: The project includes a flexible function for Bayesian A/B testing using Monte Carlo simulations with non-informative priors. The function can also be adapted to use informative priors when domain knowledge is available.

Posterior Estimation: Monte Carlo methods are used to derive posterior distributions of the test and control groups.

Probability Calculation: We calculate the probability that the test variant is better than the control group.

95% Credibility Interval: A 95% credibility interval is computed to estimate the potential lift from the test variant.

Conditional Risk Analysis: We quantify the downside risk of implementing the test variant if the control group turns out to be better.

Visualization: Intuitive plots and charts are generated for posterior distributions and the difference in lift between test and control groups.

This project is designed for data scientists and analysts looking to explore Bayesian approaches to A/B testing, particularly for user retention analysis in mobile gaming.

# Libraries
The following libraries are required to run this project:

numpy
pandas
matplotlib
seaborn
scipy

# Methodology

### Data: 
The experiment is ran on data for the mobile game, *Cookie Cats*. This data was acquired from Mürşide Yarkın and is available on Kaggle [here](https://www.kaggle.com/code/mursideyarkin/mobile-games-ab-testing-with-cookie-cats)

There are two experiment groups in the data: the control (gate_30) and the test group (gate_40).

The main experiment variable is **retention_1**, which is a Boolean that takes *True* if the individual showed up the next day and *False* if they did not return.

### EDA and Data Transformation
Basic EDA and summary statistics are generated.

The data is checked for null values and the proportions of *retention_1* are briefly analyed for each experiment arm.

The Boolean variable, *retention_1*, is transformed into a binary variable for testing. And the values gate_30 and gate_40 are replaced with *control* and *test*, respectively.

### Bayesian Techniques

Posterior Estimation: Bayesian inference is applied to estimate the posterior distributions for both control and test groups using the Beta distribution with non-informative uniform priors.

Monte Carlo Simulation: I perform 10,000 samples from the posterior distributions and calculate the likelihood that the test variant (gate_40) outperforms the control variant (gate_30).

Credibility Interval: A 95% credibility interval is calculated for the difference in *retention_1* between test and control groups.

Conditional Risk: I compute the estimated risk or negative impact on *retention_1* if the control group is actually better but we nevertheless release the test variant.

All results are displayed and plots are created for posterior distributions and the distribution of estimated lift.

# License
This project is licensed under the MIT License. See the **LICENSE** file.
