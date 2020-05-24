[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

df_respondents = nsfg.ReadFemResp()

actual_numkdhh_pmf = thinkstats2.Pmf(df_respondents.numkdhh, label='Acutal # kids in household')

def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)
    for x, p in pmf.Items():
        new_pmf.Mult(x,x)
    new_pmf.Normalize()
    return new_pmf
    
# Answer Part 1: Below will plot the actual and biased distributions of number of children in household
biased_numkdhh_pmf = BiasPmf(biased_numkdhh_pmf, label='Biased # kids in household')
thinkplot.PrePlot(2)
thinkplot.Pmfs([actual_numkdhh_pmf, biased_numkdhh_pmf])
thinkplot.Show(xlabel='Number Kids', ylabel='PMF')

# Answer Part 2: below will print the means for actual 
# and biased distributions of number of children in household
print(f'The mean for the actual data for number of kids in household is {actual_numkdhh_pmf.Mean()}')
print(f'The mean for the biased data for number of kids in household is {biased_numkdhh_pmf.Mean()}')
