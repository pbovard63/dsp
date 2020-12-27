[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

## Code:  

**Calculating the Means:**  
first_wgt_mean = firsts.totalwgt_lb.mean()  
others_wgt_mean = others.totalwgt_lb.mean()  
first_wgt_mean, others_wgt_mean  
Output: 7.201 (first_wgt_mean), 7.326 (other_wgt_mean)  

**Calculating the Cohen Size Effect for means:**  
CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)  
Output: -0.0887  

**Calculating the Cohen Size Effect for Pregnancy Lengths to Compare:**  
CohenEffectSize(firsts.prglngth,others.prglngth)  
Output: 0.0289  

The Cohen Effect Size of the difference between first babies' and other babies' weight is larger than the effect on pregnancy length by about 4x (-0.089 vs 0.0289).  
Additionally, the first babies tend to weighh slightly less (0.12 lb, approx) as compared to other babies (7.20 lb vs. 7.33 lb).  
