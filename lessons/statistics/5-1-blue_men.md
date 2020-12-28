[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

## Code from Response:  

**First, I converted 5'10" and 6'1" to cm from inches:**  
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
Output: lower is 177.8 cm, upper is 185.42 cm  

**Next, Found the percentage of the male population that was within this height range:**  
pct_range = dist.cdf(upper_hgt) - dist.cdf(lower_hgt)  
print(pct_range)  
Output: 34.27%  

**Next, confirmed that sex coding in the data was "1" for Male, to calculate the number of people eligible:**  
male = df[df.sex == 1]  
male.htm3.mean()  
Output: 178.1 cm  

**Finally, Found the number of males eligible (i.e. between 5'10" and 6'1"):**  
male_respondents = len(male)  
blue_man_eligible = male_respondents * pct_range  
print(int(blue_man_eligible))  
Output: 53,366
