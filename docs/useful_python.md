# Useful python code



## pandas datetime indexing and filtering

```python
df_2013 = df[df.index.year == 2013]
```

**Month:** `df[df.index.month == 1]` (January)

**Day:** `df[df.index.day == 15]`

**Hour:** `df[df.index.hour == 9]`

**Specific date:** `df[df.index == '2013-04-01']`

**Date ranges:** `df['2013-01-01':'2013-06-30']` (using string slicing)

 #### Resampling datetime data

`df_hourly = df.resample('H').mean()`

`df_daily = df.resample('D').mean() `

**`.sum()`:**  Sum the values.

**`.max()`:** Take the maximum value.

**`.min()`:** Take the minimum value.

**`.first()`:** Take the first value within the hour.

**`.last()`:** Take the last value within the hour.

**`.ohlc()`:**  Get the open, high, low, and close values for each hour (useful for financial data).

Suppose I wanted means but only for 

````python
# Create a boolean mask for hours between 6 am and 8 pm inclusive
mask = (df.index.hour >= 6) & (df.index.hour <= 20)

# Apply the mask to the dataframe
df_filtered = df[mask]

# Resample to daily frequency and calculate the mean
df_daily_filtered = df_filtered.resample('D').mean()

# Display the first 5 rows
print(df_daily_filtered.head().to_markdown(index=True, numalign="left", stralign="left"))

# Print the column names and their data types
print(df_daily_filtered.info())
```
````



### Conditional and unconditional expectations using numpy and scipy

```python
import scipy.stats as stats

# Example: Normal distribution with mean 5 and standard deviation 2
dist = stats.norm(loc=5, scale=2) 

expectation = dist.expect()

```

What about unconditional expectation of a function under the distribution

```python
import scipy.stats as stats

# Normal distribution with mean 0 and standard deviation 1
dist = stats.norm(loc=0, scale=1)

# Function to calculate X^2
def x_squared(x):
    return x**2

# Calculate E[X^2]
expectation_x_squared = dist.expect(func=x_squared)
print(expectation_x_squared)  # Output: 1.0 (variance of the standard normal distribution)
```



#### Conditional expectation

```python
import scipy.stats as stats
import numpy as np

# Define the distribution (example: normal distribution)
dist = stats.norm(loc=5, scale=2)  # Mean 5, standard deviation 2

# Define xLO
xLO = 3

# Define the function 
def func(x):
    return 100 - x

# Calculate the conditional expectation E[100 - x | x < xLO]
conditional_expectation = dist.expect(func=func, lb=-np.inf, ub=xLO)

print(conditional_expectation)
```

