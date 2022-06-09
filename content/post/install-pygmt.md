---
title: "Install pyGMT"
date: 2021-09-18T17:30:16+07:00
draft: true
toc: true
comments: true
categories:
- installation
- mapping_tool
tags:
- python
- miniconda
- linux
- windows
---

Beriku adalah cara install pyGMT

``` bash
conda create -n pyGMT python=3.7
conda activate pyGMT
conda install pyGMT
```

Namun jika anda ingin meng-install pada env tertentu misal env eqtransformer, maka setelah anda selesai menginstall EQT maka :

aktifkan EQT lalu install pyGMT

``` bash
conda activate eqtransformer
conda install pyGMT
``` 

Nah sekarang, module pygmt sudah ada dalam eqt

coba dengan perintah 

``` python
import pygmt
```

jika tidak muncul error, maka pygmt telah berhasil terinstall 