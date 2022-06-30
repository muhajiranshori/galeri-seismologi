---
title: "Tutorial EQTransformer"
date: 2021-08-10T13:30:56+07:00
draft: false
toc: true
comments: true
categories:
- machine_learning
- deep_learning
- earthquake_detection
tags:
- windows
- linux
- python
---

# Pendahuluan

Pernah dengar istilah **Machine Learning ?** **Deep learning ?**

Saya yakin pernah, kebetulan 2 istilah tersebut sering berseliweran di jagat maya. 

Machine Learning (ML) adalah metode pembuatan sebuah program dimana kita tidak perlu memasukkan perintah explisit ke dalamnya. 

Lantas bagaimana sistem kerjanya ?

Pertanyaan yang bagus. 

Sistem kerjanya adalah dengan mendesain program agar mampu mempelajari pola atau fitur yang terkandung di dalam data untuk kemudian menyimpannya menjadi sebuah model sehingga model tersebut dapat dipergunakan untuk memprediksi data yang lain.

Lalu apa itu **Deep learning (DL)** ? DL adalah bagian dari ML namun dengan ciri khas algoritmanya mengandung banyak *layer* dalam proses mempelajari data.

**ML** dan **DL** serta kawan-kawannya tidak kita bedah pada artikel ini, disini kita akan mengulas tentang  **EQTransformer (EQT)**.

*EQTransformer (EQT)* adalah sebuah program DL yang buat oleh Musthofa Mousavi pada tahun 2020, seorang ilmuan seismologi asal Iran.

EQT memiiliki kemampuan untuk mendeteksi sinyal gempa berikut pickingnya secara otomatis.

Bicara soal picking gempa secara otomatis, kan kita sudah lama kenal dengan STA/LTA ? 

Apa keunggulan EQT dibanding metode legendaris tersebut ?

EQT memiliki keungglan mampu membedakan mana gempa mana noise secara lebih baik di banding STA/LTA. Jika terdapat gangguan noise atau sejinisnya pada sensor, STA/LTA tetap akan menganggapnya sebgaai sebuah event, namun EQT mempu mengenalinya dengan baik.

EQT 
   
Pada artikel ini akan kami tunjukkan cara menjalankan EQT pada data offline, jika anda ingin melihat tutorial dg data onlien silakan simak disini.
   
   
## 1. Install EQT

Berikut cara menginstalnya :

Pastikan komputer anda telah terinstall conda ataupun miniconda. Silakan baca artikel **berikut**.

Spesifikasi komputer minimal harus memiliki RAM 8G (pernah saya coba pada laptop dengan RAM 4G dan gagal)

Jalankan perintah berikut pada terminal anda :
	
	conda create -n eqt python=3.7
	conda activate eqt
	pip install EQTransformer

	
Tunggu beberapa saat hingga proses intall berhasil, jika sudah selesai coba import modul eqtransformer dengan perintah seperti di bawah ini.


	Python 3.9.5 (default, May 18 2021, 14:42:02) [MSC v.1916 64 bit (AMD64)] :: Anaconda, Inc. on win32
	Type "help", "copyright", "credits" or "license" for more information.
	>>> import eqtransformer
    >>>

Jika tidak muncul error, maka proses install telah berhasil. 


## 2. Persiapan Data Waveform

Pada dokumentasi EQT **ini** telah telah dibahas cara melakukan otomatis deteksi dan *picking* menggukaan data online.

Nah disini kita akan belajar bagaimana cara menerapkan program EQT pada data lokal dalam hal ini waveform dalam format miniseed yang tersimpan pada komputer lokal kita.

Sebelumnya anda dapat membaca artikel saya sebelumnya tentang bagaimana cara mendownload waveform dalam format miniseed **disini**.

Saya akan gunakan cara ke-3 yaitu meng-copy waveform dari archive seiscomp.

Berikut adalah struktur data waveform saya  

	.
	├── archives
	│   └── 2021
			└── sta
	│	└── 2021
	├── config - Copy.toml
	


## 3. Menjalankan EQTransformer

Sebelum menjalankan EQT bahan-bahan apa saja yang harus disiapkan ??

1. File jason station
2. File 
3. File	
	
	
	
Tutorial tersebut adalah jika anda ingin melakukan autodeteksi dan autoipicking pada data lokal namun tidak secara real time.

Bagaimana jika anda memiliki data waveform yang terupdate secara real time ? misal data archive waveform pada seiscomp.

Silakan simak pada artikel saya selanjutnya berikut **ini**. 

Setelah kemarin kita belajar cara meng-install EQT hingga siap digunakan, kali ini kita langsung praktek menggunakan EQT untuk mendeteksi gempa swarm Ambarawa yang terjadi pada Bulan Oktober 2021.

Berdasarkan adata katalog Satsiun Geofisika Pasuruan, terdaoat 24 event gempa ambarawa dalam kurun waktu antara tanggal 1 - 25 Oktoer 2021.

Jumlah tersebut bisa berbeda untuk stasiun observasi yang lain, mengingat stasiun yang dijalankan di seiscomp bisa jadi berbeda.

Data saya peroleh dari seiscomp yaitu dari folder `/home/seiscomp/val/lib/2021/.../

Struktur folder nya dalah sebagai berikut.

Saya hanya meng-copy data miniseed pada tgl 1 - 12 Oktober 2021
	
	
	
	
	