---
title: "Relokasi Velest Part 1 Persiapan Data"
date: 2021-04-08T08:51:33+07:00
draft: false
toc: true
comments: true
categories:
- earthquake_relocation
- 1-D_model_determination
tags:
- linux
- python
- velest
- GMT
---

# 1. Pendahuluan
Velest adalah program yang dibuat oleh Evan dkk. (1994) yang berguna untuk me-relokasi hiposenter serta mementukan model kecepatan seismik 1-dimensi. Prinsip atau teori yang mendasari program ini dapat dipelajari **disini**.

Baiklah langsung saja, kali ini kita akan mencoba menerapkan software velest untuk me-relokasi hiposenter gempa Palu yang terjadi pada 28 September 2018 dengan Mw 7.1. Kita tahu bahwa gempa dahsyat tersebut   menimbulkan tsunami dan liquifaksi yang menlan ribuan korban jiwa.  

**Daerah penelitian**
![Palu](/img/Velest/Palu.png)
**Keterangan**

 - `Bintang warna merah` adalah episenter gempabumi utama Mw 7.1, 28 September 2018 
 - `Segitiga tebalik warna kuning` adalah stasiun yang digunakan dalam penelitian
 - `Garis warna biru dengan label huruf` adalah garis cross-section dimana irisan seismisitas akan di tampilkan
 - `Segitiga warna merah` adalah gunung api
 - `Garis merah` adalah sesar 
 - `Bathymetri` yang digunakakan adalah srtm_15
 
Pada artikel ini kita akan membahas cara relokasi hiposenter dengan veleset dengan step-setep sebagai berikut :
1. Filter data katalog arrival time : Tahap pendahuluan untuk menampilkan peta daerah penelitian
2. Convert Data : berisi tentang cara konversi format data menjadi format input velest
3. Running Velest : berisi tentang cara menjalankan program Velest
4. Plot hiposenter hasil relokasi : berisi tentang cara melakukan plotting hiposenter hasil relokasi 
5. Plot histogram residuals : berisi tentang cara melakukan plotting residual yaitu nilai selisih antara travel time observasi dan teoritis 
6. Plot model kecepatan 1-D : tentang cara melakukan plotting hasil pemodelan kecepatan 1-D
7. Plot vektor pergeseran : berisi tentang cara melakukan plotting vektor pergeseran hiposenter antara sebelum dan sesudah relokasi

# 2. Struktur Folder

Untuk memulai tutorial ini secara urut dan runut maka persiapkan struktur folder seperti di bawah ini. 

Folder kerja sebagai contoh dapat anda unduh **disini**

	(base) muhajir@galeri-seismologi:mnt/e/GALERI_SEISMOLOGI/Relokasi-Velest$ tree
	.
	├── README.md
	├── [1] Research Area
	│   ├── Palu.png
	│   ├── Palu.ps
	│   ├── Research_Area.bat
	│   ├── mainshock.dat
	│   ├── station.dat
	│   └── volcano.dat
	├── [2] Convert Data
	│   ├── Palu.cnv
	│   ├── Palu.pha
	│   ├── Palu.txt
	│   ├── Palu_sta.txt
	│   ├── Velest.m
	│   ├── arrival2event_Palu.py
	│   ├── arrival2pha_Palu.py
	│   ├── cat_event_Palu.dat
	│   └── getPSinStation.m
	├── [3] Velest
	│   ├── AK135.mod
	│   ├── Palu.OUT
	│   ├── Palu.cnv
	│   ├── Palu.sta
	│   ├── data_Palu.CNV
	│   ├── stacor_Palu.OUT
	│   ├── velest
	│   ├── velest.cmn
	│   └── velout.mod
	├── [4] Plot Relocated EQ
	│   ├── PK.dat
	│   ├── Palu_awal.bat
	│   ├── Palu_awal.png
	│   ├── Palu_final.bat
	│   ├── Palu_final.dat
	│   ├── Palu_final.png
	│   ├── STA.dat
	│   ├── STA1.dat
	│   ├── cat_event_Palu.dat
	│   ├── kedalaman1.cpt
	│   └── kedalaman2.cpt
	├── [5] Plot Residuals
	│   ├── Histogram_Palu.bat
	│   ├── Palu_P.dat
	│   ├── Palu_S.dat
	│   └── Residual_Palu_P.png
	├── [6] Plot 1-D Velocity Model
	│   ├── 1D_Palu.bat
	│   ├── final_p.dat
	│   ├── final_s.dat
	│   ├── initial_p.dat
	│   ├── initial_s.dat
	│   └── velout.mod
	└── [7] Vektor Pergeseran Hiposenter
		├── A.dat
		├── Palu_Final.dat
		├── Vektor_Palu.bat
		├── Vektor_Palu.png
		├── Vektor_Palu.ps
		├── kedalaman.cpt
		├── kedalaman1.cpt
		├── mainshock.dat
		├── pal.bat
		├── pal2.bat
		└── station.dat

# 3. Data dan Software

## Data

- Data yang digunakan adalah data arrival time repository gempabumi BMKG tahun 2018 studi kasus gempa Palu Mw 7.1, 28 September 2018.

## Software yang dibutuhkan
**Software-software yang butuhkan yaitu :**
  - [Python](https://www.python.org/) dan `Matlab` Untuk konversi format data 
  - [GMT](https://www.generic-mapping-tools.org/) Untuk visualisasi hasil  (tutorial ini menggunakan GMT4) 
  - `Velest` Program utama relokasi hiposenter
  - [Notepad++](https://notepad-plus-plus.org/downloads/) Untuk menampilkan meng-edit script maupun hasil program. Dapat juga menggunaakan text editor lain sesuai keinginan  
  - `Virtual Box` yang berisi `Linux Ubuntu 12 LTS` Untuk menjalankan program velest

Untuk dapat menjalankan tutorial ini dengan baik maka persiapkan dan install terlebih dahulu beberapa software pendukung.



# 4. Filter Data

Filter data berguna untuk menyaring data dengan beberapa kriteria yang kita butuhkan seperti batasan magnitudo, koordinat wilayah, jumlah stasiun dan lain-lain.

Cara filter data sudah pernah kami bahas pada tutorial relokasi hypoDD **berikut**. 

# 5. Convert Data

Langkah-langkah konversi data input pada velest serupa dengan simulps12 namun ada sedikit perbedaan.

**Langkah-langkah convert data**

1. Siapkan file `Palu.txt`. File tersebut adalah hasil filter data sebagaimana dijelaskan langkah-langkahnya  [berikut](https://github.com/muhajiranshori/Tomografi-Simulps12/tree/main/%5B1%5D%20Filer%20Katalog)
2. Jalankan script `cat2event.py` dan `cat2pha.py` dimana masing-masing akan menghasilkan file `cat_event_Palu.dat` dan `Palu.pha`

  ``` python
import cat2event
makeStationList(input_file='Palu.txt', output_file='cat_event_Palu.dat')
  ```
`file cat_event_palu.txt was created sucessfully`

  ``` python
import cat2pha
makeStationList(input_file='Palu.txt', output_file='Palu.pha')
  ```
`file Palu.pha was created sucessfully`


3. Siapkan file data stasiun `Palu_sta.txt` dengan format (nama_stasiun lat lon)
  ```
APSI	-0.91	121.65
BBSI	-5.49	122.56
BKSI	-5.32	120.12
BNSI	-4.4	120.11
BSSI	-6.14	120.49
GTOI	0.76	122.87
KAPI	-5.01	119.75
KDI		-3.96	122.62
KKSI	-4.17	121.65
KMSI	0.57	123.98
LUWI	-1.04	122.77
MJSI	-3.5	118.91
MKS		-5.22	119.47
MMSI	-2.69	118.91
MNI		1.44	124.84
MPSI	0.34	119.9
MRSI	0.48	121.94
MSSI	-2.55	120.32
NLAI	-3.24	127.1
PCI		-0.91	119.84
PMSI	-3.5	118.91
SANI	-2.05	125.99
SGSI	3.69	125.53
SKSI	-2.53	121.33
SMSI	0.99	122.37
SPSI	-3.96	119.77
TMSI	1.29	124.92
TOLI	1.11	120.78
TTSI	-3.05	119.82
  ```
4. Jalankan script `Velest.m` pada Matlab.
5. Tunggu beberapa saat mka akan dihasilkan file `Palu.cnv`

  ```
181226 0524 24.10  1.5700S 120.1500W  10.00   3.20    1
TTSIP0 25.23TTSIS0 46.81SPSIP0 40.04SPSIS0 69.90MRSIP0 43.21MRSIS0 77.31
 PCIP0 14.12APSIP0 27.54PMSIP0 38.26LUWIP0 43.30SMSIP0 54.23

181225 2036 10.10  1.1900S 119.6900W  10.00   4.60    2
 PCIP0  5.62 PCIS0 11.07TTSIP0 31.35TTSIS0 56.35SMSIP0 51.84SMSIS0 98.80
APSIP0 34.24PMSIP0 40.81SPSIP0 44.56MRSIP0 41.41LUWIP0 48.92KKSIP0 57.24
KAPIP0 59.27 MKSP0 63.80 KDIP0 61.29BKSIP0 64.57KMSIP0 71.90SANIP0 91.95
NLAIP0109.61

181223 1608 24.10  1.5400S 120.0900W  10.00   3.30    3
TTSIP0 25.75TTSIS0 46.41 PCIP0 11.27APSIP0 27.37PMSIP0 39.19SPSIP0 40.20
LUWIP0 43.90SMSIP0 53.88BKSIP0 58.58

181223 0307 47.50  1.4100S 120.1800W  10.00   3.70    4
LUWIP0 42.92LUWIS0 75.66 PCIP0 12.36APSIP0 25.59TTSIP0 29.21PMSIP0 39.44
SPSIP0 41.45MRSIP0 40.76SMSIP0 51.37 KDIP0 55.37KAPIP0 55.44

181222 1223 24.40  1.5700S 119.8700W  17.00   3.30    5
TTSIP0 24.44TTSIS0 45.35APSIP0 30.63APSIS0 55.16MRSIP0 46.10MRSIS0 80.56
LUWIP0 46.40LUWIS0 84.19 PCIP0 13.87PMSIP0 34.40SPSIP0 38.85KKSIP0 48.89
KAPIP0 52.89

181221 2123 21.40  0.3800S 119.7800W  10.00   3.80    6
MRSIP0 37.16MRSIS0 67.03 PCIP0  9.79APSIP0 33.24TTSIP0 43.27SMSIP0 45.98
LUWIP0 49.65PMSIP0 52.33SPSIP0 55.08KKSIP0 63.71 KDIP0 69.12
...
  ```










<!--more-->
