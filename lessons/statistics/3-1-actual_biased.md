[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

### Answer Part 1: Running the below will plot the actual and biased distributions of number of children in household.

```bash
df_respondents = nsfg.ReadFemResp()

actual_numkdhh_pmf = thinkstats2.Pmf(df_respondents.numkdhh, label='Acutal # kids in household')

def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)
    for x, p in pmf.Items():
        new_pmf.Mult(x,x)
    new_pmf.Normalize()
    return new_pmf

# plots the actual and biased distributions
biased_numkdhh_pmf = BiasPmf(biased_numkdhh_pmf, label='Biased # kids in household')
thinkplot.PrePlot(2)
thinkplot.Pmfs([actual_numkdhh_pmf, biased_numkdhh_pmf])
thinkplot.Show(xlabel='Number Kids', ylabel='PMF')
