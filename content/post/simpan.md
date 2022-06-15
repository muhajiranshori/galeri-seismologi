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

------------------------------------------------
Mengapa gempa perlu dilakukan relokasi ? 

Salah satu alasannya adalah seringnya terdapat fix depth pada data.

Berikut saya tunjukkan contoh fix depth pada kegempaan di bawah gunungapi anak krakatau.



Setelah direlokasi, gempa yang tadinya dominan berada pada kedalaman 10 km menjadi bergeser memebentuk suatu cluster di bawah gunungapi.

Itulah salah satu guna dari relokasi hiposneter.

Lantas bagaimaan cara melakukannya ?

Siapkan kopi, duduk yang manis karena step-nya cukup panjang.

Mari kita mulai.

-----------------------

Model kecepatab 1 dimensi yang digunakan adalah model koulakove 2007

-----------------------

Bagi anda yang ingin menggunakan software ini silakan download secara gratis **disini** dan jangan lupa mensitasi papaer **ini**.



git status

git add .

git commit -m "comment"

git push origin master

set path=C:\programs\GMT4\bin;%PATH%
     set F=Jatim.ps
     set R=109/116/-11.5/-4
     set GU=GU.dat
     set seis=seis.dat
     set M=mainshock.dat
     set GA=GA.dat
     set ST=station.dat
     set A=volcano.dat
     
     set P=E:/Muhajir/GMT/topo_putih.cpt
     set NC=E:/Muhajir/GMT/srtm_15_indo.grd
     set NC1=E:/Muhajir/GMT/srtm_15_indo.grd.int
     set sesar=E:/Muhajir/GMT/sesar.gmt
     set sesar2=E:/Muhajir/GMT/sesar2.gmt
     set sesar=E:/Muhajir/GMT/hajir.gmt
     set sesar2=E:/Muhajir/GMT/sesar2.gmt
     
     set SA=SA.d
     set SB=SB.d
     set SC=SC.d
     
     set LA=lineA.d
     set LB=lineB.d
     set LC=lineC.d
     
     set EA1=111.7580000
     set EA2=-6.00
     set CA1=111.7580000
     set CA2=-11.00
     
     set EA=%EA1%/%EA2%
     set CA=%CA1%/%CA2%
     
     set EB1=112.9200000
     set EB2=-6.00
     set CB1=112.9200000
     set CB2=-11.00
     
     set EB=%EB1%/%EB2%
     set CB=%CB1%/%CB2%	 
     
     set EC1=114.0000000
     set EC2=-6.00
     set CC1=114.0000000
     set CC2=-11.00           
     
     set EC=%EC1%/%EC2%
     set CC=%CC1%/%CC2%	 
            
               
     psbasemap -JM12c -R%R% -Ba2WSne:.":" --HEADER_FONT_SIZE=12 -P -K -Y15 -X2> %F%
     
     grdimage %NC% -R -J -C%P% -I%NC1% -V -K -O  >> %F%
     
     pscoast  -V -O -J -R -W1.5 -B2WSne -Lf110.0/-11.0/50/200 -T110/-10.0/0.9i -Slightblue -Df -K >> %F%
     
     rem gawk "{ print $8, $7*-1, $9, $10*0.015}" %I% | psxy -R -J -O -Ckedalaman1.cpt -Sci -W1.0 -K >> %F% 
     
     gawk "{print $2, $1}" %ST% | psxy -JM -R -Si0.20c -W2 -Gyellow  -O -K >>%F%
     gawk "{print $1, $2}" %A% | psxy -JM -R -St0.15c -W2 -Gred  -O -K >>%F%
     gawk "{print $1, $2}" %GU% | psxy -JM -R -Sa0.35c -W2 -Gred  -O -K >>%F%
     gawk "{print $1, $2}" %GA% | psxy -JM -R -St0.35c -W2 -Gred  -O -K >>%F%
     gawk "{print $1, $2}" %seis% | psxy -JM -R -Si0.35c -W2 -Gyellow  -O -K >>%F%
     gawk "{ print $8, $7*-1, $10*0.015 }" %M% | psxy -R -J -O -Sci -W2.0 -K >> %F% 
     
     gawk "{print $1, $2}" %A% | psxy -JM -R -St0.25c -W2 -Gred  -O -K >>%F%
     
     echo %EA1% %EA2% 10 0 1 LT A'>%LA%
     echo %CA1% %CA2% 10 0 1 LT A>>%LA%
     
     psxy %LA% -JM -R -W4,blue   -O -K >>%F%
     pstext %LA% -JM -R   -O -K >>%F%
     
     echo %EB1% %EB2% 10 0 1 LT B'>%LB%
     echo %CB1% %CB2% 10 0 1 LT B>>%LB%
     
     psxy %LB% -JM -R -W4,blue   -O -K >>%F%
     pstext %LB% -JM -R   -O -K >>%F%
     
     echo %EC1% %EC2% 10 0 1 LT C'>%LC%
     echo %CC1% %CC2% 10 0 1 LT C>>%LC%
     
     psxy %LC% -JM -R -W4,blue   -O -K >>%F%
     pstext %LC% -JM -R   -O -K >>%F%
     
     echo 111 -4 10 0 1 LT > tmp
     echo 109 -4 10 0 1 LT >> tmp
     psxy tmp -JM -R -W3,black   -O -K >> %F%
     
     echo 111 -6.0 10 0 1 LT > tmp
     echo 111 -4 10 0 1 LT >> tmp
     psxy tmp -JM -R -W3,black   -O -K >> %F%
     
     echo 109 -6.0 10 0 1 LT > tmp
     echo 111 -6.0 10 0 1 LT >> tmp
     psxy tmp -JM -R -W3,black   -O -K >> %F%
     
     echo 109 -4 10 0 1 LT > tmp
     echo 109 -6.0 10 0 1 LT >> tmp
     
     psxy tmp -JM -R -W3,black   -O -K >> %F%
     
     echo 109.5 -4.2 9 0 7 LT Gempa Utama> tmp
     echo 109.5 -4.5 9 0 7 LT Seismometer >> tmp
     echo 109.5 -5.7 9 0 7 LT Gunung Api >> tmp
     
     pstext tmp -JM -R   -O -K >>%F%
     
     psxy -R -JM -Wthin -m -O -K -W2 %sesar% >> %F%
     psxy -R -JM -Wthin -m -O -K -W2 %sesar2% >> %F%
     
     echo 109.5 -4.8 9 0 7 LT M 3 > %SA%
     echo 109.5 -5.1 9 0 7 LT M 4 >> %SB%
     echo 109.5 -5.4 9 0 7 LT M 5 >> %SC%
     pstext %SA% -JM -R -O -G -N -K >> %F%
     pstext %SB% -JM -R -O -G -N -K >> %F%
     pstext %SC% -JM -R -O -G -N -K >> %F%
     
     psbasemap -Jn0.11c -R93/140/-12/10 -B90/90/0.5SEwn --HEADER_FONT_SIZE=2 -P -Y10.130 -X6.85 -O -K >> %F%
     pscoast  -V -O -J -R -W0.4 -B -Df -S77/255/217  -Ggray -K >> %F%
     
     echo 108.5 1 6 0 1 LT Kalimantan > tmp
     echo 108 -6.5 6 0 1 LT Jawa >> tmp
     echo 98 -1 6 0 1 LT Sumatra >> tmp
     echo 118 -1 6 0 1 LT Sulawesi >> tmp
     echo 131 -3 6 0 1 LT Papua >> tmp
     echo 95 -9 6 0 1 LT Samudra Hindia >> tmp
     
     pstext tmp -Jn -R -O -K >>%F%
     
     echo 116 -4 10 0 1 LT > tmp
     echo 109 -4 10 0 1 LT >> tmp
     psxy tmp -Jn -R -W3,red   -O -K >> %F%
     
     echo 116 -11 10 0 1 LT > tmp
     echo 116 -4 10 0 1 LT >> tmp
     psxy tmp -Jn -R -W3,red   -O -K >> %F%
     
     echo 109 -11 10 0 1 LT > tmp
     echo 116 -11 10 0 1 LT >> tmp
     psxy tmp -Jn -R -W3,red   -O -K >> %F%
     
     echo 109 -4 10 0 1 LT > tmp
     echo 109 -11 10 0 1 LT >> tmp
     
     psxy tmp -Jn -R -W3,red   -O >> %F%
     
     ps2raster %F% -A -Tg -P -E1200
     
     del *.d
     del tmp
     rem del *.ps

## Langkah-langkah :
1. [Filter Data](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B1%5D%20Research%20Area) Tahap pendahuluan untuk menampilkan peta daerah penelitian
2. [Convert Data](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B2%5D%20Convert%20Data) berisi tentang cara konversi format data menjadi format input `HypoDD`
3. [HypoDD](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B3%5D%20HYPODD) berisi tentang cara menjalankan program `HypoDD`
4. [Plot Hasil](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B4%5D%20Plot%20Result) berisi tentang cara melakukan plotting hiposenter hasil relokasi 




