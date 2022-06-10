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


Data yang digunakan adalah data arrival time repository gempabumi BMKG tahun 2018 studi kasus gempa Palu Mw 7.1, 28 September 2018.



# 4. Membuat Grid Node

# 5. Running Simulps12







# 7. Plot Hiposenter Hasil Relokasi


Sebuah media untk saling berbagi dan berdiskusi seputar dunia seismologi.

Catatan-catatan ini saya tulis sebagai sebuah dokumentasi proses belajar yang saya lakukan.

Semua konten pada blog ini dapat anda baca, copy, praktekkan 


SEMOGA BERMANFAAT. 

Halo semua, ini adalah postingan pertama saya. Selamat datang di Galeri Seismologi, sebuah media untuk saling berbagi dan berdiskusi seputar dunia seismologi.

Bagi anda mahasiswa ilmu kebumian, akademisi, praktisi kegempaan atau siapapun yang cinta dengan bidang ini, mari bergabung dan belajar bersama.

Catatan-catatan ini saya tulis sebagai sebuah dokumentasi proses belajar yang saya lakukan dan semoga dapat bermanfaat bagi kita semua

Salam  

Setiap material, baik tulisan, persamaan matematika dan gambar yang tertera pada blog ini ditujukan untuk keperluan pendidikan semata. 
Setiap tulisan, persamaan maupun gambar yang diambil dari tempat lain diberikan keterangan autorisasi. 
Penulis berusaha semaksimal mungkin untuk menghargai hak cipta dari hasil karya orang lain dan berupaya untuk membaca dengan teliti mengenai perjanjian hak cipta. Jika penulis melakukan kekeliruan, dan pemilik hak cipta keberatan, penulis bersedia untuk mencabut gambar, tulisan, maupun persamaan yang tertera dalam blog ini. Karena Blog ini ditujukan untuk keperluan pendidikan, penyalahgunaan selain untuk keperluan pendidikan diluar tanggung jawab pemilik blog. Anda dipersilakan untuk meng-copy, paraphrase dan quote sepanjang mencantumkan sumbernya.


Mengapa perlu dilakukan relokasi ? 

Salah satu alasannya adalah seringnya terdapat fix depth pada data.

Berikut saya tunjukkan contoh fix depth pada kegempaan di bawah gunungapi anak krakatau.



Setelah direlokasi, gempa yang tadinya dominan berada pada kedalaman 10 km menjadi bergeser memebentuk suatu cluster di bawah gunungapi.

Itulah salah satu guna dari relokasi hiposneter.

Lantas bagaimaan cara melakukannya ?

Siapkan kopi, duduk yang manis karena step-nya cukup panjang.

Mari kita mulai.


-----------------------

Bagi anda yang ingin menggunakan software ini silakan download secara gratis **disini** dan jangan lupa mensitasi papaer **ini**.












