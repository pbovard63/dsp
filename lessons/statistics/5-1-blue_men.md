[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

## Question:  
In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters μ = 178 cm and   
σ = 7.7 cm for men, and μ = 163 cm and σ = 7.3 cm for women.  

In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com).  
What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.  

## My Code from Response:  

**First, I converted 5'10" and 6'1" to cm from inches:**  
```{python}
def InchesToCm(height):  
    """  
    Takes an input as a height in inches and returns the height in cm.  
    """  
    cm_height = float(height) * 2.54  
    return cm_height  

lower_hgt = InchesToCm(70)  
upper_hgt = InchesToCm(73)  

print(lower_hgt)   
print(upper_hgt)  
```
Output: lower is 177.8 cm, upper is 185.42 cm  

**Next, Found the percentage of the male population that was within this height range:**  
```{python}
pct_range = dist.cdf(upper_hgt) - dist.cdf(lower_hgt)  
print(pct_range)  
```
Output: 34.27%  

**Next, confirmed that sex coding in the data was "1" for Male, to calculate the number of people eligible:**  
```{python}
male = df[df.sex == 1]  
male.htm3.mean()
```
Output: 178.1 cm  

**Finally, Found the number of males eligible (i.e. between 5'10" and 6'1"):**  
```{python}
male_respondents = len(male)  
blue_man_eligible = male_respondents * pct_range  
print(int(blue_man_eligible))  
```
Output: 53,366 men in the survey  

Images:  
![](Images/Ch5%20Ex1%20Intial%20Image.png)
![](Images/Ch5%20Ex1%20Final%20Image.png)
