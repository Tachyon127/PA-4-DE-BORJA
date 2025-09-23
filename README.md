# PA-4-DE-BORJA

**ECE BOARD EXAM**

A. This Python script utilizes data wrangling and visualization techniques.
```
import pandas as pd ###imports Panda library
df = pd.read_csv('board2.csv') ###Loads the board2.csv file
df
```
A variable Instru is utilized to have a dataframe where values such as Track is set to 'Instrumentation', Hometown is set to 'Luzon', and the score in Electronics is greater than 70. The aforementioned values are displayed under columns titled "NAME, GEAS, ELECTRONICS".
```
Instru = df[(df['Hometown']=='Luzon') & (df['Track']=='Instrumentation') & (df['Electronics']>70)][['Name', 'GEAS','Electronics']]
Instru
```
A variable named Mindy utilizes a dataframe with values where the hometown is constant as Mindanao, and the gender is set to female, and the average score greater than or equal to 55. The previous values are under the columns "Name, Track, Electronics, Average"
```
f['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

Mindy = df[(df['Hometown']=='Mindanao') & 
        (df['Gender']=='Female') &
        (df['Average']>=55)][['Name', 'Track','Electronics', 'Average']]
Mindy
```

B. Visualization using Matplotlib
```
import matplotlib.pyplot as plt
```
Utilizing the initial dataframe board2, the average of four subjects (Electronics, Math, GEAS, and Communication) are recalculated and plotted. The syntax ```mean(axis=1)``` indicates that the mean is computed row-wise to display a single score when compared with other groups or categories (Track, Hometown, Gender)
```
subs = ['Electronics', 'Math', 'GEAS', 'Communication'] df['Average'] = df[subs].mean(axis=1)
gender_avg = df.groupby('Gender')['Average'].mean() 
hometown_avg = df.groupby('Hometown')['Average'].mean()
track_avg = df.groupby('Track')['Average'].mean()
```
The figures for data plotting is created, and the data is plotted with labeled axis for visual comparison.
```
###Gender
plt.figure(figsize=(5,3))
gender_avg = df.groupby('Gender')['Average'].mean()
plt.bar(gender_avg.index, gender_avg.values)
plt.xlabel('Gender')
plt.ylabel('Average Score');
###Hometown
plt.figure(figsize=(5,3))
hometown_avg = df.groupby('Hometown')['Average'].mean()
plt.bar(hometown_avg.index, hometown_avg.values)
plt.xlabel('Hometown')
plt.ylabel('Average Score');
###Track
plt.figure(figsize=(5,3))
track_avg = df.groupby('Track')['Average'].mean()
plt.bar(track_avg.index, track_avg.values)
plt.xlabel('Track')
plt.ylabel('Average Score');
```
The performance across gender, track, and hometown, is compared by using the syntax: `.describe()` which displays the count, mean, standard deviation, maxima and minima.
```
df[df['Gender'] == 'Male']['Average'].describe()
df[df['Gender'] == 'Female']['Average'].describe()

df[df['Track'] == 'Instumentation']['Average'].describe()
df[df['Track'] == 'Microelectronics']['Average'].describe()
df[df['Track'] == 'Communication']['Average'].describe()

df[df['Hometown'] == 'Luzon']['Average'].describe()
df[df['Hometown'] == 'Visayas']['Average'].describe()
df[df['Hometown'] == 'Mindanao']['Average'].describe()
```
