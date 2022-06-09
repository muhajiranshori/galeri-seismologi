---
title: "Ambient Noise Cross Corelation"
date: 2022-05-22T14:39:17+07:00
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

    Using TensorFlow backend.
    03-19 07:38 [INFO] [EQTransformer] Running EqTransformer  0.1.59
    03-19 07:38 [INFO] [EQTransformer] *** Loading the model ...
    03-19 07:45 [INFO] [EQTransformer] *** Loading is complete!
    03-19 07:45 [INFO] [EQTransformer] There are files for 3 stations in downloads_mseeds directory.
    03-19 07:45 [INFO] [EQTransformer] Started working on PBSI, 1 out of 3 ...
    03-19 07:45 [INFO] [EQTransformer] 20220313T.205900__20220314T.210000Z.mseed
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: Matching sans\-serif:style=normal:variant=normal:weight=normal:stretch=normal:size=10.0.
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizThreeSymReg.ttf', name='STIXSizeThreeSym', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSans-Oblique.ttf', name='DejaVu Sans', style='oblique', variant='normal', weight=400, stretch='normal', size='scalable')) = 1.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizFourSymBol.ttf', name='STIXSizeFourSym', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 10.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSerif.ttf', name='DejaVu Serif', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSansMono.ttf', name='DejaVu Sans Mono', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\cmtt10.ttf', name='cmtt10', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\cmr10.ttf', name='cmr10', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSansMono-BoldOblique.ttf', name='DejaVu Sans Mono', style='oblique', variant='normal', weight=700, stretch='normal', size='scalable')) = 11.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSerif-Bold.ttf', name='DejaVu Serif', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 10.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\cmex10.ttf', name='cmex10', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizTwoSymBol.ttf', name='STIXSizeTwoSym', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 10.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizFiveSymReg.ttf', name='STIXSizeFiveSym', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\cmb10.ttf', name='cmb10', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSansMono-Oblique.ttf', name='DejaVu Sans Mono', style='oblique', variant='normal', weight=400, stretch='normal', size='scalable')) = 11.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSerif-Italic.ttf', name='DejaVu Serif', style='italic', variant='normal', weight=400, stretch='normal', size='scalable')) = 11.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizOneSymBol.ttf', name='STIXSizeOneSym', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 10.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXGeneralBolIta.ttf', name='STIXGeneral', style='italic', variant='normal', weight=700, stretch='normal', size='scalable')) = 11.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXGeneralBol.ttf', name='STIXGeneral', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 10.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizTwoSymReg.ttf', name='STIXSizeTwoSym', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\cmmi10.ttf', name='cmmi10', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\cmsy10.ttf', name='cmsy10', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSansMono-Bold.ttf', name='DejaVu Sans Mono', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 10.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXGeneralItalic.ttf', name='STIXGeneral', style='italic', variant='normal', weight=400, stretch='normal', size='scalable')) = 11.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSansDisplay.ttf', name='DejaVu Sans Display', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizOneSymReg.ttf', name='STIXSizeOneSym', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizThreeSymBol.ttf', name='STIXSizeThreeSym', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 10.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSans-BoldOblique.ttf', name='DejaVu Sans', style='oblique', variant='normal', weight=700, stretch='normal', size='scalable')) = 1.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXGeneral.ttf', name='STIXGeneral', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\cmss10.ttf', name='cmss10', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSans-Bold.ttf', name='DejaVu Sans', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 0.33499999999999996
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSerifDisplay.ttf', name='DejaVu Serif Display', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXNonUni.ttf', name='STIXNonUnicode', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSans.ttf', name='DejaVu Sans', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 0.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXNonUniBol.ttf', name='STIXNonUnicode', style='normal', variant='normal', weight=700, stretch='normal', size='scalable')) = 10.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\DejaVuSerif-BoldItalic.ttf', name='DejaVu Serif', style='italic', variant='normal', weight=700, stretch='normal', size='scalable')) = 11.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXNonUniIta.ttf', name='STIXNonUnicode', style='italic', variant='normal', weight=400, stretch='normal', size='scalable')) = 11.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXSizFourSymReg.ttf', name='STIXSizeFourSym', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Users\\WIN 10\\.conda\\envs\\eqt\\lib\\site-packages\\matplotlib\\mpl-data\\fonts\\ttf\\STIXNonUniBolIta.ttf', name='STIXNonUnicode', style='italic', variant='normal', weight=700, stretch='normal', size='scalable')) = 11.335
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Windows\\Fonts\\MSUIGHUR.TTF', name='Microsoft Uighur', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Windows\\Fonts\\javatext.ttf', name='Javanese Text', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Windows\\Fonts\\LEELAWAD.TTF', name='Leelawadee', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 10.05
    03-19 07:48 [DEBUG] [matplotlib.font_manager] findfont: score(FontEntry(fname='C:\\Windows\\Fonts\\arial.ttf', name='Arial', style='normal', variant='normal', weight=400, stretch='normal', size='scalable')) = 6.413636363636363
    

    ---------------------------------------------------------------------------

    OSError                                   Traceback (most recent call last)

    C:\Users\WIN10~1\AppData\Local\Temp/ipykernel_10416/2772615821.py in <module>
          1 from EQTransformer.core.mseed_predictor import mseed_predictor
          2 
    ----> 3 mseed_predictor(input_dir='downloads_mseeds', input_model='EqT_model.h5', stations_json=json_basepath, output_dir='detections', detection_threshold=0.6, P_threshold=0.6, S_threshold=0.3, number_of_plots=100, plot_mode='time', overlap=0.3, batch_size=500)
    

    ~\.conda\envs\eqt\lib\site-packages\EQTransformer\core\mseed_predictor.py in mseed_predictor(input_dir, input_model, stations_json, output_dir, detection_threshold, P_threshold, S_threshold, number_of_plots, plot_mode, loss_weights, loss_types, normalization_mode, batch_size, overlap, gpuid, gpu_limit, overwrite)
        320                     post_write = len(detection_memory)
        321                     if plt_n < args['number_of_plots'] and post_write > pre_write:
    --> 322                         _plotter_prediction(data_set[meta["trace_start_time"][ix]], args, save_figs, predD[ix][:, 0], predP[ix][:, 0], predS[ix][:, 0], meta["trace_start_time"][ix], matches)
        323                         plt_n += 1
        324 
    

    ~\.conda\envs\eqt\lib\site-packages\EQTransformer\core\mseed_predictor.py in _plotter_prediction(data, args, save_figs, yh1, yh2, yh3, evi, matches)
       1398 
       1399         fig.tight_layout()
    -> 1400         fig.savefig(os.path.join(save_figs, str(evi)+'.png'))
       1401         plt.close(fig)
       1402         plt.clf()
    

    ~\.conda\envs\eqt\lib\site-packages\matplotlib\figure.py in savefig(self, fname, transparent, **kwargs)
       3017                         ax.patch._cm_set(facecolor='none', edgecolor='none'))
       3018 
    -> 3019             self.canvas.print_figure(fname, **kwargs)
       3020 
       3021     def ginput(self, n=1, timeout=30, show_clicks=True,
    

    ~\.conda\envs\eqt\lib\site-packages\matplotlib\backend_bases.py in print_figure(self, filename, dpi, facecolor, edgecolor, orientation, format, bbox_inches, pad_inches, bbox_extra_artists, backend, **kwargs)
       2323                         orientation=orientation,
       2324                         bbox_inches_restore=_bbox_inches_restore,
    -> 2325                         **kwargs)
       2326             finally:
       2327                 if bbox_inches and restore_bbox:
    

    ~\.conda\envs\eqt\lib\site-packages\matplotlib\backend_bases.py in wrapper(*args, **kwargs)
       1646             kwargs.pop(arg)
       1647 
    -> 1648         return func(*args, **kwargs)
       1649 
       1650     return wrapper
    

    ~\.conda\envs\eqt\lib\site-packages\matplotlib\_api\deprecation.py in wrapper(*inner_args, **inner_kwargs)
        410                          else deprecation_addendum,
        411                 **kwargs)
    --> 412         return func(*inner_args, **inner_kwargs)
        413 
        414     DECORATORS[wrapper] = decorator
    

    ~\.conda\envs\eqt\lib\site-packages\matplotlib\backends\backend_agg.py in print_png(self, filename_or_obj, metadata, pil_kwargs, *args)
        541         mpl.image.imsave(
        542             filename_or_obj, self.buffer_rgba(), format="png", origin="upper",
    --> 543             dpi=self.figure.dpi, metadata=metadata, pil_kwargs=pil_kwargs)
        544 
        545     def print_to_buffer(self):
    

    ~\.conda\envs\eqt\lib\site-packages\matplotlib\image.py in imsave(fname, arr, vmin, vmax, cmap, format, origin, dpi, metadata, pil_kwargs)
       1673         pil_kwargs.setdefault("format", format)
       1674         pil_kwargs.setdefault("dpi", (dpi, dpi))
    -> 1675         image.save(fname, **pil_kwargs)
       1676 
       1677 
    

    ~\.conda\envs\eqt\lib\site-packages\PIL\Image.py in save(self, fp, format, **params)
       2235                 fp = builtins.open(filename, "r+b")
       2236             else:
    -> 2237                 fp = builtins.open(filename, "w+b")
       2238 
       2239         try:
    

    OSError: [Errno 22] Invalid argument: 'E:\\Muhajir\\EQT\\EQT2\\detections\\PBSI_outputs\\figures\\2022-03-13 21:34:16.487500.png'



```python
#from EQTransformer.utils.plot import plot_data_chart

#plot_data_chart('time_tracks.pkl', time_interval=10)

```




![ancc](/img/ANCC/70_150.png)


