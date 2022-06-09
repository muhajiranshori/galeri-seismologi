---
title: "Tutorial Seizmo"
date: 2021-12-18T17:30:56+07:00
draft: false
toc: true
comments: true
categories:
- waveform_treatment
- sac
tags:
- windows
- matlab
- seizmo
---

# 1. Pendahuluan
Seizmo adalah program berbasis matlab yang dikenbangkan oleh Garreth Euler dari washington unoversity.

Di dalamnya terkandung banyak sekali modul-modul untuk pengolahan waveform.

# 2. Instalasi

Berikut adalah cara install-nya.

Disini saya menggunakan OS Windows 10 dan Matlab versi 2016. 

Download master seizmo **[disini](https://github.com/g2e/seizmo/archive/master.zip)** 

Ekstak ke dalam suatu folder misal `E:\Muhajir\Seizmo\`

Buka program `Matlab`, ubah direktori kerja lalu ketikkan `install_sezmo` pada direktori kerja

# 3. Cara Penggunaan

Untuk menggunakannya anda dapat membaca help, caranya ketikkan

``` matlab
help seizmo
```

maka akan muuncul

## Contoh penggunaan

Berikut kami tunjukkan cara membaca sinyal secara masal 

**RD.m**

``` matlab
data=readheader('*')
      data=data(strcmpi(getheader(data,'iftype id'),'itime'))
      data=readdata(data)
```

**qh.m**
``` matlab
queryheader(data,'kzdate','kztime')
```

### Plot Waveform

