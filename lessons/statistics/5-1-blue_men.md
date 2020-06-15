[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

Answer: **34.27%** of men in the US pass the height requirement of the Blue Man group (i.e. are between 5'10" and 6'1").

```bash
dist = scipy.stats.norm(loc=178, scale=7.7)

def imperial_to_cms(feet, inches):
    ft_to_in = feet * 12
    total_in = ft_to_in + inches
    cms = total_in * 2.54
    return cms
    
low = dist.cdf(imperial_to_cms(5,10))
high = dist.cdf(imperial_to_cms(6,1))

print(f'''{round((high-low)*100,2)}% of men in \
the US pass the height requirement of the Blue \
Man group (i.e. are between 5'10" and 6'1").
''')
```

