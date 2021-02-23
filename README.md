# Weather-Data-Analysis
https://drive.google.com/file/d/1JvD4Ss2yS3d9X36YkWqmqZXLamNWLSFJ/view
# Weather Data Analysis

import pandas as pd

data = pd.read_csv(r"C:\Users\pallavi\Desktop\DSBA\Project1. Weather Data.csv")

data.shape

data.head()

# Find all the unique windspeed values in the data

data['Wind Speed_km/h'].nunique()

data.nunique()

# Find the number of times when the windspeed is exactly 4 km/hr

data[data['Wind Speed_km/h'] == 4]

# Find all the null values in the data

data.isnull().sum()

# Rename column Weather to Weather condition

data.rename(columns = {'Weather' : 'Weather Condition'})

# What is the mean visibility?

data.Visibility_km.mean()

# What is the Standard Deviation of Pressure?

data.Press_kPa.std()

# What is the varience of relative humidity?

data['Rel Hum_%'].var()

# Find all the instances when the Snow was recorded.

data[data.Weather == "Snow"]

# Find all the instances when the wind speed is above 24 and the visibility is equal to 25.

data[(data['Wind Speed_km/h'] > 24) & (data.Visibility_km == 25)]

# What is the mean value of each column against each weather condition?

data.groupby('Weather').mean()

# What is the maximum value against each Weather?

data.groupby('Weather').max()

# Show all the records weather is Fog.

data[data.Weather == "Fog"]

# Find all the instances when weather is clear or visibility is above 40.

data[(data.Weather == "Clear") | (data.Visibility_km > 40)]

# Find all the instances weather is clear and relative humidity is greater than 50 or visibility is above 40.

data[(data.Weather == "Clear") & (data['Rel Hum_%'] > 50) | (data.Visibility_km > 40)]

