[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

## Exercise 3.1: Code:  
resp = nsfg.ReadFemResp(). 
*Standard Histogram:*. 
hist_num = thinkstats2.Hist(resp.numkdhh, label='Children per Household'). 
thinkplot.Hist(hist_num). 
thinkplot.Config(xlabel='Number of Children per Household', ylabel='Count'). 

*Standard PMF:*. 
pmf_num = thinkstats2.Pmf(resp.numkdhh, label='Children per Household - Unbiased'). 
thinkplot.Pmf(pmf_num). 
thinkplot.Config(xlabel='Number of Children per Household', ylabel='Count'). 

*Biased PMF:*. 
biased_pmf_num = BiasPmf(pmf_num, label='Biased'). 
thinkplot.PrePlot(2). 
thinkplot.Pmfs([pmf_num, biased_pmf_num]). 
thinkplot.Config(xlabel='Children Per Household', ylabel='PMF'). 

*Mean of Unbiased PMF:*. 
print(pmf_num.Mean()). 
Answer: 1.024. 

*Mean of the Biased PMF:*. 
print(biased_pmf_num.Mean()). 
Answer: 2.404. 

