# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 02-09-2025

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
```
```
data1=pd.read_csv("/content/plane_crash.csv")
```
```
data1.head(10)
```
```
data1["Fatalities"] = data1["Fatalities"].fillna(0).astype(int)
```
```
data=data1["Fatalities"]
```
```
N=len(data)
```
```
lags = range(35)
```
```
autocorr_values = []
```
```
mean_data = np.mean(data)
```
```
variance_data = np.var(data)
```
```
normalized_data = (data - mean_data) / np.sqrt(variance_data)
```
```
for lag in lags:
  if lag == 0:
    autocorr_values.append(1)
  else:
    auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
    autocorr_values.append(auto_cov / variance_data)
```
```
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```


### OUTPUT:
<img width="991" height="616" alt="image" src="https://github.com/user-attachments/assets/d3a7438f-74cb-43c5-a99e-57232cc0b7d8" />

### RESULT:
Thus we have successfully implemented the auto correlation function in python.

