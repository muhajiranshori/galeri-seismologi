---
title: "Convert Metadata"
date: 2022-04-27T11:38:31+07:00
draft: false
toc: true
comments: true
categories:
- metadata
- waveform_treatment
tags:
- batch
---

# 1. Pendahuluan

Kali ini kita akan membahas cara merubah format metadata waveform dari `xml` menjadi `dataless`

Data seismik yang sering digunakan dalam seismologi adalah berformat seed
*(Stardard for the Exchange of Earthquake Data)*. Data seed bersifat praktis dan mudah
digunakan dalam banyak penelitian seismologi. Data ini memiliki struktur sederhana
yaitu berisi data time series sinyal berikut informasi metadata-nya. Metadata merupakan
informasi penting yang mendeskripsikan data time series diantaranya pewaktuan,
network, channel, komponen (horizontal dan vertikal), koordinat stasiun dan lain-lain.
Informasi tambahan dapat pula ditambahkan pada variabel header seperti koordinat event
gempabumi, arrival time beberapa fase sinyal seismik dan lain-lain.

Terdapat 2 tipe file seed yaitu miniseed dan full seed atau biasa disebut seed.
Miniseed adalah versi sederhana dari file seed dimana informasi pada metadata yang
terkandung di dalamnya hanya yang utama saja yaitu pewaktuan, network, channel dan
komponen. Beberapa server data seismologi ada yang masih menyediakan data dalam
fromat seed namun ada juga yang merubah layanannya menjadi hanya menyediakan file
miniseed, sedangkan metadatanya disediakan secara terpisah dengan fomat *.txt dan
*.xml.

Format metadata dapat berupa *.txt dan *.xml dan dapat pula berupa dataless.
Metadata dengan format dataless biasanya lebih sering digunakan daripada 2 format
sebelumnya. Salah satu fungsi dari metadata berformat dataless adalah sebagai bahan
untuk meng-convert data waveform dari format miniseed menjadi seed menggunakan
program rdseed dimana dalam proses konversinya membutuhkan tambahan informasi
yang terkandung pada file metadata. Makalah singkat ini bertujuan untuk menguraikan
cara merubah format metadata stasiun seismik dari format *.xml menjadi format dataless
menggunakan program stationxml-seed-converter agar kompatibel dengan program
rdseed.

# 2. Langkah convert metadata

## 2.1 Download Converter
Download converter **[disini](https://github.com/irisedu/stationxml-seed-converter)**. Ekstrak dan simpan file converter yang telah berhasil
didownload di dalam sebuah direktori pada komputer anda

## 2.2 Install Java
Pastikan komputer anda telah terinstall java. Terdapat
banyak tutorial cara menginstall java di internet, salah satunya **ini**. Apabila sudah
menginstall java, lakukan test dengan mengetik perintah 
```
java -version
```
apabila muncul seperti di bawah ini maka komputer anda telah terinstall
java dan mampu menjalankan program-program berbasis java.

	java version "1.8.0_301"
	Java(TM) SE Runtime Environment (build 1.8.0_301-b09)
	Java HotSpot(TM) Client VM (build 25.301-b09, mixed mode, sharing)


## 2.3 Sediakan metadata xml
Sediakan metadata stasiun berformat *.xml. Metadata
stasiun dapat didownload salah satunya melalui webdc seperti Gambar 3 di bawah ini.
Tentukan telebih dahulu stasiun seismik mana saja yang akan didownload metadatanya,
lalu edit start dan end pada isian time window dengan sebarang waktu asalkan masih
tercakup dalam waktu beroperasinya stasiun seismik. Pilih Request Type Metadata
(StationXML) dan Metadata Level Response lalu tekan submit. Buka tab download lalu
pilih save untuk menyimpan file metadata yang telah kita request

