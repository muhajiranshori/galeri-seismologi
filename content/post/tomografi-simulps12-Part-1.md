---
title: "Tomografi Simulps12 Part 1 : Persiapan Data"
date: 2021-03-02T17:14:18+07:00
draft: false
toc: true
comments: true
categories:
- earthquake_relocation
- tomography
- ray_tracing
- checkerboard_test
tags:
- cygwin
- python
- simulps12
---
# 1. Pendahuluan

Kalo dalam dunai kedokteran kita mengenal CT-Scan, maka dalam dunia ilmu kebumian kita mengenal tomografi.

Dengan CT-Scan kita dapat melihat bagian dalam tubuh manusia tanpa harus membedahnya, maka dengan tomografo kita dapat melihat isi perut bumi seperti mantel, lempeng yang tersubduski, magma dan lain sebagainya tanpa harus menggalinya.

Lantas bagaimana hal tersebut bisa dilakukan ? caranya dalah dengan menggunakan bantuan sinar gelombang seismik yang dihasilkan oleh gempabumi yang menjalar ke seluruh bagian bumi dan diterima oleh seismometer.

Sinar seismik yang menjalar tersebut akan mengalami perlambatan ataupun percepatan tergantung pada karakteristik medium yang dilaluinya. Untuk lebih jelasnya tentang teori dasar tomografi dapat anda baca pada artikel **[berikut](/post/moment-yagi/)**. 

Langkah-langkah tomografi pada artikel ini cukup panjang sehingga saya akan membaginya menjadi beberapa Part yaitu :

- Part 1 : Persiapan Data
- Part 2 : Membuat Grid Node
- Part 3 : Running Simulps12
- Part 4 : Plotting Hiposenter Hasil Relokasi
- Part 5 : Plotting Tomogram
- Part 6 : Plotting Residuals
- Part 7 : Membuat Ray Tracing
- Part 8 : Membuat Uji Resolusi
- Part 9 : Membuat Kurva *Trade Off*
- Part 10 : Plotting Tomogram Berdasarkan Daerah Teresolusi

# 2. Struktur Folder

	(base) muhajir@galeri-seismologi:/mnt/e/GALERI_SEISMOLOGI/Tomografi-Simulps12$ tree
	.
	├── README.md
	├── [1] Filer Katalog
	│   ├── Catalog_Filter.py
	│   ├── Mamasa.pha
	│   ├── Mamasa.txt
	│   ├── Seismisitas_Mamasa.bat
	│   ├── Slice_Mamasa.bat
	│   ├── cat2event.py
	│   ├── cat2pha.py
	│   ├── cat_event_Mamasa.dat
	│   ├── kedalaman.cpt
	│   ├── kedalaman2.cpt
	│   └── tmp
	├── [2] Convert Input Data
	│   ├── Mamasa.pha
	│   ├── Mamasa.txt
	│   ├── Mamasa_sta.txt
	│   ├── Simulps.m
	│   ├── cat2event_mamasa.py
	│   ├── cat_event_Mamasa.dat
	│   ├── earthq.dat
	│   ├── getPSinStation.m
	│   └── seiscomp2pha_edit.py
	├── [3] Grid Node
	│   ├── A.dat
	│   ├── GRD.txt
	│   ├── Grid_Node.bat
	│   ├── Pusat.txt
	│   ├── STA1.dat
	│   ├── cat_event_Mamasa.dat
	│   ├── grd.m
	│   ├── grid.txt
	│   ├── grid_node_mamasa.png
	│   ├── kedalaman1.cpt
	│   ├── palet.bat
	│   └── tmp
	├── [4] Simulps12
	│   ├── control.dat
	│   ├── cygwin1.dll
	│   ├── del.bat
	│   ├── earthq.dat
	│   ├── fort.13
	│   ├── fort.16
	│   ├── fort.20
	│   ├── fort.22
	│   ├── fort.23
	│   ├── fort.24
	│   ├── fort.26
	│   ├── fort.36
	│   ├── simulps.exe
	│   ├── simulps.ms.pdf
	│   ├── simulps12.f
	│   ├── simulps_common.inc
	│   ├── stations.dat
	│   ├── velocity.dat
	│   └── velocity_ckb.dat
	├── [5] Ray Tracing
	│   ├── RT_Mamasa.ps
	│   ├── Ray_Tracing.bat
	│   ├── STA1.dat
	│   ├── control.dat
	│   ├── cygwin1.dll
	│   ├── del.bat
	│   ├── earthq.dat
	│   ├── ray.bat
	│   ├── ray.dat
	│   ├── rays.dat
	│   ├── simulps.exe
	│   ├── stalat.dat
	│   ├── stalon.dat
	│   ├── stations.dat
	│   └── velocity.dat
	├── [6] Plot Relocated EQ
	├── [7] Plot Tomogram
	└── [8] Checkerboard Test


# 3. Persiapan Data

Data yang digunakan pada artikel ini adalah data arrival time gempabumi di daerah Selat Sunda dan sekitarnya tahun 2009 - 2015.

## Filter Katalog

Jika anda bekerja dengan katalog *arrival time* maka tahap awal yang harus anda lakukan adalah filter data katalog agar data yang anda olah lebih spesifik. 

Bagaimana cara melakukannya, baca petunjuknya **[disini](/post/filter-data-katalog/)**.


## Convert Data

Convert data dilakukan unruk merubah format data dari format katalo *arrival time* menjadi format input `simulps12`

Cara nya adalah sebegai berikut :

  


# 4. Plot Seismisitas

Untuk keperluan visualisasi data, lakukan plotting seismisitas menggunakan `GMT4` dengan langkah sebagai berikut :

1. Jalankan script `cat2event.py` untuk merubah format data `Mamasa.txt` menjadi `cat_event_Mamasa.dat` sesuai dengan definisi file input dan output pada baris 5 dan 6.
2. Jalankan script `Seismistas_Mamasa.bat` dan `Slice_Mamasa.bat` dengan terlebih dahulu mendefinisikan data input pada baris 5.

*Catatan : Jangan lupa menyediakan file pendukung yang terdapat disini dan mengedit baris 7 - 12 sesuai dengan path file pada komputer anda. 

**Hasil plot menggunakan script `Seismisitas_Mamasa.bat`**


**Hasil plot menggunakan script `Slice_Mamasa.bat`**





Catatan :

Gambar - gambar pada artikel ini adalah hasil tesisi yang dilakukan oleh Muhajir Anshori







