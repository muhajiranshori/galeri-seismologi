---
title: "Tomografi Simulps12 Part 2 Membuat Grid Node"
date: 2021-05-04T17:14:18+07:00
draft: false
toc: false
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

# #3 Grid Node

 - Penentuan grid node adalah tahapan penting dalam tomografi. 
 - Grid node adalah titik-titik imajiner yang kita definisikan sebelum melakukan pemodelan tomografi dimana nilai kecepatan seismik secara spasial akan direpresentasikan oleh nilai kecepatan pada titik-titik tersebut. Oleh karena itu kita harus memastikan bahawa grid node yang kita tentukan telah meng-cover area penelitian dengan baik. Jika lokasi hiposenter maupun stasiun terletak di luar grid node, maka proses pemodelan akan error. 
 - Kerapatan grid node akan menentukan tingkat resolusi tomogram yang akan dihasilkan, semakin rapat semakin tinggi resolusi. 
 - Akan tetapi tingkat kerapatn grid node juga harus di sesuaikan dengan kondisi data sebaran stasiun.  

# Berikut adalah langkah-langkah praktis dalam penentuan grid node 

1. Edit file `Pusat.txt` yang berisi koordinat pusat grid node ( lintang, bujur). Biasanya ditentukan dari titik tengah daerah penelitian.  
2. Edit file `grd.txt` yang berisi jarak antar grid pada arah x (bujur) dan arah y (lintang) dalam satuan km.
3. Jalankan script `grd.m` yang akan menghasilkan file `GRD.txt`. File tersebut berisi koordinat grid node (lintang, bujur)
4. Untk mengetahui apakah koordinat grid node yang kita buat telah sesuai atau tidak maka lakukan plotting dengan script `Grid_Node.bat`. Sebaiknya plotting grid node di-overlay juga dengan plotting lokais episeter dan statsiun yang digunakan dalam penelitian. Hal ini dilakukan untuk memastikan bahwa grid node yang kita tentukan sudah cukup meng-cover lokasi episenter dan stasiun. Jika kurang sesuai misal masih ada event ynag terletak diluar grid node, maka ulangi tahan 2 dan 3 dengan merubah jarak antar grid nya.   

## Berikut adalah hasil plotting grid node menggunakan script `Grid_Node.bat`

![grid_node_mamasa](https://user-images.githubusercontent.com/28419810/108687227-0866dd00-7529-11eb-9881-db34b9a0fb90.png)