---
title: "Waveform Alignment"
date: 2022-04-08T17:08:16+07:00
draft: false
comments: true
categories:
- waveform_treatment
tags:
- linux
- sac
---

# 1. Pendahuluan

Halo selamat pagi, jumpa lagi kita di Galeri Seismologi.

Kali ini saya akan menyajikan tutorial receh berikutnya yaitu bagaimana caranya mensejajarkan waveform ?

Maksudnya bagaimana ?

Jika bekerja dengan waveform 3 komponen, dan program yang akan anda gunakan hanya akan memanggil sukuen data, maka anda perlu berhati-hati karena seringkali waveform yang telah kita unduh belum sejajar.

Berikut adalah contohnya

`Gambar plot 1 seizmo`

Lantas bagaimaan mengatasinya ? Mari kita simak.

# 2. Cara mensejajarkan waveform

Berikut adalah langkah-langkahnya :

- Langah pertama siapkan terlebih dahulu file waveform dalam format miniseed.

- Edit script berikut

```
abcdefgh
```

Ubah baris ke-7 dengan `origin time` event

- Jalankan script dengan perintah

```
bash script.sh
```

Maka akan dihasilkan file xxxx.seed


Catatan :

Secara teknis metode ini saya khususkan untuk bagian **raw data preparation** pada tutorial **[Moment]**. 