---
title: "Simpan"
date: 2022-05-31T00:06:31+07:00
draft: true
---

### cara menghapus environmnet
conda remove --name eqt --all

# PSSAC

Jika anda ingin menampilakn waveform dengan perintah seperti GMT, maka pssac adalah jawabannya. 

Sebenarnya versi asli pssac adalah sebagai berikut, anda harus mengcompilenya terlebih dahulu baru dapat menggunakannya.

Namun sekarang anda tidak perlu repot-repot melakukannya, cukup install GMT5 dan pssac sudah ada di dalamnya.

Ok, kita kaan praktek pssac pada GMT5. Saya anggap anda sudah berhasil menginstall GMT5, jika belum lihat petunuk berikut.

 Begian ini adalah pendahuluan untuk menampilkan daerah penelitian yaitu daerah Palu Sulawesi Tengah dimana pada tanggal 28 September 2018 telah terjadi gempabumi dengan Mw 7.1 serta menimbulkan tsunami dan liquifaksi yang menlan ribuan korban jiwa.  

Beberapa bagian pada tutorial selalu di awali dengan filter data karena agar lebih praktis kita menyediakan sebuah data arrival time secara utuh untuk kegempaan seluruh indonesia yang kemudian akan di filter berdasarkan area penelitian tertentu.

Beberapa bagian pada tutorial selalu di awali dengan filter data karena agar lebih praktis kita menyediakan sebuah data arrival time secara utuh untuk kegempaan seluruh indonesia yang kemudian akan di filter berdasarkan area penelitian tertentu.


1. Filter Katalog (Pelengkap)
2. Velest
3. Simulps12
4. HypoDD
5. EQTransformer
6. Hypoinvers
7. Hypoellipse
8. GMT
9. Tips GMT (Pelengkap)
10. SAC
11. Moment Yagi
12. Cluster K-Mean Spesific area JCOP
13. ANCC
14. QSeis
15. sac2mseed
16. mseed2sac
17. Obspy
18. Download Waveform
19. Picking Seisgram
20. 




Langkah pertama adalah mendownload converter **[disini](https://github.com/irisedu/stationxml-seed-converter)**. Ekstrak dan simpan file converter yang telah berhasil
didownload di dalam sebuah direktori pada komputer anda

Langkah kedua adalah memastikan komputer anda telah terinstall java. Terdapat
banyak tutorial cara menginstall java di internet, silakan mencarinya. Apabila sudah
menginstall java, lakukan test dengan mengetik perintah (java -version) pada command
prompt, apabila muncul seperti Gambar 2 berikut maka komputer anda telah terinstall
java dan mampu menjalankan program-program berbasis java.

Langkah ketiga adalah menyediakan metadata stasiun berformat *.xml. Metadata
stasiun dapat didownload salah satunya melalui webdc seperti Gambar 3 di bawah ini.
Tentukan telebih dahulu stasiun seismik mana saja yang akan didownload metadatanya,
lalu edit start dan end pada isian time window dengan sebarang waktu asalkan masih
tercakup dalam waktu beroperasinya stasiun seismik. Pilih Request Type Metadata
(StationXML) dan Metadata Level Response lalu tekan submit. Buka tab download lalu
pilih save untuk menyimpan file metadata yang telah kita request