---
title: "Autodeteksi Dan Autopicking Eqtransformer"
date: 2022-05-31T16:06:37+07:00
draft: false
toc: true
comments: true
categories:
- machine_learning
- deep_learning
- automatic_earthquake_localization
tags:
- linux
- python
- eqtransformer
---

# 1. Pendahuluan

Jika sebelumnya kita sudah belajar cara meng-install EQTransformer (EQT), menjalankan EQT untuk mendeteksi Gempa Ambarawa, Nah sekarang kita akan membuat si program EQT ini dapat berjalan secara *real time* atau *semi real time* untuk secara otomatis mendeteksi dan melakukan picking sinyal setiap kali terjadi event gempa hingga diperoleh parameter berikut petanya.

Menarik bukan...

Harapan kita tentu pada nantinya kita tidak perlu repot-repot lagi melakukan analisa gempa karena semua dapat berjalan secara otomatis, walaupun secara akurasi masih harus perlu diuji secara serius.

Bagaiamana caranya ? langsung saja kita mulai.

# 2. Struktur Folder

# 3. Data dan Software

# 4. Running

Langkah pertama adalah menghapus file-file sebelumya agar tidak terjadi redundant dan memeori tidak semakin besar.

Berikut adalah bash script-nya 

**rm.bash**
``` bash
#!/usr/bin/bash
rm -r downloads_mseeds_processed_hdfs
rm -r downloads_mseeds
rm -r preproc
rm -r asociation
rm -r detections
rm hypoinvers.arc
rm hypoinvers.prt
rm hypoinvers.sum
```

Jalankan dengab cara :

``` bash
bash rm.bash
```

Langkah selanjutnya adalah *raw data preparation* 

Berikut adalah bash script-nya 

**preapare.bash**
``` bash
#!/usr/bin/bash
mkdir -p Data &
rm -r Data/* &
current_date=$(date +%j -d "2 day ago")
#current_date=$(date +%j)
cp -t /home/sysop/Muhajir/AutoLoc1.0/Data /home/sysop/seiscomp/var/lib/archive/2022/IA/*/*/*$current_date
rm /home/sysop/Muhajir/AutoLoc1.0/Data/*GEJI*
rm /home/sysop/Muhajir/AutoLoc1.0/Data/*GKJM*
rm /home/sysop/Muhajir/AutoLoc1.0/Data/*SEJI*
rm /home/sysop/Muhajir/AutoLoc1.0/Data/*PPJI*
```
Jalankan dengab cara :

``` bash
bash prepare.bash
```

**run.bash**
``` bash
#!/usr/bin/bash
source /home/sysop/miniconda3/bin/activate eqt
cd /home/sysop/Muhajir/AutoLoc1.0/
bash rm.bash
bash prepare.bash
echo "Preparing Raw Data : done"
python eqt.py
echo "Running EQTransfomer : done"
sh run_hypoinvers.sh
echo "Running Hypoinvers : done"
python sum2evt.py
python peta.py
echo "Creating Map : done"
```

**eqt.py**
``` python
from EQTransformer.utils.hdf5_maker import preprocessor
from EQTransformer.core.predictor import predictor
from EQTransformer.utils.associator import run_associator

from obspy import read, UTCDateTime
import numpy as np
import shutil, os

length = 2*3600
#start_time = UTCDateTime("2022-01-12T19:00:00")
#end_time = start_time + length
end_time = UTCDateTime()
end_time = end_time - 2*60*60*24
start_time = end_time - length

stime = str(start_time.year)+'-'+str(start_time.month)+'-'+str(start_time.day)+' '+str(start_time.hour)+':'+str(start_time.minute)+':'+str(start_time.second)+'.00'
etime = str(end_time.year)+'-'+str(end_time.month)+'-'+str(end_time.day)+' '+str(end_time.hour)+':'+str(end_time.minute)+':'+str(end_time.second)+'.00'


st = read('Data/*')
dt = UTCDateTime(start_time)
st.trim(dt, dt + length) 
st.merge(method=0, fill_value='interpolate', interpolation_samples=0) 
st.filter('bandpass', freqmin=1.00, freqmax=10.0, corners=2, zerophase=True)
#st = read('*.SAC')

n = np.arange(0, len(st), 1)


for i in n:

    tr = st[i]
    
    network = tr.stats.network
    station = tr.stats.station
    channel = tr.stats.channel
    starttime = tr.stats.starttime
    starttime=str(starttime)
    endtime = tr.stats.endtime
    endtime = str(endtime)
    
    Year = starttime.split('-')[0]
    Month = starttime.split('-')[1]
    Day = starttime.split('-')[2][0:2]
    
    Hour = starttime.split(':')[0][11:13]
    Minute = starttime.split(':')[1]
    Second = starttime.split(':')[2][0:2]
    
    Year_end = endtime.split('-')[0]
    Month_end = endtime.split('-')[1]
    Day_end = endtime.split('-')[2][0:2]
    
    Hour_end = endtime.split(':')[0][11:13]
    Minute_end = endtime.split(':')[1]
    Second_end = endtime.split(':')[2][0:2]
    
    
    name = network+'.'+station+'..'+channel+'__'+str(Year)+str(Month)+str(Day)+'T.'+str(Hour)+str(Minute)+str(Second_end)+'__'+str(Year_end)+str(Month_end)+str(Day_end)+'T.'+str(Hour_end)+str(Minute_end)+str(Second_end)+'Z'+'.mseed'
    
    tr.write(name , format="MSEED")
    directory = station
  
	# Parent Directory path
    parent_dir = "/home/sysop/Muhajir/AutoLoc1.0/downloads_mseeds/"
  
	# Path
    path = os.path.join(parent_dir, directory)
    #os.mkdir(path)
	
    os.makedirs(path, exist_ok=True)
    source = "/home/sysop/Muhajir/AutoLoc1.0/"+name
    destination = "/home/sysop/Muhajir/AutoLoc1.0/downloads_mseeds/"+directory
    shutil.move(source, destination)


json_basepath = os.path.join(os.getcwd(),"json/station_list.json")
preprocessor(preproc_dir="preproc", mseed_dir='downloads_mseeds', stations_json=json_basepath, overlap=0.3, n_processor=2)

predictor(input_dir= 'downloads_mseeds_processed_hdfs', input_model='EqT_model.h5', output_dir='detections', detection_threshold=0.3, P_threshold=0.1, S_threshold=0.1, number_of_plots=100, plot_mode='time')

out_dir = "asociation"
try:
        shutil.rmtree(out_dir)
except Exception:
        pass
os.makedirs(out_dir)


run_associator(input_dir='detections', start_time=stime, end_time=etime,  moving_window=25, pair_n=3)
```

**run_hypoinvers.bash**
``` bash
./hyp1.40 << EOF
@hypoinvers.hyp
Y2000.phs
hypoinvers.prt
hypoinvers.sum
hypoinvers.arc
LOC
EOF
```

**Y2000.phs**
```
2022 428151925.14 0 3.00 98 16.80 5.000.00
PRJI IA  HHE     2022 4281519 0.00       35.32ES 1
PRJI IA  HHZ IP 22022 428151924.41        0.00   0
PCJI IA  HHE     2022 4281519 0.00       36.30ES 2
PCJI IA  HHZ IP 32022 428151925.41        0.00   0
UGM  IA  HHE     2022 4281519 0.00       39.00ES 1
UGM  IA  HHZ IP 22022 428151927.14        0.00   0
PWJI IA  HHE     2022 4281519 0.00       51.66ES 2
PWJI IA  HHZ IP 22022 428151934.31        0.00   0
                                                                  200001
2022 428153313.79 0 3.00 98 16.80 5.000.00
PWJI IA  HHE     2022 4281533 0.00       19.91ES 1
PWJI IA  HHZ IP 22022 4281533 3.56        0.00   0
MLJI IA  HHE     2022 4281533 0.00       19.45ES 2
MLJI IA  HHZ IP 32022 4281533 4.57        0.00   0
PCJI IA  HHE     2022 4281533 0.00       21.30ES 2
PCJI IA  HHZ IP 22022 4281533 5.46        0.00   0
MKJM IA  HHE     2022 4281533 0.00       42.27ES 2
MKJM IA  HHZ IP 32022 4281533 7.42        0.00   0
SNJI IA  HHE     2022 4281533 0.00       27.15ES 2
...
```

**peta.py**
``` python
import pygmt
import numpy as np

fig = pygmt.Figure()

pygmt.config(MAP_FRAME_TYPE="plain")
pygmt.config(FORMAT_GEO_MAP="ddd.xx")


#region = [110, 115, -12, -5]
#
#x = np.random.uniform(region[0], region[1], 100)
#y = np.random.uniform(region[2], region[3], 100)


#data = np.loadtxt('hypo.dat')
data = np.genfromtxt('hypo.dat', delimiter=',')
ld = len(data)
if data.shape == (ld,):
	data=np.reshape(data, (1, ld))
x=data[:,[1]]
y=data[:,[0]]
l=len(x)
y=y*-1

x = np.reshape(x, (l, ))
y = np.reshape(y, (l, ))

fig.coast(
    # Set the x-range from 10E to 20E and the y-range to 35N to 45N
    region="109/116/-12/-5",
    # Set projection to Mercator, and the figure size to 15 centimeters
    projection="M15c",
    # Set the color of the land to light gray
    land="lightgray",
    # Set the color of the water to white
    water="skyblue",
    # Display the national borders and set the pen thickness to 0.5p
    borders="2/0.5p",
    # Display the shorelines and set the pen thickness to 0.5p
    shorelines="1/0.3p",
    # Set the frame to display annotations and gridlines
    frame = ["ag", "+t'Peta Seismistas Jawa Timur (AutoLocEQT 1.0)'"],
)

fig.plot(x=x, y=y, style="c0.2c", color="red", pen="black")
#fig.show()
fig.savefig("Peta_Real_Time.png")
```


