---
title: "Tomografi Simulps12 Part 8 Membuat Uji Resolusi"
date: 2021-03-18T16:28:36+07:00
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

# 9. Memuat Checkerboard Test (CRT)

Kurang afdhol rasanya jika membuat tomogram tanpa membuat *Checkerboard Test (CRT)* ibarat kata makan soto tanpa kerupuk. 

CRT adalag sebuah metode uji resolusi tomografi yang sangat populer atau hampir pasti menjadi menu wajib pada setiap sajian paper tomografi.

Metode ini dilakukan dengan membuat initial model dengan nilai parameter selang-seling menyerupai papan catur (biasanya plus minus sekian persen dari model awal yang digunakan). 

CRT mampu merepresentasikan resolusi spasial dari tomogram yang kita sajikan berdasarkan tingkat pemulihan model *checkerboard*.

Bagaimana cara bikinnya ? mari kita praktekkan.

Cara yang dilakukan sama persis dengan tahan 3 diatas, namun dengan mengganti veloc.txt menjadi model *checkerboar* 

![checker_board](/img/simulps12/dVp_Horizontal_0.png)


![checker_board](/img/simulps12/dVp_ckb_test_20.png)
