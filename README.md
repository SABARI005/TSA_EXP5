### Developed By: SABARI S
### Register No: 212222240085
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on the Air quality dataset.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


df = pd.read_csv('/content/data_date.csv') 

print(df.head())

df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)

air_data = df['AQI Value']

new_index = pd.date_range(start=air_data.index.min(), periods=len(air_data), freq='B')[:len(air_data)]
air_data.index = new_index

decomposition = seasonal_decompose(air_data, model='additive', period=30) 

trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

plt.figure(figsize=(12, 6))
plt.plot(air_data, label=' Air Quality')
plt.title(' Air Quality')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal Component', color='orange')
plt.title('Seasonal Component')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend Component', color='green')
plt.title('Trend Component')
plt.legend()
plt.show()

plt.plot(residuals, label='Residuals', color='red')
plt.legend(loc='best')
plt.tight_layout()
plt.show()
```

### OUTPUT:
FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/2dbdf8f5-e816-4ffd-a505-cc9151e72af3)


PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/176088b0-44ab-462b-bd94-2aab35142834)



SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/3b46a6a7-4b01-419d-937c-6765d441abc3)


TREND PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/ba57ecc9-be32-4a64-82fb-99dd4a53a8e5)



OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/7cec75a7-7534-436f-9eb3-9135f748afde)




### RESULT:
Thus  the python code for the time series analysis and decomposition is executed sucessfully.
