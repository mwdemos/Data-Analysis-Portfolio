# Predicting Insurance Charges

Pricing in insurance is determined by several factors and is assisted by data analysis. To predict future charges and learn more about supporting pricing decisions, I analyzed insurance customer data. I used Excel to import a [dataset](https://www.kaggle.com/datasets/thedevastator/prediction-of-insurance-charges-using-age-gender) (Kaggle, Bob Wakefield) containing information about demographics and premium charges. With that data, I utilized Excel’s various functions and VBA features to make my analyses and predictions.

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
