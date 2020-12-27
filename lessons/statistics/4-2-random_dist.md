[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

## Exercise 2 from Ch. 4 Code:  

**Generating the 1000 random values:**  
rands = np.random.random(1000)  
len(rands)  
Output = 1000  

**Plotting the PMF:**  
rands_pmf = thinkstats2.Pmf(rands)  
thinkplot.Pmf(rands_pmf, label = 'Random Values')  
thinkplot.Config(xlabel='Random Values: 0-1', ylabel='PMF')  
What goes wrong? --> Can't tell the difference between any values, it's so close together  

**Plotting the CDF:**  
rands_cdf = thinkstats2.Cdf(rands)  
thinkplot.Cdf(rands_cdf, label = 'Random Values - CDF')  
thinkplot.Config(xlabel='Random Values: 0-1', ylabel='CDF')  
Is this distribution uniform? Yes, as the CDF is a straight line.  
