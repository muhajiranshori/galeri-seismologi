---
title: "Relokasi HypoDD Part 1 : Persiapan Data"
date: 2021-03-02T17:21:25+07:00
draft: false
toc: false
comments: true
categories:
- earthquake_relocation
tags:
- cygwin
- python
- hypoDD
- GMT
---

# 1. Pendahuluan

Sebagai pengamat gempa yang dalam setiap tugas dituntuk untuk menentukan lokasi hiposenter secara cepat, acap kali banyak posisi hiposenter gempa kita masih kurang tepat (misal masih banyak terdapat fix depth) sehingga disinilah pentingnya proses relokasi gempa.

Dengan melakukan relokasi kita berharap hiposenter dapat bergeser pada posisi terbaiknya yang lebih *make sense* secara geologi sehingga lebih mudah diinterpretasi terkait kondisi seismotektoniknya.

Saya akan tunjukkan contoh fix depth pada data katalog berikut perubahannya setelah dilakukan relokasi.


**Sebelum Relokasi**
![Krakatau_Before](/img/hypoDD/krakatau_before.png)
*Seismisitas di bawah gunungapi Anak Krakatau **sebelum** relokasi hiposenter* ([sumber](http://stageof.tretes.bmkg.go.id/artikel-kondisi-kegempaan-di-bawah-gunung-api-anak-krakatau-periode-tahun-2009-2017--berdasarkan-hasil-relokasi-hiposenter-7))


**Setelah Relokasi**
![Krakatau_After](/img/hypoDD/krakatau_after.png)
*Seismisitas di bawah gunungapi Anak Krakatau **sesudah** relokasi hiposenter* ([sumber](http://stageof.tretes.bmkg.go.id/artikel-kondisi-kegempaan-di-bawah-gunung-api-anak-krakatau-periode-tahun-2009-2017--berdasarkan-hasil-relokasi-hiposenter-7))

Nah kali ini kita akan praktek melakukan relokasi hiposenter menggunakan program hypoDD. 

Apa saja alat dan bahan yang harus dipersiapkan serta bagaimana langkah kerjanya ? Mari kita simak. 

# 2. Struktur Folder Kerja

Sebelum memulai tutorial download terlebih dahulu [folder_hypoDD] yang memiliki struktur sebagai berikut.

	(base) muhajir@galeri-seismologi:/mnt/e/GALERI_SEISMOLOGI/Relokasi-HypoDD$ tree
	.
	├── README.md
	├── [1] Research Area
	│   ├── GA.dat
	│   ├── GU.dat
	│   ├── Jatim.bat
	│   ├── Jatim.png
	│   ├── Jatim.ps
	│   ├── README.md
	│   ├── mainshock.dat
	│   ├── seis.dat
	│   ├── station.dat
	│   └── volcano.dat
	├── [2] Convert Data
	│   ├── Jatim.pha
	│   ├── Jatim.txt
	│   ├── README.md
	│   └── cat2pha.py
	├── [3] HYPODD
	│   ├── Jatim.pha
	│   ├── README.md
	│   ├── hypoDD
	│   │   ├── cygwin1.dll
	│   │   ├── dt.ct
	│   │   ├── event.dat
	│   │   ├── event.sel
	│   │   ├── hypoDD.exe
	│   │   ├── hypoDD.inp
	│   │   ├── hypoDD.loc
	│   │   ├── hypoDD.log
	│   │   ├── hypoDD.res
	│   │   ├── hypoDD.sta
	│   │   └── station.dat
	│   ├── ph2dt
	│   │   ├── cygwin1.dll
	│   │   ├── dt.ct
	│   │   ├── event.dat
	│   │   ├── event.sel
	│   │   ├── ph2dt.exe
	│   │   ├── ph2dt.inp
	│   │   └── ph2dt.log
	│   └── station.dat
	└── [4] Plot Result
		├── A.dat
		├── Jatim_Katalog.bat
		├── Jatim_Katalog.png
		├── Jatim_hypoDD_reloc.bat
		├── Jatim_hypoDD_reloc.png
		├── README.md
		├── event.dat
		├── hypoDD.reloc
		├── kedalaman.cpt
		├── kedalaman1.cpt
		├── kedalaman2.cpt
		├── palet1.bat
		├── palet2.bat
		└── station.dat



# 3. Daerah Penelitian
Begian ini adalah pendahuluan untuk menampilkan daerah penelitian yaitu daerah Jawa Timur. 

Double klik pada file `Jawa_Timur.bat` maka akan menghasilkan gambar sebagai berikut : 
     
![jawa_timur](/img/Jatim.png)

**Keterangan**

 - `Bintang warna merah` adalah episenter gempabumi utama Mw 7.1, 28 September 2018 
 - `Segitiga tebalik warna kuning` adalah stasiun yang digunakan dalam penelitian
 - `Garis warna biru dengan label huruf` adalah garis cross-section dimana irisan seismisitas akan di tampilkan
 - `Segitiga warna merah` adalah gunung api
 - `Garis merah` adalah sesar 
 - `Bathymetri` yang digunakakan adalah srtm_15


# 4. Data dan Software

## Data
- Data yang digunakan adalah data arrival time repository gempabumi seicomp Stasiun Geofisika Pasuruan daerah Jawa Timur tahun 2015 -2021.

## Software-software yang digunakan yaitu :
  - [Python](https://www.python.org/) dan `Matlab` Untuk konversi format data 
  - [GMT](https://www.generic-mapping-tools.org/) Untuk visualisasi hasil  (tutorial ini menggunakan GMT4) 
  - [HypoDD](https://www.ldeo.columbia.edu/~felixw/hypoDD.html) Program utama relokasi hiposenter
  - [Notepad++](https://notepad-plus-plus.org/downloads/) Untuk menampilkan meng-edit script maupun hasil program. Dapat juga menggunaakan text editor lain sesuai keinginan  
  - [Cygwin](https://www.cygwin.com/) Untuk menjalankan program `HypoDD` 


# 5. Convert Data

Langkah-langkah konversi data input pada hypoDD.

# Langkah-langkah

1. Siapkan file `Jatim.txt`. File tersebut adalah hasil filter data sebagaimana dijelaskan langkah-langkahnya  [berikut](https://github.com/muhajiranshori/Tomografi-Simulps12/tree/main/%5B1%5D%20Filer%20Katalog)
2. Jalankan script `cat2pha.py` yang akan menghasilkan file `Jatim.pha`

``` python
import cat2pha
cat2pha(input_file='jatim.txt' output_file='jatim.pha')
```


3. Pindahkan file `Jatim.pha` tersebut ke dalam folder `[3] HypoDD` untuk proses selanjutnya.

## Catatan 

Nama file iput dan output harus di edit atau di sesuaikan dengan nama data anda ( Lihat script dengan text editor)


