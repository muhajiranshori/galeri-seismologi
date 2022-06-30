---
title: "nb_conda_kernels"
date: 2020-02-07T09:21:17+07:00
draft : false
toc: true
comments: true
categories:
- jupyter_notebook
- nb_conda_kernels
- conda_environment
tags:
- linux
- windows
- wsl 
- python
---

Kemarin kita sudah belajar bagaimana cara meng-install **jupyter notebook** berikut tips-tips penggunaanya.

Bagi anda yang sering menggunakan beberapa macam software berbasis python dengan beragam ruang environment (env) yang diatur dengan conda, maka tiap kali anda ingin berpindah `env`, anda harus mengetikkan perintah 

``` 
conda activate <env_name>
```



Jika anda bekerja hanya pada terminal, hal ersebut akan dapat dengan  mudah dilakukan namun lain cerita jika anda menggunakan jupyter notebook.

Misalnya jika anda sedang bekerja dengan env eqtransformer kemudian tiba-tiba anda ingin berpindah ke env yang lain untuk mengerjakan hal yang berbeda, maka anda harus *log out* jupyer notebook anda terlebih dahulu baru mengktifkan `env` yang berbeda, kemudian masuk lagi ke dalam jupyter notebok yang baru. 

Kedengarannya cukup merepotkan.

Adakah cara termudah mengatasi masalah tersebut ?

Caranya adalah dengan menginstall **conda-kernel**

Dengan conda-kernel maak jupyter akan mengenali semua env yang yelah anda install dan anda dapat berpindah env melalui senuah menu pada jupyter itu sendiri tanpa harus menutupnya dan mengetikkan perintah pada terminal.

Mari kita simak caarnya. 