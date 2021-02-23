# Weather-Data-Analysis
https://drive.google.com/file/d/1JvD4Ss2yS3d9X36YkWqmqZXLamNWLSFJ/view
Weather Data Analysis
import pandas as pd
data = pd.read_csv(r"C:\Users\pallavi\Desktop\DSBA\Project1. Weather Data.csv")
data.shape
(8784, 8)
data.head()
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa	Weather
0	01-01-2012 00:00	-1.8	-3.9	86	4	8.0	101.24	Fog
1	01-01-2012 01:00	-1.8	-3.7	87	4	8.0	101.24	Fog
2	01-01-2012 02:00	-1.8	-3.4	89	7	4.0	101.26	Freezing Drizzle,Fog
3	01-01-2012 03:00	-1.5	-3.2	88	6	4.0	101.27	Freezing Drizzle,Fog
4	01-01-2012 04:00	-1.5	-3.3	88	7	4.8	101.23	Fog
Find all the unique windspeed values in the data
data['Wind Speed_km/h'].nunique()
34
data.nunique()
Date/Time           8784
Temp_C               533
Dew Point Temp_C     489
Rel Hum_%             83
Wind Speed_km/h       34
Visibility_km         24
Press_kPa            518
Weather               50
dtype: int64
Find the number of times when the windspeed is exactly 4 km/hr
data[data['Wind Speed_km/h'] == 4]
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa	Weather
0	01-01-2012 00:00	-1.8	-3.9	86	4	8.0	101.24	Fog
1	01-01-2012 01:00	-1.8	-3.7	87	4	8.0	101.24	Fog
96	01-05-2012 00:00	-8.8	-11.7	79	4	9.7	100.32	Snow
101	01-05-2012 05:00	-7.0	-9.5	82	4	4.0	100.19	Snow
146	01-07-2012 02:00	-8.1	-11.1	79	4	19.3	100.15	Cloudy
...	...	...	...	...	...	...	...	...
8768	12/31/2012 8:00	-8.6	-10.3	87	4	3.2	101.14	Snow Showers
8769	12/31/2012 9:00	-8.1	-9.6	89	4	2.4	101.09	Snow
8770	12/31/2012 10:00	-7.4	-8.9	89	4	6.4	101.05	Snow,Fog
8772	12/31/2012 12:00	-5.8	-7.5	88	4	12.9	100.78	Snow
8773	12/31/2012 13:00	-4.6	-6.6	86	4	12.9	100.63	Snow
474 rows × 8 columns

Find all the null values in the data
data.isnull().sum()
Date/Time           0
Temp_C              0
Dew Point Temp_C    0
Rel Hum_%           0
Wind Speed_km/h     0
Visibility_km       0
Press_kPa           0
Weather             0
dtype: int64
Rename column Weather to Weather condition
data.rename(columns = {'Weather' : 'Weather Condition'})
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa	Weather Condition
0	01-01-2012 00:00	-1.8	-3.9	86	4	8.0	101.24	Fog
1	01-01-2012 01:00	-1.8	-3.7	87	4	8.0	101.24	Fog
2	01-01-2012 02:00	-1.8	-3.4	89	7	4.0	101.26	Freezing Drizzle,Fog
3	01-01-2012 03:00	-1.5	-3.2	88	6	4.0	101.27	Freezing Drizzle,Fog
4	01-01-2012 04:00	-1.5	-3.3	88	7	4.8	101.23	Fog
...	...	...	...	...	...	...	...	...
8779	12/31/2012 19:00	0.1	-2.7	81	30	9.7	100.13	Snow
8780	12/31/2012 20:00	0.2	-2.4	83	24	9.7	100.03	Snow
8781	12/31/2012 21:00	-0.5	-1.5	93	28	4.8	99.95	Snow
8782	12/31/2012 22:00	-0.2	-1.8	89	28	9.7	99.91	Snow
8783	12/31/2012 23:00	0.0	-2.1	86	30	11.3	99.89	Snow
8784 rows × 8 columns

What is the mean visibility?
data.Visibility_km.mean()
27.66444672131151
What is the Standard Deviation of Pressure?
data.Press_kPa.std()
0.8440047459486474
What is the varience of relative humidity?
data['Rel Hum_%'].var()
286.2485501984998
Find all the instances when the Snow was recorded.
data[data.Weather == "Snow"]
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa	Weather
55	01-03-2012 07:00	-14.0	-19.5	63	19	25.0	100.95	Snow
84	01-04-2012 12:00	-13.7	-21.7	51	11	24.1	101.25	Snow
86	01-04-2012 14:00	-11.3	-19.0	53	7	19.3	100.97	Snow
87	01-04-2012 15:00	-10.2	-16.3	61	11	9.7	100.89	Snow
88	01-04-2012 16:00	-9.4	-15.5	61	13	19.3	100.79	Snow
...	...	...	...	...	...	...	...	...
8779	12/31/2012 19:00	0.1	-2.7	81	30	9.7	100.13	Snow
8780	12/31/2012 20:00	0.2	-2.4	83	24	9.7	100.03	Snow
8781	12/31/2012 21:00	-0.5	-1.5	93	28	4.8	99.95	Snow
8782	12/31/2012 22:00	-0.2	-1.8	89	28	9.7	99.91	Snow
8783	12/31/2012 23:00	0.0	-2.1	86	30	11.3	99.89	Snow
390 rows × 8 columns

Find all the instances when the wind speed is above 24 and the visibility is equal to 25.
data[(data['Wind Speed_km/h'] > 24) & (data.Visibility_km == 25)]
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa	Weather
23	01-01-2012 23:00	5.3	2.0	79	30	25.0	99.31	Cloudy
24	01-02-2012 00:00	5.2	1.5	77	35	25.0	99.26	Rain Showers
25	01-02-2012 01:00	4.6	0.0	72	39	25.0	99.26	Cloudy
26	01-02-2012 02:00	3.9	-0.9	71	32	25.0	99.26	Mostly Cloudy
27	01-02-2012 03:00	3.7	-1.5	69	33	25.0	99.30	Mostly Cloudy
...	...	...	...	...	...	...	...	...
8705	12/28/2012 17:00	-8.6	-12.0	76	26	25.0	101.34	Mainly Clear
8753	12/30/2012 17:00	-12.1	-15.8	74	28	25.0	101.26	Mainly Clear
8755	12/30/2012 19:00	-13.4	-16.5	77	26	25.0	101.47	Mainly Clear
8759	12/30/2012 23:00	-12.1	-15.1	78	28	25.0	101.52	Mostly Cloudy
8760	12/31/2012 0:00	-11.1	-14.4	77	26	25.0	101.51	Cloudy
308 rows × 8 columns

What is the mean value of each column against each weather condition?
data.groupby('Weather').mean()
Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa
Weather						
Clear	6.825716	0.089367	64.497738	10.557315	30.153243	101.587443
Cloudy	7.970544	2.375810	69.592593	16.127315	26.625752	100.911441
Drizzle	7.353659	5.504878	88.243902	16.097561	17.931707	100.435366
Drizzle,Fog	8.067500	7.033750	93.275000	11.862500	5.257500	100.786625
Drizzle,Ice Pellets,Fog	0.400000	-0.700000	92.000000	20.000000	4.000000	100.790000
Drizzle,Snow	1.050000	0.150000	93.500000	14.000000	10.500000	100.890000
Drizzle,Snow,Fog	0.693333	0.120000	95.866667	15.533333	5.513333	99.281333
Fog	4.303333	3.159333	92.286667	7.946667	6.248000	101.184067
Freezing Drizzle	-5.657143	-8.000000	83.571429	16.571429	9.200000	100.202857
Freezing Drizzle,Fog	-2.533333	-4.183333	88.500000	17.000000	5.266667	100.441667
Freezing Drizzle,Haze	-5.433333	-8.000000	82.000000	10.333333	2.666667	100.316667
Freezing Drizzle,Snow	-5.109091	-7.072727	86.090909	16.272727	5.872727	100.520909
Freezing Fog	-7.575000	-9.250000	87.750000	4.750000	0.650000	102.320000
Freezing Rain	-3.885714	-6.078571	84.642857	19.214286	8.242857	99.647143
Freezing Rain,Fog	-2.225000	-3.750000	89.500000	15.500000	7.550000	99.945000
Freezing Rain,Haze	-4.900000	-7.450000	82.500000	7.500000	2.400000	100.375000
Freezing Rain,Ice Pellets,Fog	-2.600000	-3.700000	92.000000	28.000000	8.000000	100.950000
Freezing Rain,Snow Grains	-5.000000	-7.300000	84.000000	32.000000	4.800000	98.560000
Haze	-0.200000	-2.975000	81.625000	10.437500	7.831250	101.482500
Mainly Clear	12.558927	4.581671	60.667142	14.144824	34.264862	101.248832
Moderate Rain,Fog	1.700000	0.800000	94.000000	17.000000	6.400000	99.980000
Moderate Snow	-5.525000	-7.250000	87.750000	33.750000	0.750000	100.275000
Moderate Snow,Blowing Snow	-5.450000	-6.500000	92.500000	40.000000	0.600000	100.570000
Mostly Cloudy	10.574287	3.131174	62.102465	15.813920	31.253842	101.025288
Rain	9.786275	7.042810	83.624183	19.254902	18.856536	100.233333
Rain Showers	13.722340	9.187766	75.159574	17.132979	22.816489	100.404043
Rain Showers,Fog	12.800000	12.100000	96.000000	13.000000	6.400000	99.830000
Rain Showers,Snow Showers	2.150000	-1.500000	76.500000	22.500000	21.700000	101.100000
Rain,Fog	8.273276	7.219828	93.189655	14.793103	6.873276	100.500862
Rain,Haze	4.633333	2.066667	83.333333	11.666667	6.700000	100.540000
Rain,Ice Pellets	0.600000	-0.600000	92.000000	24.000000	9.700000	100.120000
Rain,Snow	1.055556	-0.566667	89.000000	28.388889	11.672222	99.951111
Rain,Snow Grains	1.900000	-2.100000	75.000000	26.000000	25.000000	100.600000
Rain,Snow,Fog	0.800000	0.300000	96.000000	9.000000	6.400000	100.730000
Rain,Snow,Ice Pellets	1.100000	-0.175000	91.500000	23.250000	6.000000	100.105000
Snow	-4.524103	-7.623333	79.307692	20.038462	11.171795	100.536103
Snow Pellets	0.700000	-6.400000	59.000000	35.000000	2.400000	99.700000
Snow Showers	-3.506667	-7.866667	72.350000	19.233333	20.158333	100.963500
Snow Showers,Fog	-10.675000	-11.900000	90.750000	13.750000	7.025000	101.292500
Snow,Blowing Snow	-5.410526	-7.621053	84.473684	34.842105	4.105263	99.704737
Snow,Fog	-5.075676	-6.364865	90.675676	17.324324	4.537838	100.688649
Snow,Haze	-4.020000	-6.860000	80.600000	5.000000	4.640000	100.782000
Snow,Ice Pellets	-1.883333	-3.666667	87.666667	23.833333	7.416667	100.548333
Thunderstorms	24.150000	19.750000	77.000000	7.500000	24.550000	100.230000
Thunderstorms,Heavy Rain Showers	10.900000	9.000000	88.000000	9.000000	2.400000	100.260000
Thunderstorms,Moderate Rain Showers,Fog	19.600000	18.500000	93.000000	15.000000	3.200000	100.010000
Thunderstorms,Rain	20.433333	18.533333	89.000000	15.666667	19.833333	100.420000
Thunderstorms,Rain Showers	20.037500	17.618750	86.375000	18.312500	15.893750	100.233750
Thunderstorms,Rain Showers,Fog	21.600000	18.700000	84.000000	19.666667	9.700000	100.063333
Thunderstorms,Rain,Fog	20.600000	18.600000	88.000000	19.000000	4.800000	100.080000
What is the maximum value against each Weather?
data.groupby('Weather').max()
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa
Weather							
Clear	9/28/2012 4:00	32.8	20.4	99	33	48.3	103.63
Cloudy	9/30/2012 9:00	30.5	22.6	99	54	48.3	103.65
Drizzle	9/30/2012 3:00	18.8	17.7	96	30	25.0	101.56
Drizzle,Fog	9/30/2012 2:00	19.9	19.1	100	28	9.7	102.07
Drizzle,Ice Pellets,Fog	12/17/2012 9:00	0.4	-0.7	92	20	4.0	100.79
Drizzle,Snow	12/19/2012 18:00	1.2	0.2	95	19	11.3	101.15
Drizzle,Snow,Fog	12/22/2012 3:00	1.1	0.6	98	32	9.7	100.15
Fog	9/22/2012 0:00	20.8	19.6	100	22	9.7	103.04
Freezing Drizzle	12/17/2012 0:00	-2.3	-3.3	93	26	12.9	101.02
Freezing Drizzle,Fog	12-10-2012 05:00	-0.3	-2.3	94	33	8.0	101.27
Freezing Drizzle,Haze	02-01-2012 13:00	-5.0	-7.7	83	11	4.0	100.36
Freezing Drizzle,Snow	12/28/2012 2:00	-3.3	-4.6	94	24	12.9	101.18
Freezing Fog	3/17/2012 6:00	-0.1	-0.3	99	9	0.8	102.85
Freezing Rain	12/17/2012 2:00	0.3	-1.7	92	28	16.1	101.00
Freezing Rain,Fog	12/17/2012 1:00	0.1	-0.9	93	26	9.7	101.01
Freezing Rain,Haze	02-01-2012 15:00	-4.9	-7.4	83	9	2.8	100.41
Freezing Rain,Ice Pellets,Fog	12/17/2012 3:00	-2.6	-3.7	92	28	8.0	100.95
Freezing Rain,Snow Grains	1/13/2012 9:00	-5.0	-7.3	84	32	4.8	98.56
Haze	3/13/2012 23:00	14.1	11.1	86	17	9.7	102.97
Mainly Clear	9/28/2012 8:00	33.0	21.2	99	63	48.3	103.59
Moderate Rain,Fog	12-10-2012 08:00	1.7	0.8	94	17	6.4	99.98
Moderate Snow	12/27/2012 9:00	-4.9	-6.7	93	39	0.8	100.67
Moderate Snow,Blowing Snow	12/27/2012 12:00	-5.4	-6.4	93	41	0.6	100.64
Mostly Cloudy	9/29/2012 9:00	32.4	24.4	100	83	48.3	103.65
Rain	9/30/2012 22:00	22.8	20.4	99	52	48.3	102.26
Rain Showers	9/26/2012 16:00	26.4	23.0	97	41	48.3	102.31
Rain Showers,Fog	10/20/2012 3:00	12.8	12.1	96	13	6.4	99.83
Rain Showers,Snow Showers	12-05-2012 10:00	2.2	-1.2	78	28	24.1	101.11
Rain,Fog	9/30/2012 23:00	21.7	19.5	100	46	9.7	101.77
Rain,Haze	3/13/2012 9:00	5.5	2.9	86	17	9.7	100.61
Rain,Ice Pellets	12/18/2012 5:00	0.6	-0.6	92	24	9.7	100.12
Rain,Snow	4/23/2012 3:00	1.7	0.5	94	52	25.0	101.07
Rain,Snow Grains	12/21/2012 0:00	1.9	-2.1	75	26	25.0	100.60
Rain,Snow,Fog	12-08-2012 21:00	0.8	0.3	96	9	6.4	100.73
Rain,Snow,Ice Pellets	12/21/2012 5:00	1.3	0.1	94	28	6.4	100.47
Snow	4/27/2012 9:00	3.7	0.3	96	57	25.0	102.73
Snow Pellets	11/24/2012 15:00	0.7	-6.4	59	35	2.4	99.70
Snow Showers	2/23/2012 13:00	2.9	-0.7	94	37	48.3	102.50
Snow Showers,Fog	12/29/2012 13:00	-10.0	-11.1	92	22	9.7	102.52
Snow,Blowing Snow	2/25/2012 9:00	-1.4	-2.9	91	48	9.7	100.62
Snow,Fog	3/14/2012 19:00	1.1	0.8	99	35	9.7	102.07
Snow,Haze	02-01-2012 21:00	-3.6	-6.4	81	15	6.4	100.99
Snow,Ice Pellets	3/28/2012 8:00	0.8	-1.7	92	33	11.3	100.96
Thunderstorms	7/16/2012 1:00	26.7	20.1	87	15	25.0	100.62
Thunderstorms,Heavy Rain Showers	5/29/2012 6:00	10.9	9.0	88	9	2.4	100.26
Thunderstorms,Moderate Rain Showers,Fog	7/17/2012 6:00	19.6	18.5	93	15	3.2	100.01
Thunderstorms,Rain	7/23/2012 18:00	21.3	19.1	93	30	24.1	100.83
Thunderstorms,Rain Showers	9/14/2012 20:00	25.5	23.1	98	32	25.0	101.06
Thunderstorms,Rain Showers,Fog	7/31/2012 20:00	22.9	21.3	91	35	9.7	100.64
Thunderstorms,Rain,Fog	7/17/2012 5:00	20.6	18.6	88	19	4.8	100.08
Show all the records weather is Fog.
data[data.Weather == "Fog"]
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa	Weather
0	01-01-2012 00:00	-1.8	-3.9	86	4	8.0	101.24	Fog
1	01-01-2012 01:00	-1.8	-3.7	87	4	8.0	101.24	Fog
4	01-01-2012 04:00	-1.5	-3.3	88	7	4.8	101.23	Fog
5	01-01-2012 05:00	-1.4	-3.3	87	9	6.4	101.27	Fog
6	01-01-2012 06:00	-1.5	-3.1	89	7	6.4	101.29	Fog
...	...	...	...	...	...	...	...	...
8716	12/29/2012 4:00	-16.0	-17.2	90	6	9.7	101.25	Fog
8717	12/29/2012 5:00	-14.8	-15.9	91	4	6.4	101.25	Fog
8718	12/29/2012 6:00	-13.8	-15.3	88	4	9.7	101.25	Fog
8719	12/29/2012 7:00	-14.8	-16.4	88	7	8.0	101.22	Fog
8722	12/29/2012 10:00	-12.0	-13.3	90	7	6.4	101.15	Fog
150 rows × 8 columns

Find all the instances when weather is clear or visibility is above 40.
data[(data.Weather == "Clear") | (data.Visibility_km > 40)]
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa	Weather
67	01-03-2012 19:00	-16.9	-24.8	50	24	25.0	101.74	Clear
106	01-05-2012 10:00	-6.0	-10.0	73	17	48.3	100.45	Mainly Clear
107	01-05-2012 11:00	-5.6	-10.2	70	22	48.3	100.41	Mainly Clear
108	01-05-2012 12:00	-4.7	-9.6	69	20	48.3	100.38	Mainly Clear
109	01-05-2012 13:00	-4.4	-9.7	66	26	48.3	100.40	Mainly Clear
...	...	...	...	...	...	...	...	...
8749	12/30/2012 13:00	-12.4	-16.2	73	37	48.3	100.92	Mostly Cloudy
8750	12/30/2012 14:00	-11.8	-16.1	70	37	48.3	100.96	Mainly Clear
8751	12/30/2012 15:00	-11.3	-15.6	70	32	48.3	101.05	Mainly Clear
8752	12/30/2012 16:00	-11.4	-15.5	72	26	48.3	101.15	Mainly Clear
8756	12/30/2012 20:00	-13.8	-16.5	80	24	25.0	101.52	Clear
3027 rows × 8 columns

Find all the instances weather is clear and relative humidity is greater than 50 or visibility is above 40.
data[(data.Weather == "Clear") & (data['Rel Hum_%'] > 50) | (data.Visibility_km > 40)]
Date/Time	Temp_C	Dew Point Temp_C	Rel Hum_%	Wind Speed_km/h	Visibility_km	Press_kPa	Weather
106	01-05-2012 10:00	-6.0	-10.0	73	17	48.3	100.45	Mainly Clear
107	01-05-2012 11:00	-5.6	-10.2	70	22	48.3	100.41	Mainly Clear
108	01-05-2012 12:00	-4.7	-9.6	69	20	48.3	100.38	Mainly Clear
109	01-05-2012 13:00	-4.4	-9.7	66	26	48.3	100.40	Mainly Clear
110	01-05-2012 14:00	-5.1	-10.7	65	22	48.3	100.46	Mainly Clear
...	...	...	...	...	...	...	...	...
8749	12/30/2012 13:00	-12.4	-16.2	73	37	48.3	100.92	Mostly Cloudy
8750	12/30/2012 14:00	-11.8	-16.1	70	37	48.3	100.96	Mainly Clear
8751	12/30/2012 15:00	-11.3	-15.6	70	32	48.3	101.05	Mainly Clear
8752	12/30/2012 16:00	-11.4	-15.5	72	26	48.3	101.15	Mainly Clear
8756	12/30/2012 20:00	-13.8	-16.5	80	24	25.0	101.52	Clear
2921 rows × 8 columns

