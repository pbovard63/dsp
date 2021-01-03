[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

# Question:  
Using data from the NSFG, make a scatter plot of birth weight versus mother’s age. Plot percentiles of birth  
weight versus mother’s age. Compute Pearson’s and Spearman’s correlations. How would you characterize the  
relationship between these variables?  

# My Answer:  
Introductory:  
```{python}
import first
live, firsts, others = first.MakeFrames()
live = live.dropna(subset=['agepreg', 'totalwgt_lb'])
'''
Scoping out the data as a refresher:
```{python}
#Scoping data to refresh how it looks
live.head()
```
Setting variables for mother's age and Birth weight in lb.  Finding max and min values to set axis appropriately  
in scatter plot.  
```{python}
#Setting variables for mother's age and Birth weight in lb.  Finding max and min values to set
#axis appropriately in scatter plot.
mothers_age = live.agepreg
birth_wgt = live.totalwgt_lb
print(mothers_age.min(), mothers_age.max())
print(birth_wgt.min(), birth_wgt.max())
```
*Output:*
10.83 44.08  
0.125 15.4375  
  
Initial Scatter Plot for age and weight:  
```{python}
#Initial Scatter Plot for age and weight:
thinkplot.Scatter(mothers_age, birth_wgt, alpha=0.2, s=10)
thinkplot.Config(xlabel='Mothers Age (years)',
                 ylabel='Birth weight (lb)',
                 axis=[10, 50, 0, 20],
                 legend=False)
```
Output:  
![](Images/Ch7%20E1/Ch7E1%20Scatter.png)  
Based on this image, the scatter plot shows a possible slight positive relationship between age and birth  
weight, although it is not strong.


Plotting percentiles of birth weight versus mother's age:  
```{python}
#Plotting Percentiles of Birth Weight Versus Mothers Age 
bins = np.arange(10, 50, 2)
indices = np.digitize(live.agepreg, bins)
groups = live.groupby(indices)

for i, group in groups:
    print(i, len(group))
```
Computing the CDF:  
```{python}
#Computing CDF:
mean_ages = [group.agepreg.mean() for i, group in groups][1:-1]
cdfs = [thinkstats2.Cdf(group.totalwgt_lb) for i, group in groups][1:-1]
```
Plotting:
```{python}
thinkplot.PrePlot(3)
for percent in [75, 50, 25]:
    weight_percentiles = [cdf.Percentile(percent) for cdf in cdfs]
    label = '%dth' % percent
    thinkplot.Plot(mean_ages, weight_percentiles, label=label)
    
thinkplot.Config(xlabel='Mothers Age (years)',
                 ylabel='Birth weight (lb)',
                 xlim = [10,50],
                 legend=True)
```
Output Plot:  
![](Images/Ch7%20E1/Ch7E1_CDFPlot.png)  

Computing the Coefficients:
```{python}
SpearmanCorr(mothers_age, birth_wgt)
Corr(mothers_age, birth_wgt)
```
Outputs: 
Spearman: 0.09461004109658226  
Corr: 0.06883397035410908  
Both correlations are relatively low, showing a weak relationship.

