# PA-4-DE-BORJA

Problem "**ECE BOARD EXAM**"

A.
1. A .csv file named board2 is loaded into a data frame using pandas ```board2.csv```
2. The dataset is filtered to display:
   - Students from Luzon taking Instrumentation with electronics > 70 and,
   - Female students from Mindanao with an average>=55 (created by taking the mean of Math, Electronics, GEAS, and Communication.)

```
Instru = df[(df['Hometown']=='Luzon') & (df['Track']=='Instrumentation') & (df['Electronics']>70)][['Name', 'GEAS','Electronics']]
Instru

df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

Mindy = df[(df['Hometown']=='Mindanao') & 
        (df['Gender']=='Female') &
        (df['Average']>=55)][['Name', 'Track','Electronics', 'Average']]
Mindy
```

B.
- **Visualization using Matplotlib**

Using the dataframe board2 in part A, the average of the four subjects are recalculated and plotted; 
1. ```import matplotlib.pyplot as plt``` is used to import the plotting library.
2. Four subjects are selected to compute the average of Electronics, Math, GEAS, and Communication. ```df['Average'] = df[subs].mean(axis=1)``` computes the mean by row to display a single score when compared with other groups
3. This process is repeated with other categories such as the gender, hometown, and track.
```
gender_avg = df.groupby('Gender')['Average'].mean() 
hometown_avg = df.groupby('Hometown')['Average'].mean()
track_avg = df.groupby('Track')['Average'].mean()
```
4. Figures are created to plot the data, ```plt.figure(figsize=(5,3))```
5. The data is then plotted using ```plt.bar()``` for visual comparison and the axis labeled
6. Lastly, ```.describe()``` is used to generate a comparison of performance across Gender, Track, and Hometown.

