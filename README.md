## SIMULATION PROJECT - r programming

## Simulation Study 1, Significance of Regression

In this simulation study we will investigate the significance of regression test. We will simulate from two different models using the data found in study_1.csv file:

The “significant” model 
Yi=β0+β1xi1+β2xi2+β3xi3+ϵi
where ϵi ~ N(0,σ2) and β0 =3, β1 =1, β2 =1, β3 =1.

The “non-significant” model
Yi=β0+β1xi1+β2xi2+β3xi3+ϵi
where ϵi
 ~ N(0,σ2
) and β0 =3, β1 =0, β2 =0, β3 =0.

For both, we will consider a sample size of 25 (n = 25) and three possible levels of noise. That is, three values of σ
 i.e., σ ∈ (1,5,10)

Then for each of the three values of σ, for calculate the following for both models.

A. The Fstatistic for the significance of regression test
B. The p-value for the significance of regression test
C. R2

For each model-σ combination we will use 2500 simulations. Then for each simulation, we will fit a regression model.

![pic1](https://github.com/bsathyamur/simulation_project_r_programming/blob/master/fstat-and-val-comp.png)

![pic2](https://github.com/bsathyamur/simulation_project_r_programming/blob/master/rsquared-comp.png)

### Discussion

#### f-Statistic 
The f-statistic doesn’t seem to align with the true distribution curve.
#### p-Value 
When the null hypothesis, H0, is true, all p-values between 0 and 1 are equally likely. In other words, the p-value has a rectangular distribution between 0 and 1
On the other hand, if H1 is true, then the p-values have a distribution for which p-values near zero are more likely than p-values near 1. The precise distribution under the alternative hypothesis depends on the specific hypotheses being tested and the true value of the parameter, but it always favours values near 0.
#### R-squared
I am not able to understand what type of distribution does the r-squared follows under null and alternate hypthesis. Lower values of sigma seem to have more dense higher values of R-squared for the significant model. In case of the non significant model since its mostly noise, the r-squared doesn’t seem to vary much for each sigma.

## Simulation Study 2, Using RMSE for Selection

Using the data found in study_2.csv, We will simulate from the below model

Yi=β0+β1xi1+β2xi2+β3xi3+β3xi4+β3xi5+β3xi6+ϵi where ϵi ~ N(0,σ2) and β0 =0, β1 =5, β2 =-4, β3 =1.6, β1 =-1.1, β2 =0.7, β3 =0.3.

We will consider a sample size of 500 and three possible levels of noise. That is, three values of σ i.e., n=500 and σ ∈ (1,2,4).We simulate the data by randomly splitting the data into train and test sets of equal sizes (250 observations for training, 250 observations for testing).For each simulation, we fit the nine models, with forms as shown below:
y ~ x1
y ~ x1 + x2
y ~ x1 + x2 + x3
y ~ x1 + x2 + x3 + x4
y ~ x1 + x2 + x3 + x4 + x5
y ~ x1 + x2 + x3 + x4 + x5 + x6
y ~ x1 + x2 + x3 + x4 + x5 + x6 + x7
y ~ x1 + x2 + x3 + x4 + x5 + x6 + x7 + x8
y ~ x1 + x2 + x3 + x4 + x5 + x6 + x7 + x8 + x9
For each model and for each of the level of noise, we simulate 1000 times and calculate the Train and Test RMSE to identify the best model.

![RMSE_comparison](https://github.com/bsathyamur/simulation_project_r_programming/blob/master/RMSE-comp1.png)

### Discussion

Based on the plots in the results section, when looking at the mean RMSE for train vs. Test and also the frequency of the lowest RMSE, model 6 seems to get picked consistently as the best model. So the method seem to be pick the right model consistently.

When sigma is low, the frequency of lowest RMSE increases which suggests that as noise increases the possibility of a model getting picked up as best model increases.

## Simulation Study 3: Power

we will investigate the power of the significance of regression test for simple linear regression.

H0:β1=0 vs H1:β1≠0

Power is the probability of rejecting the null hypothesis when the null is not true, that is, the alternative is true and β1 is non-zero.Many things affect the power of a test. In this case, some of those are:

Sample Size, n
Signal Strength, β1
Noise Level, σ
Significance Level, α
In this study, we’ll investigate the first three. To do so we will simulate from the model

Yi=β0+β1xi+ei

We will then consider different signals, noises, and sample sizes:
β1 ∈ (−2,−1.9,−1.8,…,−0.1,0,0.1,0.2,0.3,…1.9,2)
σ ∈ (1,2,4)
n ∈ (10,20,30)

We will hold the significance level constant at α=0.05 . 

![power-pic](https://github.com/bsathyamur/simulation_project_r_programming/blob/master/power-comp.png)

### Discussion

Based on the plots in the results section, for sigma = 1 and 2 their seem to be not much difference in power but when sigma = 4 the power reduced drastically which suggests that as sigma increases power decreases.

Also the power curve is least when beta1 is close to 0 rather than the beta1 values farther away from zero which suggests that as beta1 is close to zero power decreases.

Within each sigma, the number of observations doesn’t seem to have much of variation or impact on the power curve. There is some negligible difference between each values of n. So overall we can conclude sigma and beta1 seem to have a greater impact on power rather than number of observations.

I tried to simulate with 2000 observations and the result still seem to be the same.So doing the simulation 1000 times seem to be sufficient for this case study.
