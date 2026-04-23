# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 21/04/2026

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv("gold_price.csv")
data.head()
data['Date']=pd.to_datetime(data['Date'])
data.set_index('Date',inplace=True)
data['GLD_diff']=data['GLD']-data['GLD'].shift(1)
result=seasonal_decompose(data['GLD_diff'].dropna(),model='additive',period=12)
data['GLD_sea_diff']=result.resid
data['GLD_log']=np.log(data['GLD'])
data['GLD_log_diff']=data['GLD_log']-data['GLD_log'].shift(1)
result=seasonal_decompose(data['GLD_log_diff'].dropna(),model='additive',period=12)
data['GLD_log_seasonal_diff']=result.resid
plt.figure(figsize=(16,16))
plt.subplot(6,1,1)
plt.plot(data['GLD'],label='Original')
plt.legend(loc='best')
plt.title('Original Data')
plt.xlabel('Date')
plt.ylabel('GLD')
plt.subplot(6,1,2)
plt.plot(data['GLD_diff'],label='Regular Difference')
plt.legend(loc='best')
plt.title('Regular Differencing')
plt.xlabel('Date')
plt.ylabel('Differenced GLD')
plt.subplot(6,1,3)
plt.plot(data['GLD_sea_diff'],label='Seasonal Adjustment')
plt.legend(loc='best')
plt.title('Seasonal Adjustment')
plt.xlabel('Date')
plt.ylabel('Seasonally Adjusted GLD')
plt.subplot(6,1,4)
plt.plot(data['GLD_log'],label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')
plt.xlabel('Date')
plt.ylabel('log(GLD)')
plt.subplot(6,1,5)
plt.plot(data['GLD_log_diff'],label='Log Transformation and Regular Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regualr Differencing')
plt.xlabel('Date')
plt.ylabel('RDiff(GLD)')
plt.subplot(6,1,6)
plt.plot(data['GLD_log_seasonal_diff'],label='Log Transformation and regualr Differencing and Seasonal Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and regualr Differencing and Seasonal Differencing')
plt.xlabel('Date')
plt.ylabel('SDiff(RDiff(GLD))')
plt.tight_layout()
plt.show()
data.plot(kind='line')
```

### OUTPUT:


REGULAR DIFFERENCING:
<img width="1663" height="549" alt="image" src="https://github.com/user-attachments/assets/025e1929-67f9-45ac-9b29-214ecd63d149" />

SEASONAL ADJUSTMENT:
<img width="1669" height="282" alt="image" src="https://github.com/user-attachments/assets/17ab00c3-4bb2-4963-b3ec-2025cd789f5e" />

LOG TRANSFORMATION:
<img width="1723" height="275" alt="image" src="https://github.com/user-attachments/assets/9adbda8c-eceb-4706-b043-28e400f4940d" />

LOG TRANSFORMATION AND REGULAR DIFFERENCING:
<img width="1679" height="277" alt="image" src="https://github.com/user-attachments/assets/567c4eb9-5cdb-4fc8-a4b5-0124639ba186" />

LOG TRANSFORMATION AND REGULAR DIFFERENCING AND SEASONAL DIFFERENCING:
<img width="1672" height="279" alt="image" src="https://github.com/user-attachments/assets/012d74bf-7641-4e55-8727-a86dc60179fe" />

<img width="806" height="555" alt="image" src="https://github.com/user-attachments/assets/d992a244-8ebf-4fbf-96e5-9eb2e4ca757e" />

### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
