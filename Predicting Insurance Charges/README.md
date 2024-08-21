# Predicting Insurance Charges

Pricing in insurance is determined by several factors and is assisted by data analysis. To predict future charges and learn more about supporting pricing decisions, I analyzed insurance customer data. I used Excel to import a dataset (Kaggle, Bob Wakefield) containing information about demographics and premium charges. With that data, I utilized Excel’s various functions and VBA features to make my analyses and predictions.
- [Dataset](https://www.kaggle.com/datasets/thedevastator/prediction-of-insurance-charges-using-age-gender) (Kaggle, Bob Wakefield)
- [My Excel Workbook](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Insurance.xlsx)

# Demographics

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/demographics.png)

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/age_bmi_distributions.png)

The insured represented in the data have an average age around 39, with ages ranging as low as 18 to as high as 64, and the majority of the insured are 18-23 years old. BMI follows a normal distribution and its mean is about 30.6, indicating that most of the insured are overweight or obese. There are almost as many females as there are males represented in the data and about 20% are smokers. In terms of region, the Northeast, Northwest, Southeast, and Southwest US are almost equally represented.

# Charges Statistics

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/charges_stats.png)

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/charges_distribution.png)

There is considerable variability in charges made to the insured, with a wide range from near $1,100 to as high as almost $63,800 and a significant standard deviation of approximately $12,100. The distribution of charges is skewed right with the average charge being around $13,300 and a few charges scattered on the much higher end of the distribution. At least 13% of the insured are charged an amount more than one standard deviation greater than the mean (about $25,380).

# Looking for Relationships Between Variables

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/age_vs_charges_groupedBySex.png)

Charges increase as age increases, without an apparent difference between sexes.

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/age_vs_charges_groupedBySmokers.png)

We can see that smokers have clearly higher charges regardless of their age.

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/charges_outliers.png)

Three standard deviations higher than the overall average charge is $49,600.45 (13270.42 + (3*12110.01)). Seven (~0.5%) of the insured represented here are charged more than that amount and are outliers in the dataset. All of them are smokers. In fact, the top 114 highest charged insured are smokers.

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/bmi_vs_charges_groupedBySmoker.png)

There does not appear to be a correlation between BMI and charges, except for smokers. Charges appear to increase linearly for smokers as BMI increases. For smokers, the highest charges occur after a point of inflection at BMI 30 (obesity).

# Predicting Charges

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/regression_age_vs_charges.png)

There is a linear correlation between age and charges that can be modeled by the equation y = 257.72x + 3165.9. The correlation is relatively weak with a coefficient of about 0.30. The slope of the trend line tells us that for every increase of 1 year in age, the average charge to the insured increases by about $257.72.

![Model](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Predicting%20Insurance%20Charges/Images/regression_bmi_vs_charges_smokers.png)

There is a strong positive linear correlation between BMI and charges (r=0.81) amongst smokers. The slope of the trend line tells us that generally as BMI increases by one point, smokers’ charges increase by about $1,473.11.

# Conclusions

Smoking and comorbidities clearly have a dramatic impact on both risk and, thus, charges. Analyzing factors like smoking or comorbidities amongst the insured can support pricing decisions in insurance to help manage the risk they take on by providing coverage.

The correlation equations can provide a roadmap when considered for modeling the charges of other, similar customer groups. They can forecast prices by predicting future charges and they provide useful points of reference for insurers in backing up pricing decisions internally and externally. For instance, an underwriter could use analyses like this when approving or writing a policy and refer to the models to justify their reasoning to a client or to their team.

For more accurate predictions on the age vs. charges correlation, other regression models might be used, or perhaps an exponential trend line might fit better than a linear one. Were I to continue my analysis I would explore other kinds of regression like multiple or polynomial or AI algorithms such as random forest or gradient boosting regression.
