---
title: "Tomografi Simulps12 Part 7 Membuat Ray Tracing"
date: 2021-05-14T16:28:13+07:00
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

Jika pada pembahasan sebelumnya kia sudah belajar 

Halo selamat pagi, kali ini kita akan membahas tentang cara membuat ray tracing. Tentu temen2 sering melihat pada paper2 tomografi tampian ray tracing yaitu garis2 yang mengubungkan antara soure ( gempa) dan receiver ( sesimograf ). Pada artikel ini saya tidak membahas ttg metode2 ray tracing namun hanya sekedar bagaimana cara membuat dan menampilkannya. 
Apa pentingnya ray tracing ? disamping untuk keperluam visualasasi, RT berguna untuk menganalisis tingkat resolusi tomogram yh dihasilkan dimana kita bisa tahu daerah2 mana saja yg tercover sinar seismik secara rapat dan yang tidak. Walaupun hal tersrbut secara lebih akurat dapat dilakukan dengan metode uji resolusi tomografi seperti chcekrboard test, DWS, KHIT. Apa itu CRT, DWS, KHIT ? lagi2 kan kita bahas pada artikel berikutnya.
Bagi anda yang sudah membaca artikel ttg simulps tentu tentu akan mengerti bahwa program tsb memiliki beberapa output. Output yg dihasilkan tergantung pada setting file control. Untuk mnghasilkan output data ray tracing set file control baris ke 3 dg 1 0 0 1. Maka akan dihasilkan file *.rt setelah proses running selesai.

![ray_tracing_P](/img/simulps12/Ray_Tracing_P.png)



![ray_tracing_S](/img/simulps12/Ray_Tracing_S.png)
