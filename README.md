# GOVT19: Applied Multivariate Data Analysis

## Final Group Project: Factors Determining Sentence Length and Severity for U.S. Inmates	
- Affiliation: Dartmouth College
- In Brief: Conducted multivariate linear and logistic regression using R, investigating the significant predictors of sentence length and severity for U.S. inmates across State and Federal Prisons. Visualized results showing expected values of receiving an extreme sentence as a function of various predictors including age, race, gender, education level, family background.

### Project Description

##### Question and Hypotheses
Of demographic and case-specific factors, which are significant predictors of sentence length and severity?
- H1: Black defendants can expect to receive longer sentences than white defendants. 
- H2: The effect of being a violent offender, as opposed to being a non-violent offender on sentence length is greater for Black defendants as opposed to white defendants.
- H3: Older defendants are less likely to receive an extreme sentence (life in prison or the death penalty) than younger defendants.

##### Background Research:
The American criminal justice system has long been criticized for showing racial bias in sentencing decisions (Everett 2002). Hence, state and federal sentencing guidelines were implemented to reduce disparities in sentencing on the basis of race and ethnicity, and ensure neutrality in sentencing (Blair 2004). However, research shows that Blacks still tend to receive harsher sentences than whites and that the differences in sentence length are only partly explained by offense-related characteristics (Everett 2002). 

##### Data:
We are examining a set of variables from the 2004 Survey of Inmates taken from the Bureau of Justice Statistics. This survey was conducted through personal interviews of a nationally representative sample of inmates across both State and Federal prisons. The survey included responses to questions about demographics, criminal history, sentencing, gender, drug use, and prisoner health. 

##### Methodology:
For H1 & H2, we use a multivariate linear regression with an interaction term Black & violent offense as one of the IVs and sentence in months as the DV.
- Given the skew of our DV (with 6% classified as outliers and increasing the mean sentencing by 30 months), we estimated three OLS models, with varying degrees of outlier removal. We decided to use the most restrictive model (excluding sentences greater than 2000 months), given that its R-squared value is slightly higher, meaning more variation is explained by the model. Note: no predictors change in sign or statistical significance between the three models.
- We calculated pairwise correlations between predictors to test for multicollinearity.
To study H3, we use a logistic regression. The dependent variable of interest is whether or not a defendant receives an extreme sentence (either life in prison or the death penalty). 
- We created a subset of the data that only included entries for violent offenses, not drug or property offenses, because violent offenses are a near perfect predictor for receiving extreme sentences. 

##### Discussion:
- What we are interested in is whether there is a difference in sentence length (in months) for Black vs white offenders conditional on their offense being violent. In our chosen linear model (the rightmost model), the interaction term Black x Violent Offense is statistically significant, confirming our second hypothesis that sentence length increases for the offense being violent is dependent on the offender being Black or white.
- The effect of being a violent offender (not changing the race of the offender from the baseline of being white) induces an increase of 107.5 months. This effect is statistically significant, with a p-value of <2e-16.
- The effect of being black and a violent offender is 129.4 months – 22 months greater than their white counterparts. This effect is statistically significant, with a p-value of 4.91e-160. Note that this p-value was calculated from the standard error found using the variance covariance matrix.
In regards to our first hypothesis that black defendants can expect to receive longer sentences, our model showed that the isolated effect of being black is a 4.75 month increase, but this result is not statistically significant.

The binomial logit model showed that only two predictors are statistically significant in predicting whether or not a defendant receives an extreme sentence, those two being Black (β = 0.29) and age (β = 0.42). 
We were intrigued by the significance of age, and plotted the predicted probability of receiving an extreme sentence as a function of age across the five categories given in our data set. As observed in the graph, the Pr(extreme sentence) increases as the defendant’s age increases. To examine the substantive significance, we calculated the change in Pr(extreme sentence) when we change the age category for a hypothetical profile of a defendant. As seen in our table, the predicted probability increases by at least .05 for each unit increase to the subsequent age category. This is a substantively significant effect. In addition, the change in the predicted probability increases as age category increases – e.g., a defendant that is 25-34 as opposed to <25 sees a .05982 increase in their Pr(extreme sentence), but when that increase is to 65-96 from 55-64, that change in probability is as high as .10.
In conclusion, our findings disprove our final hypothesis that older defendants are less likely to receive an extreme sentence than younger ones. This is because age was a statistically significant predictor of receiving an extreme sentence, but in the direction of older defendants being more likely to receive an extreme sentence. This effect was also determined to be substantively significant.

##### Works Cited
- Blair, I. V., Judd, C. M., & Chapleau, K. M. (2004). The Influence of Afrocentric Facial Features in Criminal Sentencing. Psychological Science, 15(10), 674–679.
- Everett, Ronald S; Wojtkiewicz, Roger A. (2002). Difference, Disparity, and Race/Ethnic Bias in Federal Sentencing: [1]. Journal of Quantitative Criminology; New York Vol. 18, Iss. 2, 189-211.
- Ryon, Stephanie Bontrager, et al. “Sentencing in Light of Collateral Consequences: Does Age Matter?” Journal of Criminal Justice, vol. 53, 2017, pp. 1–11., doi:10.1016/j.jcrimjus.2017.07.009.
