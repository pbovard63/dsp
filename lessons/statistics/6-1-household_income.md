[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

## **Question:**  
Compute the median, mean, skewness and Pearson’s skewness of the resulting sample. What fraction of households   report a taxable income below the mean? How do the results depend on the assumed upper bound?  

## **My Answer:**  
**First: upper bound of $1MM income:**  
*Computing Median Income:*  
```{python}
median_income = Median(sample)
print("Median Income: ${}".format(median_income))
```
Output: Median Income: $51850.467130224424  
  
*Computing Mean Income:*  
```{python}
mean_income = Mean(sample)
print("Mean Income: ${}".format(mean_income))
```
Output: Mean Income: $64917.27321308837  
  
*Computing Sample Skewness:*  
```{python}
sample_skewness = Skewness(sample)
print("Sample Skewness: {}".format(sample_skewness))
```
Output: Sample Skewness: 1.501796755986916  
  
*Computing Sample Pearson's Skewness:*  
```{python}
sample_pearson = PearsonMedianSkewness(sample)
print("Pearson's Skewness: {}".format(sample_pearson))
```
Output: Pearson's Skewness: 0.7796867219331586  
  
**Observation:** Based on the mean being higher than the Median,  
this has a right (positive) skew. The Pearson skewness and skewness  
both support this, as they are both also positive.  
*Computing percentage with income less than or equal to mean:*  
```{python}
#Fraction of Households with an income of less than or equal to the mean.
cdf.Prob(mean_income)
```
Output: 0.6014113322699216  
  
**How would increasing the upper bound affect this data?**
My assumption: The assumed upper bound limits the true Skew of the data, as higher incomes would lead to an even  
further rightward skew, pulled by the higher incomes. All incomes above $1MM are fixed, so their effect is not    
fully seen.  
**Testing: upper bound of $10MM income:**  
*Computing Median Income:*  
```{python}
#Increasing Limit to 10 million (log = 7) upper bound:
median_income = Median(sample)
print("Median Income: ${}".format(median_income))
```
Output: Median Income: $51851.43596335339  
  
*Computing Mean Income:*  
```{python}
#Increasing Limit to 10 million (log = 7) upper bound:
mean_income = Mean(sample)
print("Mean Income: ${}".format(mean_income))
```
Output: Mean Income: $65716.6597189188  
  
*Computing Sample Skewness:*  
```{python}
#Increasing Limit to 10 million (log = 7) upper bound:
sample_skewness = Skewness(sample)
print("Sample Skewness: {}".format(sample_skewness))
```
Output: Sample Skewness: 76.8955675708605  
  
*Computing Sample Pearson's Skewness:*  
```{python}
#Increasing Limit to 10 million (log = 7) upper bound:
sample_pearson = PearsonMedianSkewness(sample)
print("Pearson's Skewness: {}".format(sample_pearson))
```
Output: Pearson's Skewness: 0.45272673642253447  
  
*Computing percentage with income less than or equal to mean:*  
```{python}
#Fraction of Households with an income of less than or equal to the mean.
cdf.Prob(mean_income)
```
Output: 0.6070756720674798  
