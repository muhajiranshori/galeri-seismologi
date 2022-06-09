---
title: "Relokasi HypoDD Part 1 : Persiapan Data"
date: 2020-09-02T17:21:25+07:00
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

# 1. Pendahuluan

# 2. Struktur Folder Kerja

	(base) muhajir@galeri-seismologi:/mnt/e/GALERI_SEISMOLOGI/Relokasi-HypoDD$ tree
	.
	├── README.md
	├── [1] Research Area
	│   ├── GA.dat
	│   ├── GU.dat
	│   ├── Jatim.bat
	│   ├── Jatim.png
	│   ├── Jatim.ps
	│   ├── README.md
	│   ├── mainshock.dat
	│   ├── seis.dat
	│   ├── station.dat
	│   └── volcano.dat
	├── [2] Convert Data
	│   ├── Jatim.pha
	│   ├── Jatim.txt
	│   ├── README.md
	│   └── cat2pha.py
	├── [3] HYPODD
	│   ├── Jatim.pha
	│   ├── README.md
	│   ├── hypoDD
	│   │   ├── cygwin1.dll
	│   │   ├── dt.ct
	│   │   ├── event.dat
	│   │   ├── event.sel
	│   │   ├── hypoDD.exe
	│   │   ├── hypoDD.inp
	│   │   ├── hypoDD.loc
	│   │   ├── hypoDD.log
	│   │   ├── hypoDD.reloc
	│   │   ├── hypoDD.reloc.001.001
	│   │   ├── hypoDD.reloc.001.002
	│   │   ├── hypoDD.reloc.001.003
	│   │   ├── hypoDD.reloc.001.004
	│   │   ├── hypoDD.reloc.001.005
	│   │   ├── hypoDD.reloc.001.006
	│   │   ├── hypoDD.reloc.001.007
	│   │   ├── hypoDD.reloc.001.008
	│   │   ├── hypoDD.reloc.001.009
	│   │   ├── hypoDD.reloc.001.010
	│   │   ├── hypoDD.reloc.001.011
	│   │   ├── hypoDD.reloc.001.012
	│   │   ├── hypoDD.reloc.001.013
	│   │   ├── hypoDD.reloc.001.014
	│   │   ├── hypoDD.reloc.001.015
	│   │   ├── hypoDD.reloc.001.016
	│   │   ├── hypoDD.res
	│   │   ├── hypoDD.sta
	│   │   └── station.dat
	│   ├── ph2dt
	│   │   ├── cygwin1.dll
	│   │   ├── dt.ct
	│   │   ├── event.dat
	│   │   ├── event.sel
	│   │   ├── ph2dt.exe
	│   │   ├── ph2dt.inp
	│   │   └── ph2dt.log
	│   └── station.dat
	└── [4] Plot Result
		├── A.dat
		├── Jatim_Katalog.bat
		├── Jatim_Katalog.png
		├── Jatim_hypoDD_reloc.bat
		├── Jatim_hypoDD_reloc.png
		├── README.md
		├── event.dat
		├── hypoDD.reloc
		├── kedalaman.cpt
		├── kedalaman1.cpt
		├── kedalaman2.cpt
		├── palet1.bat
		├── palet2.bat
		└── station.dat



# Relokasi-HypoDD
Begian ini adalah pendahuluan untuk menampilkan daerah penelitian yaitu daerah Jawa Timur. 


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





#### Berikut adala tampilan setelah kita menjalankan script `Research_Area.bat`
![jawa_timur](/img/Jatim.png)
### Keterangan

 - `Bintang warna merah` adalah episenter gempabumi utama Mw 7.1, 28 September 2018 
 - `Segitiga tebalik warna kuning` adalah stasiun yang digunakan dalam penelitian
 - `Garis warna biru dengan label huruf` adalah garis cross-section dimana irisan seismisitas akan di tampilkan
 - `Segitiga warna merah` adalah gunung api
 - `Garis merah` adalah sesar 
 - `Bathymetri` yang digunakakan adalah srtm_15


# Relokasi-HypoDD
Kali ini kita akan membahas tutorial relokasi hiposenter menggunakan program HypoDD

## Data

- Data yang digunakan adalah data arrival time repository gempabumi BMKG daerah Jawa Timur tahun 2009 -2017.

## Software-software yang digunakan yaitu :
  - [Python](https://www.python.org/) dan `Matlab` Untuk konversi format data 
  - [GMT](https://www.generic-mapping-tools.org/) Untuk visualisasi hasil  (tutorial ini menggunakan GMT4) 
  - [HypoDD](https://www.ldeo.columbia.edu/~felixw/hypoDD.html) Program utama relokasi hiposenter
  - [Notepad++](https://notepad-plus-plus.org/downloads/) Untuk menampilkan meng-edit script maupun hasil program. Dapat juga menggunaakan text editor lain sesuai keinginan  
  - [Cygwin](https://www.cygwin.com/) Untuk menjalankan program `HypoDD` 

## Langkah-langkah :
1. [Filter Data](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B1%5D%20Research%20Area) Tahap pendahuluan untuk menampilkan peta daerah penelitian
2. [Convert Data](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B2%5D%20Convert%20Data) berisi tentang cara konversi format data menjadi format input `HypoDD`
3. [HypoDD](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B3%5D%20HYPODD) berisi tentang cara menjalankan program `HypoDD`
4. [Plot Hasil](https://github.com/muhajiranshori/Relokasi-HypoDD/tree/main/%5B4%5D%20Plot%20Result) berisi tentang cara melakukan plotting hiposenter hasil relokasi 

Untuk dapat menjalankan tutorial ini dengan baik maka persiapkan dan install terlebih dahulu beberapa software pendukung.

# Convert input data HypoDD

Langkah-langkah konversi data input pada hypoDD.

# Langkah-langkah

1. Siapkan file `Jatim.txt`. File tersebut adalah hasil filter data sebagaimana dijelaskan langkah-langkahnya  [berikut](https://github.com/muhajiranshori/Tomografi-Simulps12/tree/main/%5B1%5D%20Filer%20Katalog)
2. Jalankan script `cat2pha.py` yang akan menghasilkan file `Jatim.pha`

``` python
import cat2pha
cat2pha(input_file='jatim.txt' output_file='jatim.pha')
```


3. Pindahkan file `Jatim.pha` tersebut ke dalam folder `[3] HypoDD` untuk proses selanjutnya.

## Catatan 

Nama file iput dan output harus di edit atau di sesuaikan dengan nama data anda ( Lihat script dengan text editor)


https://github.


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


