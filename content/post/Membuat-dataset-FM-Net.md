---
title: "Membuat Dataset FM Net"
date: 2022-05-31T16:01:45+07:00
draft: false
toc: true
comments: true
categories:
- machine_learning
- deep_learning
- moment_tensor
tags:
- linux
- python
- pyrocko
- qseis
- FM-Net
---

# 1. Pendahuluan

Sebelum kita memulai pembahasan mengenai FM-Net, maka ada baiknya anda mengerti terlebih dahulu apa itu ML dan DL.

Disini kita akan belajar membuat dataset untuk program FM-Net.

Dataset atau data training nantinya akan terdiri dari data input dan data label.

Terkait cara penggunaan program FM-Net dapat anda baca **disini**

# 2. Struktur Folder

Untuk mempelajari data mari kita lihat struktur data dalam folder test_data berikut plotting nya.

Terdapat 2 jenis data yang terdapat dalam file `000001.mat` yaitu data input **( amp_3d )** berupa waveform sintetis, dan data label **(gaus_pa)** berupa kurva probabilitas gaussian denga nilai rata-rata merupakan parameter focal mechanism.

Ukuran data input adalah 972 x 48 x 128

dimana :

- 972 adalah jumlah data

- 48 adalah ( 3 x 16 ) merupakan jumlah komponen (E N Z) dan jumlah stasiun

- 128 adalah jumlah data sample

Panggil dan plot data input dengan script plot_data_input.m 

Gambar disamping adalah tampilan sample data input ( data ke-300) pada set data test. 

# 3. Data dan Software

## Data

Data yang digunakan adalah data waveform sintetis yang dibuat menggunakan software QSEIS berdasarkan skenario kombinasi parameter *focal mechanism*. 

## Software
- [Pyrocko](https://pyrocko.org/)
- [Matlab]
- [GMT4](https://www.soest.hawaii.edu/gmt/gmt/gmt_windows_SOEST.html)
- [Miniconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html)
- [Obpsy](https://github.com/obspy/obspy/wiki/Installation-via-Anaconda)
- [EQTransformer](https://eqtransformer.readthedocs.io/en/latest/)


Ukuran data target adalah 972 x 3 x 128

dimana :

- 972 adalah jumlah data
- 3 adalah parameter focal mechanism berupa nilai strike, dip, rake
- 128 adalah panjang data
Panggil dan plot data input dengan script plot_data_label.m 
Gambar disamping adalah tampilan sample data target ( data ke-300) pada set data test. 


**SKENARIO PARAMETER FOCAL MECHANISM :**
- Strike 	: 0° - 360 ° increment 30 ° ( 12 nilai )
- Dip 	: 0 ° - 90 ° increment 10 ° ( 9 nilai )
- Rake 	: -90 ° - 90 ° increment 20 °  (9 nilai )
Total Kombinasi Skenario : (12 x 9 x 9 = 972 )

**GRID :** 
- Bujur 	:  110.5 sampai 114.5 dengan increemnet 0.5 (9 grid) 
- Lintang 	: -10.95 sampai -8.55 dengan increment 0.3 (9 grid)
- Kedalaman : 0 sampai 20 km dengan increment 2 km (10 grid)

Total Kombinasi Grid : (9 x 9 x 10 = 810 )

Total : Total kombinasi skenario focmech x Total Grid = 972 x 810 = 787.320 

Ukuran tiap waveform adalah 192 kb x 787.320 = 151 Giga Byte

Sebagai percobaan makan akan di buat waveform sintetis dari 1 titik (titik pusat) dengan 972 kombinasi skenario parameter focal mechanism. 

Estimasi ukuran data hanya sekitar 182 Mega Byte. 


Edit data `grid.txt` sesuai dengan jarak grid (dalam derajat ), 

kolom pertama adalah grid bujur, 

kolom kedua adalah grid lintang. 

Tanda negatif pada ke-2 kolom tersebut masing-masing menunjukkan arah barat dan utara dari titik pusat ( bintang warna merah). 

Tentukan koordinat pusat pada file `Pusat.txt` 

Jalankan script `grid.m` maka akan tercreate file `GRD.txt` yang berisi data koordinat grid. 

Double klik file `Grid_Node.bat` untuk membuat peta grid.

![Grid_FM_Net](/img/FM-Net/grid_fm_net.png)




Beirkut adalah langkah-langkah installnya :

1. Install anaconda / miniconda dengan cara **berikut**
2. Install Pyrocko

``` python	
conda create –n pyrocko python=3.7
conda activate pyrocko	
pip install pyrocko 
```

3. Install QSEIS dengan cara download dari **[sini](https://git.pyrocko.org/pyrocko/fomosto-qseis)**, ekstrak lalu masuk kedalam folder program melalui terminal, kemudian ketik perintah :

``` python		
autoreconf -i
./configure
make
sudo make install
```

4. Buat fungsi green dengan perintah :

``` python		
fomosto init qseis.2006a my_gfs
cd my_gfs 
fomosto ttt
fomosto build
```

Sebelum menjalankan perintah `fomosto ttt`, ubah setting file qseis dan config sebagai berikut.


**gf_stores/my_gfs/exra/qseis**


```
--- !pf.QSeisConfigqseis_version: 
2006atime_region:- 
'{stored:begin}-30'- 
'{stored:end}+100'cut:- 
'{stored:begin}-30'- 
'{stored:end}+100'
```

**gf_stores/my_gfs/config**

```
sample_rate: 1.0
source_depth_min: 10000.0
source_depth_max: 30000.0
source_depth_delta: 10000.0
distance_min: 10000.0
distance_max: 2000000.0
distance_delta: 10000.0
```






Membuat waveform sintetis dengan script `create_synt.py` maka akan dihasilkan waveform dalam format miniseed dengan penamaan file `lat_lon_strike_dip_rake.mseed`. 

Sebagai contoh jalankan `create_synt_exp.py` ( perhitungan 1 grid saja).

Jalankan script `miniseed2ascii.py` untuk merubah file miniseed menjadi ascii dengan format `TSPAIR` (akan dihasilkan file `outfile.ascii`).

Jalankan script `ascii2txt.py` untuk merubah file `ascii` menjadi `.txt` (akan dihasilkan file `amp_3d.txt`).


1.   Jalankan script `create_mat.m` untuk membuat dataset dalam format `.mat`. 




Membuat waveform sintetis dengan script create_synt.py maka akan dihasilkan waveform dalam format miniseed dengan penamaan file lat_lon_strike_dip_rake.mseed
Jalankan script miniseed2ascii.py untuk merubah file miniseed menjadi ascii dengan format TSPAIR (akan dihasilkan file outfile.ascii).
Jalankan script ascii2txt.py untuk merubah file ascii menjadi .txt (akan dihasilkan file amp_3d.txt).


1.   Jalankan script create_mat.m untuk membuat dataset dalam format .mat. 

Catatan :	
amp_3d adalah data input berupa waveform sintetis berjumlah 972 dari 16 stasiun 3 komponen (total 48) dan Panjang 128 s (sampling rate 1 Hz), filter 0.05 – 0.1 Hz, normalisasi amplitudo berdasarkan nilai amplitudo maksimum. 

gaus_pa adalah target atau data label berjumlah 972 berupa kurva probabilitas gaussian dengan nilai rata-rata merupakan nilai parameter focal yaitu strike, dip, rake (3 parameter), panjang data 128 dan standar deviasi masing-masing 14°, 3.5° dan 7°.


Siapkan file 000001.mat ( dari hasil persiapan data)
Siapkanfile metric.py ( untuk menghitung nilai loss )
Jalankan script train.py maka akan dihasilkan file model.cnn
Siapkan file yang akan di prediksi dalam format .mat
Lakukan prediksi dengan menjalankan script predict.py

Catatan :
Jika anda pernah menggunakan program eqtransformer pada anaconda/miniconda, maka gunakan environment eqtransformer untuk running `train.py` dan `predict.py` karena modul yang digunakan adalah sama. Cara ini lebih praktis daripada harus membuat environment baru dan menginstal beberapa modul yang dibutuhkan. 
	
Catatan :	
amp_3d adalah data input berupa waveform sintetis berjumlah 972 dari 16 stasiun 3 komponen (total 48) dan Panjang 128 s (sampling rate 1 Hz), filter 0.05 – 0.1 Hz, normalisasi amplitudo berdasarkan nilai amplitudo maksimum. 

gauss_pa adalah target atau data label berjumlah 972 berupa kurva probabilitas gaussian dengan nilai rata-rata merupakan nilai parameter focal yaitu strike, dip, rake (3 parameter), panjang data 128 dan standar deviasi masing-masing 14°, 3.5° dan 7°.