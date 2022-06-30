---
title: "Ambient Noise Cross Corelation"
date: 2022-01-22T14:39:17+07:00
draft: false
comments: true
categories:
- ambient_noise_tomography
tags:
- jupyter_notebook
- python
---

## ANCC

```python
from EQTransformer.utils.hdf5_maker import preprocessor
import os
json_basepath = os.path.join(os.getcwd(),"json/station_list.json")

preprocessor(preproc_dir="preproc", mseed_dir='downloads_mseeds', 
    stations_json=json_basepath, overlap=0.3, n_processor=2)
```

    ============ Station SISI has 3 chunks of data.
    ============ Station TDNI has 2 chunks of data.
      * SISI (1) .. 20220313 --> 20220314 .. 1 components .. sampling rate: 20.0
      * TDNI (1) .. 20220313 --> 20220314 .. 1 components .. sampling rate: 40.0
      * SISI (2) .. 20220313 --> 20220314 .. 1 components .. sampling rate: 20.0
      * TDNI (2) .. 20220313 --> 20220314 .. 2 components .. sampling rate: 40.0
      * SISI (3) .. 20220313 --> 20220314 .. 1 components .. sampling rate: 20.0
     Station TDNI had 2 chuncks of data
    4113 slices were written, 4114.0 were expected.
    Number of 1-components: 1. Number of 2-components: 1. Number of 3-components: 0.
    Original samplieng rate: 40.0.
    ============ Station PBSI has 3 chunks of data.
      * PBSI (1) .. 20220313 --> 20220314 .. 1 components .. sampling rate: 20.0
     Station SISI had 3 chuncks of data
    6171 slices were written, 6171.0 were expected.
    Number of 1-components: 3. Number of 2-components: 0. Number of 3-components: 0.
    Original samplieng rate: 20.0.
      * PBSI (2) .. 20220313 --> 20220314 .. 1 components .. sampling rate: 20.0
      * PBSI (3) .. 20220313 --> 20220314 .. 1 components .. sampling rate: 20.0
     Station PBSI had 3 chuncks of data
    6170 slices were written, 6171.0 were expected.
    Number of 1-components: 3. Number of 2-components: 0. Number of 3-components: 0.
    Original samplieng rate: 20.0.
    


```python
import os
json_basepath = os.path.join(os.getcwd(),"json/station_list.json")
```


```python
#from EQTransformer.core.predictor import predictor

#predictor(input_dir= 'downloads_mseeds_processed_hdfs', 
#    input_model='EqT_model.h5', output_dir='detections', 
#    detection_threshold=0.7, P_threshold=0.6, S_threshold=0.3, number_of_plots=100, plot_mode='time')

```


```python
from EQTransformer.core.mseed_predictor import mseed_predictor

mseed_predictor(input_dir='downloads_mseeds', input_model='EqT_model.h5', stations_json=json_basepath, output_dir='detections', detection_threshold=0.6, P_threshold=0.6, S_threshold=0.3, number_of_plots=100, plot_mode='time', overlap=0.3, batch_size=500)
```


![ancc](/img/ANCC/70_150.png)


