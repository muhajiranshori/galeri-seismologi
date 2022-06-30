---
title: "Mengolah Data Sentinel"
date: 2022-02-11T06:36:55+07:00
draft: false
toc: true
comments: true
categories:
- inSAR
- sentinel_1
- surface_deformation
tags:
- windows
- linux
---

# 1. Pendahuluan

Sentinel adalah satelit Uni Eropa yang diluncuyrkan untuk berbagai keperluan diantaranay untuk studi defromasi permukaan akibat, pertanian dan lain-lain.

Satelit ini mampu mendeteksi terjadinya deformasi permukaan dalam orde milmeter. Data -nya pun dapat didownload secara gratis. Canggih bukan ?

Misal terdapat gempa besar di darat yang merusak dan menimbulkan deformasi di permukaan, atau juga ada gunungapi yang akan atau sedang meletus, maka perubahan deformasnya dapat di ketahui menggunakan data ini.

Beirikut ini beberepa contoh hasil pengolahan data.

Lantas apa beda sentinel 1, 2 dan 3 ?

Sentinel 1. 

Sentinel 2.

Sentinel 3. 

Beberapa paper yang menggunakan data sentinel untuk mengetahui deformasi permukaan akibat gempa diantanranya adalah :


Lantas bagaimana cara mendownload data sentites sekaligus pengolaannya ?

Mari kita praktekkan.

# 2. Download Data Sentinel

- Pertama yang harus anda lakukan adalah membuat akun copernicus terlebih dahulu dengan makukan sign up pada alamat **berikut**
- Setelah anda memiliki akun, silakan login terlebih dahulu.

Karena ukuran datanya besar, maka pengolahannya pun memebutuhkan komputer dengan spec cukup tinggi sehinga pastikan komputer anda memiliki kapasitas ram minimal 16 GB. Jika kurang dari itu, processing tetap bisa berjalan namun membutuhkan waktu yang cukup lama terutama pada taha coregistration data.

Jangan lupa untuk mematikan program-program lain pada komputer anda saat processing SNAP berjalan.

# 3. Langkah Pengolahan Data Sentinel

Kali ini kita akan praktek meggunakan data sentinel 1 sensor SLC daerah Jawa Timur yang terekam pada tanggal 19 dan 31 Desember 2021. 

Berikut adalah langkah-langkah pengolahan data sentinel :

## Membuka Data

Tampilan data dengan cara buka Band lalu double klik pada intensity

## Coregister Data

data akan terbentuk memiliki akhiran `Orb_Stack`

## Membuat Interferogram

data akan terbentuk memiliki akhiran `Orb_Stack_ifg`

## TOPS Deburst

data akan terbentuk memiliki akhiran `Orb_Stack_ifg_deb`

## Topographic Phase Removal

data akan terbentuk memiliki akhiran `Orb_Stack_ifg_deb_dinsar`

## Multi-looking

data akan terbentuk memiliki akhiran `Orb_Stack_ifg_deb_dinsar_ML`

## Phase Filtering

data akan terbentuk memiliki akhiran `Orb_Stack_ifg_deb_dinsar_ML_flt`

Kali ini saya akan menggunakan linux wsl.




