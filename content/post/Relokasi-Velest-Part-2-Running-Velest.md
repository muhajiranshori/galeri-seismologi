---
title: "Relokasi Velest Part 2 Running Velest"
date: 2021-04-10T11:21:40+07:00
draft: false
toc: true
comments: true
categories:
- earthquake_relocation
- 1-D_model_determination
tags:
- linux
- python
- velest
- GMT
---

# 6. Running Velest
 - Tahapan ini kita akan belajar cara mengoperasikan program velest.
 
## File yang harus dipersiapkan

 - `AK135.mod` berisi nilai kecepatan seismik 1-D sebagai nilai kecepatan awal
 - `Palu.cnv` berisi nilai travel time observasi hasil konversi pada tahap [sebelumnya](https://github.com/muhajiranshori/Relokasi-Velest/tree/main/%5B2%5D%20Convert%20Data)
 - `Palu.sta` berisi data stasiun yang digunakan
 - `velest` program velest untuk relokasi hiposenter ( dijalankan under Linux)
 - `velest.cmn` berisi setting parameter. Nama file input dan output didefinisikan pada file tersebut.

## Langkah-langkah running velest

1. Siapkan file-file yang telah disebutkan di atas
2. Buka terminal linux lalu masuk ke dalam folder `Relokasi-Velest/"[3] Velest"/`
3. Jalan program `velest` dengan perintah 

  ``` 
  ./velest
  ```

**maka akan menghasilkan file**  

 - `Palu.OUT` berisi hasil keseluruhan dari proses relokasi hiposenter yang dilakukan oleh program `velest`
 - `stacor_Palu.OUT` bersisi nilai stasiun koreksi
 - `velout.MOD` berisi nilai kecepatan seimsik 1-D final.

4. Pindahkan ke-3 file tersebut ke dalam folder `Plot Result` untuk tahap plotting.