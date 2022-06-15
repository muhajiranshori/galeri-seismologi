---
title: "Relokasi HypoDD Pat 2 - Running HypoDD"
date: 2020-09-06T17:21:25+07:00
draft: false
toc: true
comments: true
categories:
- earthquake_relocation
tags:
- cygwin
- python
- hypoDD
- GMT
---


#  Running HypoDD
 - Tahapan ini adalah bagian inti dari relokasi hiposenter dengan Metode Double Difference yaitu running program HypoDD.
 
# File yang harus dipersiapkan

## file di luar folder
 - `station.dat` berisi informasi stasiun yang digunakan.
 - `Jatim.pha`  berisi nilai travel time observasi yang dihasilkan dari tahap [convert_data](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B2%5D%20Convert%20Data).

## file di dalam folder `ph2dt`
 - `ph2dt.inp` berisi setting parameter
 - `ph2dt.exe` program untuk menghitung bla bla bla

## file di dalam folder `hypoDD`
 - `hypoDD.inp` berisi setting parameter
 - `station.dat` berisi informasi stasiun yang digunakan.
 - `event.dat`, `event.sel` dan `dt.ct` merupakan file output dari program `ph2dt.exe` yanng menjadi input pada program `hypoDD.exe` 
 - `hypoDD.exe` program untuk menghitung melakukan relokasi double difference

# Langkah-langkah-langkah

1. Siapkan file-file yang telah disebutkan di atas
2. Buka terminal cygwin lalu masuk ke dalam folder `HypoDD/ph2dt/`
3. Jalan program `ph2dt.exe` dengan perintah 

  ```
  ./ph2dt.exe ph2dt.inp`
  ```

## maka akan menghasilkan file  

 - `event.dat` berisi daftar event yang digunakan dalam penelitian.
 - `event.sel` berisi daftar event yang memenuhi kriteria pada setting parameter `ph2dt.inp`
 - `dt.ct` berisi nilai travel time relatif antara pasangan event.

4. Pindahkan ke-3 file tersebut ke dalam folder `HypoDD`
5. Ubah direktori kerja terminal cygwin ke dalam folder `HypoDD`
6. Jalan program `hypoDD.exe` dengan perintah 

  ```
  ./hypoDD.exe`
  ```

## maka akan menghasilkan file  

 - `hypoDD.reloc.001` `hypoDD.reloc.001.002` `hypoDD.reloc.00n` bersisi parameter hiposenter hasil relokasi setep 1, 2 hingga step `n`
 - `hypoDD.reloc` berisi parameter final hasil relokasi
 - `hypoDD.sta` berisi koordinat stasiun yang digunakan dalam relokasi
 - `hypoDD.res` berisi nilai residuals

7. Pindahkan file `hypoDD.reloc` ke dalam folder `Plot Result` untuk tahap plotting 

Membahas tutorial relokasi hiposenter menggunakan software HypoDD

![Jatim_Katalog](https://user-images.githubusercontent.com/28419810/109119463-4eb17b80-7777-11eb-8f71-e1040d73c98c.png)

![Jatim_hypoDD_reloc](https://user-images.githubusercontent.com/28419810/109119484-583ae380-7777-11eb-910a-40dd0ed268a3.png)

![relokasi_jawa_timur](/img/Jatim_HypoDD_akhir.png)









`ph2dt.inp`

	* ph2dt.inp - input control file for program ph2dt
	* Input station file:
	station.dat
	* Input phase file:
	Jatim1520.pha
	*MINWGHT: min. pick weight allowed [0]
	*MAXDIST: max. distance in km between event pair and stations [200]
	*MAXSEP: max. hypocentral separation in km [10]
	*MAXNGH: max. number of neighbors per event [10]
	*MINLNK: min. number of links required to define a neighbor [8]
	*MINOBS: min. number of links per pair saved [8]
	*MAXOBS: max. number of links per pair saved [20]
	*MINWGHT MAXDIST MAXSEP MAXNGH MINLNK MINOBS MAXOBS
	0      500    100     50     8      8     32






	reading data ...
	> stations =  194
	> events total =  3446
	> events selected =  2535
	> phases =  29794
	forming dtimes...
	> P-phase pairs total =  1609198
	> S-phase pairs total =  648796
	> outliers =  17211 ( 0%)
	> phases at stations not in station list =  37260
	> phases at distances larger than MAXDIST =  3346
	> P-phase pairs selected =  250669 ( 15%)
	> S-phase pairs selected =  117221 ( 18%)
	> weakly linked events =  1726 ( 68%)
	> linked event pairs =  42382
	> average links per pair =  8
	> average offset (km) betw. linked events =   49.3882446
	> average offset (km) betw. strongly linked events =   49.3882446
	> maximum offset (km) betw. strongly linked events =   99.9981079
	
	Done.
	
	Output files: dt.ct; event.dat; event.sel; ph2dt.log
	ph2dt parameters were:
	(minwght,maxdist,maxsep,maxngh,minlnk,minobs,maxobs)
	0.  500.  100. 50 8 8 32
	
	reading data ...
	> stations =  295
	> events total =  3446
	> events selected =  2535
	> phases =  29794
	forming dtimes...
	> P-phase pairs total =  1588484
	> S-phase pairs total =  641853
	> outliers =  17654 ( 0%)
	> phases at stations not in station list =  0
	> phases at distances larger than MAXDIST =  3341
	> P-phase pairs selected =  273510 ( 17%)
	> S-phase pairs selected =  124569 ( 19%)
	> weakly linked events =  1674 ( 66%)
	> linked event pairs =  45421
	> average links per pair =  8
	> average offset (km) betw. linked events =   49.756752
	> average offset (km) betw. strongly linked events =   49.756752
	> maximum offset (km) betw. strongly linked events =   99.9981079
	
	Done.
	
	Output files: dt.ct; event.dat; event.sel; ph2dt.log
	ph2dt parameters were:
	(minwght,maxdist,maxsep,maxngh,minlnk,minobs,maxobs)
	0.  500.  100. 50 8 8 32
