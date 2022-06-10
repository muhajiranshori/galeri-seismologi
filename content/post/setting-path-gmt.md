---
title: "Setting PATH GMT"
date: 2020-02-22T17:10:53+07:00
draft: false
comments: true
categories:
- mapping_tool
tags:
- GMT
- Batch
---

Selamat malam sahabat, jumpa lagi kita di Galeri Sesmologi.

Saya kembali akan mengetengahkan tips receh yaitu bagaimana cara menjalankan GMT 2 versi misla versi 4 dan versi 5 pada komputer kita namun switch nya mudah.

Biasanya kasusnya adalah kita sudah terlanjur memiliki script GMT versi 4 namun enggan untuk merubah atau mengadaptasikannya menjadi versi 5 karena memang ada beberapa perbedaan.

Di sisi lain terkadang kita juga butuh fitur yang hanya tersedia di GMT5 misal nya fitur pssac untuk plot waveform. 

Nah saya pribadi mengatasi problem tersebut debfab cara berikut :

Tentu anda sudah pada bisa dong cara menginstall GMT, kalo belum silakan simak caranya **disini**.

Ini kita bicara untk windows yaa.

Apa kita harus menginstall setiap versi jika ingin menjalankan salah satunya ? tenang, anda tidak perlu serepot itu.

Everything gonna be easy...


Caranya adalah  jangan membuat setting envirinment variabel GMT anda, jika terlanjur tersetting maka hapus saja.

Cara nya klik kanan - path - clear

Jika anda ingin menjalankan GMT 4, tambahkan perintah ini pada script anda :

	set path=C:\programs\GMT4\bin;%PATH%

Jika anda ingin menjalankan GMT 4, tambahkan perintah ini pada script anda :

	set path=C:\programs\GMT5\bin;%PATH%

Tentu alamat path nya menyesuaikan dengan alamat pada komputer anda dimana GMT 4 dan 5 terinstall.


Mudah bukan ?...Bukan !