[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)
## Question:  
Something like the class size paradox appears if you survey children and ask how many children are in their   
family. Families with many children are more likely to appear in your sample, and families with no chil- dren   
have no chance to be in the sample.  

Use the NSFG respondent variable NUMKDHH to construct the actual distribu- tion for the number of children  
under 18 in the household.  

Now compute the biased distribution we would see if we surveyed the children and asked them how many children   
under 18 (including themselves) are in their household.  

Plot the actual and biased distributions, and compute their means. As a starting place, you can use   
chap03ex.ipynb.  

## Exercise 3.1: My Code:  
```{python}
resp = nsfg.ReadFemResp()
```
*Standard Histogram:*  
```{python}
hist_num = thinkstats2.Hist(resp.numkdhh, label='Children per Household')  
thinkplot.Hist(hist_num)  
thinkplot.Config(xlabel='Number of Children per Household', ylabel='Count'). 
```

*Standard PMF:*  
```{python}
pmf_num = thinkstats2.Pmf(resp.numkdhh, label='Children per Household - Unbiased')  
thinkplot.Pmf(pmf_num)  
thinkplot.Config(xlabel='Number of Children per Household', ylabel='Count')  
```

*Biased PMF:*     
```{python}
biased_pmf_num = BiasPmf(pmf_num, label='Biased')  
thinkplot.PrePlot(2)  
thinkplot.Pmfs([pmf_num, biased_pmf_num])  
thinkplot.Config(xlabel='Children Per Household', ylabel='PMF')  
```

*Mean of Unbiased PMF:*  
```{python}
print(pmf_num.Mean()) 
```
Answer: 1.024  

*Mean of the Biased PMF:*  
```{python}
print(biased_pmf_num.Mean())  
```
Answer: 2.404  

Images:  
![](Images/Ex3.1%20Image%201.png) 
![](Images/Ex3.1%20Image%202.png) 

