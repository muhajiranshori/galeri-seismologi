---
title: "Filter Data Katalog"
date: 2020-03-07T08:25:50+07:00
draft: false
toc: true
comments: true
categories:
- earthuake_catalog
- data_preparation
tags:
- windows
- python
---

# 1. Pendahuluan

Kali ini kami akan membahas tentang filter katalog *arrival time* BMKG. Katalog *arrival time* merupakan data utama saat kita akan melakukan beberapa studi dalam bidang seismologi seperti relokasi hiposenter, tomografi seismik dan lain-lain.

Beberapa instansi yang memiliki tupoksi observasi kegempaan biasanya menyediakan data tersebut seperti ISC, BMKG, USGS. 

Namun bagi anda yang kurang yakin dengan kualitas data tesebut, karena tentu data tersebut dihasilkan oleh banyak operator yang bisa jadi memiliki persepsi picking *arival time* yang berbeda, maka anda dapat melakukan picking sendiri menggunakan beberapa software seperti **seisgram**, **SAC**, **seisan** dan lain-lain.

Teknis penggunakan beberapa software yang saya sebutkan tersebut akan kita bahas tersendiri pada artikel yang lain.

Baiklah, kali ini kita akan mencoba praktek bagaimana cara mem-filter katalog **arrival time**. Tahap filter data ini sangat penting sebagai tahap *data preparation* karena bertujuan untuk mempersiapkan data yang spesifik sesuai daerah penelitian yang akan kita kerjakan dengan beberapa kriteria data yang dapat kita atur tentunya.

Jika anda menggunakan data katalog *arrival time* BMKG maka metode ini saya rekomendasikan sebagai tahap **data preparation** dalam praktek relokasi hiposenter menggunakan **[velest]** dan **[hypoDD]** serta tomografi seismik menggunakan **[simulps12]**.




# 2. Data dan Software

## Data

Data yang digunakan adalah data arrival time repository gempabumi BMKG.

Terdapat 2 tipe format data katalog arrival time yaitu :

- Data repository format lama

```
EventID: bmg2009hiac
Date		Time		Latitude	Longitude	Depth	Mag	TypeMag	smaj		smin	az	rms		cPhase	Region
2009-04-15	01:29:26	-7.39		107.91	98	2.7	MLv		1.79		0.19	120	0.588		10		Java, Indonesia    

Net	Sta	Phase	Date		Time		dis	Az	Res	Amp		Per	Qual	mb	ML	mB
IA	CISI	P	2009-04-15	01:29:40.7	0.2	209	-0.1	0		0	i			
IA	CNJI	P	2009-04-15	01:29:44.2	0.8	276	-0.5	0		0	i			
IA	LEM	P	2009-04-15	01:29:44.3	0.6	333	0.6	0		0	i			
IA	TGJI	P	2009-04-15	01:29:50.2	1.3	67	0.4	0		0	i			
IA	CISI	S	2009-04-15	01:29:53.1	0.2	209	0.6	0		0	i			
IA	BJI	P	2009-04-15	01:29:56.4	1.8	88	0.7	0		0	i			
IA	LEM	S	2009-04-15	01:29:58.0	0.6	333	0.3	0		0	i			
IA	CNJI	S	2009-04-15	01:29:58.5	0.8	276	-1	0		0	i			
IA	TGJI	S	2009-04-15	01:30:08.5	1.3	67	-0.2	0		0	i			
IA	BJI	S	2009-04-15	01:30:18.6	1.8	88	-0.8	0		0	i			
```


- Data repository format baru (format seiscomp)

```
Origin:
    Public ID              Origin#20210419204735.272476.37521
    Date                   2021-04-19
    Time                   20:29:36.7  +/-  0.7 s
    Latitude                -8.87 deg  +/-    6 km
    Longitude              112.48 deg  +/-    2 km
    Depth                      39 km   +/-    7 km
    Agency                 BMKG
    Author                 sysop@clientpro
    Mode                   manual
    Status                 confirmed
    Creation time          2021-04-19 20:47:35
    Residual RMS              0.50 s
    Azimuthal gap             219 deg
4 Network magnitudes:
    MLv       2.79 +/- 0.16   7            BMKG
    M         2.97            7 preferred  BMKG
    ML        3.10 +/- 0.19   7            BMKG
    Mjma      3.21 +/- 0.21   7            BMKG
17 Phase arrivals:
    sta  net   dist azi  phase   time         res     wt  sta
    GEJI  IA    0.5  11  P       20:29:48.3  -0.6 M  1.0  GEJI 
    GEJI  IA    0.5  11  S       20:29:57.9  -0.3 M  1.0  GEJI 
    MLJI  IA    0.7 357  P       20:29:51.4   0.3 M  1.0  MLJI 
    MLJI  IA    0.7 357  S       20:30:02.6   0.7 M  1.0  MLJI 
    PWJI  IA    1.1 321  P       20:29:55.3  -0.2 M  1.0  PWJI 
    PWJI  IA    1.1 321  S       20:30:09.3  -0.4 M  1.0  PWJI 
    GMJI  IA    1.1  58  P       20:29:55.4  -0.6 M  1.0  GMJI 
    GMJI  IA    1.1  58  S       20:30:11.2   0.5 M  1.0  GMJI 
    LUJI  IA    1.2  27  P       20:29:57.5   0.9 M  1.0  LUJI 
    PCJI  IA    1.5 297  P       20:30:01.4   0.8 M  1.0  PCJI 
    PCJI  IA    1.5 297  S       20:30:18.5  -0.5 M  1.0  PCJI 
    BLJI  IA    1.6  45  P       20:30:02.3   0.2 M  1.0  BLJI 
    BLJI  IA    1.6  45  S       20:30:21.5  -0.3 M  1.0  BLJI 
    JAGI  IA    1.7  77  P       20:30:03.9  -0.0 M  1.0  JAGI 
    JAGI  IA    1.7  77  S       20:30:24.4  -0.5 M  1.0  JAGI 
    UGM   IA    2.2 296  P       20:30:10.6   0.3 M  1.0  UGM  
    UGM   IA    2.2 296  S       20:30:36.2  -0.2 M  1.0  UGM  
```

Kami perlu menunjukkan bebrapa tipe data karena script converter-nya pun tentu berbeda.


## Software
**Software-software yang butuhkan yaitu :**
  - [Python](https://www.python.org/) dan `Matlab` Untuk konversi format data 
  - [GMT](https://www.generic-mapping-tools.org/) Untuk visualisasi hasil  (tutorial ini menggunakan GMT4) 
  - [Notepad++](https://notepad-plus-plus.org/downloads/) Untuk menampilkan meng-edit script maupun hasil program. Dapat juga menggunaakan text editor lain sesuai keinginan  

# 3. Langkah-langkah filter katalog

## Kriteria filter
filter data katalog dilakukan berdasarkan beberapa paramter yaitu : 

  - `polyrange` Batas Koordinat daerah penelitian 
  - `daterange` Rentang periode data (Tangal/Bulan/Tahun)
  - `magrange` Rentang magnitudo
  - `deprange` Rentang kedalaman
  - `azrange` Rentang azimuthal gap
  - `rmsrange` Rentang rms residual
  - `cphrange` Rentang jumlah fase

## Langkah-langkah filter

Filter data katalog dilakuan dengan menngunakan script `Filter_Katalog.py` dengan langkah-langkah : 

1. Edit nama file input `fi='Repository_2018.txt'` dan output `fo='Mamasa.txt'` pada baris 2 dan 3.
2. Edit parameter katalog pada baris 4 - 16 sesuai kebutuhan.
3. Simpan perubahan edit lalu jalankan script dengan cara klik kanan pada file script - pilih edit with IDLE - pilih menu Run -> Run Module
4. Maka akan ter-create file output `Mamasa.txt` yang mengandung data sesuai kriteria yang telah ditentukan 

**Catatan :**

Semakin ketat kriteria yang diterapkan, semakin sedidkit data katalog yang dihasilkan.
