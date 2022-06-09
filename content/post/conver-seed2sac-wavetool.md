---
title: "Conver Seed2sac Wavetool"
date: 2022-06-06T12:03:37+07:00
draft: false
toc: true
comments: true
categories:
- convert_waveform
tags:
- windows
- seisan
- wavetool
---

# 1. Pendahuluan
Kita akan belajar cara merubah format data waveform dari seed/mseed mnejadi sac menggunkan wavetool.

Apa itu wavetool ?

Wavetool adalah sub program yang terdapat paad seisan. Jadi dengan anda menginstall seisan maka pasti sudah terdaat wavetool di dalamnya. **Berikut** adalah cara install seisan.

# 2. Cara convert seed/mseed menjadi sac

Ketik perintah 

``` 
wavetool
```

# 3. Cara convert seed/mseed menjadi sac secara massal

Langkah sebelumnya adalah contoh cara meng-convert file single.

Bagaimana jika anda memeiliki ribuan file miniseed ? tidak mungkin akan kita convert satu persatu.

Terdapat cara untuk meng-convert nya secara massal yaitu dengan menggunakan bantuan program `dirf`.

Berikut adalah langkah-langkahnya :

- jsjs
- kskksk 



Beda gak sih sac hasil konversi dari miniseed dan seed ?

Jelas berbeda

Letak perbedaannya adalah pada headernya. Pada artikel **ini** saya sudah mengulas sekilas tentang header sac.

Ini adalah header file sac hasil konversi dari `miniseed`


Sedangkan ini adalah header file sac hasil konversi dari `seed`


File sac hasil konversi dari full seed memiliki konten header yang lebih lengkap yaitu evla, evlo, dist dan lain-lain.