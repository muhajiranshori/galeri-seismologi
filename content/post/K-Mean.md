```python
#Importing the required libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.cluster import KMeans
import geopandas as gpd
from descartes import PolygonPatch
%matplotlib inline
from matplotlib.pylab import rcParams
import pygmt


```


```python
#import the required dataset
#df_full = pd.read_csv("Data gempa bumi pulau jawa.csv")
df_full = pd.read_csv("ihsan_baru.csv")
df_full.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>No</th>
      <th>Date</th>
      <th>Epicenter</th>
      <th>Magnitudo</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Depth</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>01/01/2017</td>
      <td>Sukabumi - Jawa  Barat</td>
      <td>4.0</td>
      <td>-8.96</td>
      <td>110.00</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>01/01/2017</td>
      <td>Sukabumi - Jawa  Barat</td>
      <td>3.5</td>
      <td>-9.48</td>
      <td>114.26</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>01/01/2017</td>
      <td>Sukabumi - Jawa  Barat</td>
      <td>3.7</td>
      <td>-7.69</td>
      <td>115.48</td>
      <td>293.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>02/01/2017</td>
      <td>Sukabumi - Jawa  Barat</td>
      <td>3.1</td>
      <td>-6.11</td>
      <td>105.40</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>02/01/2017</td>
      <td>Sukabumi - Jawa  Barat</td>
      <td>3.4</td>
      <td>-7.94</td>
      <td>115.32</td>
      <td>13.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_full['Date'] = pd.to_datetime(df_full['Date'],  errors='coerce')
# only keeping the columns we require
df = df_full[['Latitude','Longitude','Magnitudo']]
df_year = df_full[['Latitude','Longitude','Magnitudo','Date']]
# only keeping earthquake categorized as moderate
df = df[df.Magnitudo >= 3]
df_year = df_year[df_year.Magnitudo >= 3]
len(df_year),len(df)
```




    (5130, 5130)




```python
#Finding the optimal K using the elbow method
Sum_of_squared_distances = []
K = range(1,10)
for k in K:
    km = KMeans(n_clusters=k)
    km = km.fit(df)    
    Sum_of_squared_distances.append(km.inertia_)
```


```python
plt.plot(K, Sum_of_squared_distances, 'rx-')
```




    [<matplotlib.lines.Line2D at 0x7fc444e73050>]




    
![png](K-Mean_files/K-Mean_4_1.png)
    



```python
kmeans = KMeans(n_clusters=2).fit(df)
df['Clusters'] = kmeans.labels_
```


```python
map_1 = gpd.read_file('KB_JATIM.SHP')
```


```python
#find the centroid location
centroid_1, centroid_2 = kmeans.cluster_centers_
centroid_1 = np.delete(centroid_1,2)
centroid_2 = np.delete(centroid_2,2)

```


```python
params={'figure.figsize':(15,12)}
rcParams.update(params)
```


```python
map_1.plot(column = 'NM_PROP')
sns.scatterplot(x=df.Longitude, y=df.Latitude, hue = df.Clusters ,palette='Set1',
                size=df.Magnitudo, sizes=(10,200), 
                    legend = 'brief')
plt.legend(loc=2, bbox_to_anchor=(0.80,1.30))

plt.scatter(centroid_1[1],centroid_1[0],color="yellow")
plt.scatter(centroid_2[1],centroid_2[0],color="yellow")
plt.axis('off')
plt.show()
plt.savefig("earthquake_clusters_1.png", dpi=200)
```


    
![png](K-Mean_files/K-Mean_9_0.png)
    



    <Figure size 1080x864 with 0 Axes>



```python
region = [
    df.Longitude.min() - 1,
    df.Longitude.max() + 1,
    df.Latitude.min() - 1,
    df.Latitude.max() + 1,
]

print(region)
print(data.head())
```

    [103.92, 117.53, -12.98, -4.51]
       year  month  day  latitude  longitude  depth_km  magnitude
    0  1987      1    4     49.77     149.29       489        4.1
    1  1987      1    9     39.90     141.68        67        6.8
    2  1987      1    9     39.82     141.64        84        4.0
    3  1987      1   14     42.56     142.85       102        6.5
    4  1987      1   16     42.79     145.10        54        5.1
    


```python
fig = pygmt.Figure()
fig.basemap(region=region, projection="M8i", frame=True)
fig.coast(land="white", water="skyblue")
fig.plot(x=df.Longitude, y=df.Latitude, style="c0.2c", color="red", pen="black")
fig.show()
```


    
![png](K-Mean_files/K-Mean_11_0.png)
    



```python
fig = pygmt.Figure()
fig.basemap(region=region, projection="M8i", frame=True)
fig.coast(land="white", water="skyblue")
fig.plot(
    x=df.Longitude,
    y=df.Latitude,
    sizes=0.02 * (1.8 ** df.Magnitudo),
    style="cc",
    color="red",
    pen="black",
)
fig.show()
```

    /home/muhajir/miniconda3/envs/ihsan/lib/python3.7/site-packages/ipykernel_launcher.py:10: FutureWarning: The 'sizes' parameter has been deprecated since v0.4.0 and will be removed in v0.6.0. Please use 'size' instead.
      # Remove the CWD from sys.path while we load stuff.
    


    
![png](K-Mean_files/K-Mean_12_1.png)
    



```python
#map_1.plot(column = 'PROPINSI')
sns.scatterplot(x=df.Longitude, y=df.Latitude, hue = df.Clusters ,palette='Set1',
                size=df.Magnitudo, sizes=(10,200), 
                    legend = 'brief')
plt.legend(loc=2, bbox_to_anchor=(0.80,1.30))

plt.scatter(centroid_1[1],centroid_1[0],color="yellow")
plt.scatter(centroid_2[1],centroid_2[0],color="yellow")
plt.axis('off')
plt.show()
plt.savefig("earthquake_clusters_1.png", dpi=200)
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    /tmp/ipykernel_16730/1333633597.py in <module>
          1 #map_1.plot(column = 'PROPINSI')
    ----> 2 sns.scatterplot(x=df.Longitude, y=df.Latitude, hue = df.Clusters ,palette='Set1',
          3                 size=df.Magnitudo, sizes=(10,200),
          4                     legend = 'brief')
          5 plt.legend(loc=2, bbox_to_anchor=(0.80,1.30))
    

    ~/miniconda3/envs/ihsan/lib/python3.7/site-packages/pandas/core/generic.py in __getattr__(self, name)
       5485         ):
       5486             return self[name]
    -> 5487         return object.__getattribute__(self, name)
       5488 
       5489     def __setattr__(self, name: str, value) -> None:
    

    AttributeError: 'DataFrame' object has no attribute 'Longitude'



```python
df_2018 = df_full[(df_full['Date'].dt.year == 2018) & (df_full['Magnitudo']>=3)]

df_2019 = df_full[(df_full['Date'].dt.year == 2019) & (df_full['Magnitudo']>=3)]

df_2020 = df_full[(df_full['Date'].dt.year > 2020) & (df_full['Magnitudo']>=3)]
```


```python
#Defining the location for April 8th 2019 earthquake
may_22_location = [110.78,-6.69]
```


```python
#map_1.plot(column = 'DATA')

plt.scatter(df_2018.Longitude, df_2018.Latitude,20,color='cyan',
            label="2018")
plt.scatter(df_2019.Longitude, df_2019.Latitude,20,label="2019",
            color='orange')
plt.scatter(df_2020.Longitude, df_2020.Latitude,20,label = "2020",
            color='purple')
plt.scatter(may_22_location[0],may_22_location[1],20,color='black',
            alpha=1, label="May 22 epicenter")

plt.legend(loc=2, bbox_to_anchor=(0.80,1.30))

plt.axis('Off')
plt.show()
plt.savefig("earthquake_clusters_2.png", dpi=200)
```


    
![png](K-Mean_files/K-Mean_16_0.png)
    



    <Figure size 1080x864 with 0 Axes>



```python
import pandas as pd
import pygmt

# Load sample iris data, and convert 'species' column to categorical dtype
df = pd.read_csv("https://github.com/mwaskom/seaborn-data/raw/master/iris.csv")
df["species"] = df.species.astype(dtype="category")

# Use pygmt.info to get region bounds (xmin, xmax, ymin, ymax, zmin, zmax)
# The below example will return a numpy array like [0., 3., 4., 8., 1., 7.]
region = pygmt.info(
    table=df[["petal_width", "sepal_length", "petal_length"]],  # x, y, z columns
    per_column=True,  # report output as a numpy array
    spacing="1/2/0.5",  # rounds x, y and z intervals by 1, 2 and 0.5 respectively
)

# Make our 3D scatter plot, coloring each of the 3 species differently
fig = pygmt.Figure()
pygmt.makecpt(cmap="cubhelix", color_model="+c", series=(0, 3, 1))
fig.plot3d(
    x=df.petal_width,
    y=df.sepal_length,
    z=df.petal_length,
    sizes=0.1 * df.sepal_width,  # Vary each symbol size according to a data column
    color=df.species.cat.codes.astype(int),  # Points colored by categorical number code
    cmap=True,  # Use colormap created by makecpt
    region=region,  # (xmin, xmax, ymin, ymax, zmin, zmax)
    frame=[
        "WsNeZ3",  # z axis label positioned on 3rd corner
        'xafg+l"Petal Width"',
        'yafg+l"Sepal Length"',
        'zafg+l"Petal Length"',
    ],
    style="uc",  # 3D cUbe, with size in centimeter units
    perspective=[315, 25],  # Azimuth NorthWest (315°), at elevation 25°
    zscale=1.5,  # Vertical exaggeration factor
)
fig.show()


```

    /home/muhajir/miniconda3/envs/ihsan/lib/python3.7/site-packages/ipykernel_launcher.py:13: FutureWarning: The 'table' parameter has been deprecated since v0.5.0 and will be removed in v0.7.0. Please use 'data' instead.
      del sys.path[0]
    


    
![png](K-Mean_files/K-Mean_17_1.png)
    



```python
!ls *.SHP
```

    KB_JATIM.SHP



```python
map_1 = gpd.read_file('KB_JATIM.SHP')
```


```python
map_1.plot(column = 'NM_PROP')
```




    <AxesSubplot:>




    
![png](K-Mean_files/K-Mean_20_1.png)
    



```python

```
