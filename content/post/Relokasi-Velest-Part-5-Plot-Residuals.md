---
title: "Relokasi Velest Part 5 Plot Residuals"
date: 2020-08-20T11:21:40+07:00
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

# Plot Residuals P dan S

Kemarin kita sudah belaja cara plotting vektor pergeseran lokasi hiposneter sebelum dan sesudah relokasi.

Sekarang kita akan belajar menge-plot residual P dan S. 

Apa itu residuals P dan S ?

Nilai residuals P dan S adalah nilai selish travel time observasi dan kalkulasi gelombang P dan S.

## Data Residuals P dan S

Setrelah anda slelasu running program velest, maka data nilai residuals P dan S dapat anda lihat pada file `velest.out`

Search saja dengan kata kuci `residuals` maka akan muncul sepeeti berikut

Gambar

Copy nilai tersebut pada sebuaf file degan nama `residuls_P.dat` dan `resdiuals_S.dat`

**residuls_P.dat**

```
1.512
-0.778
0.135
-0.788
-0.059
-1.167
0.555
0.31
-0.586
...
```

**residuls_S.dat**

```
2.262
-0.002
1.894
1.585
1.418
0.652
-0.537
0.108
0.782
```

## Plot histogram residuals dengan GMT

Berikut adalah script GMT untuk plot residuals P dan S 

**residuals.bat**

``` batch
set F=Residual_Palu_P.ps
set I=Palu_P.dat
set II=Palu_S.dat
            
psbasemap -JX7.0/7.5 -R-8/8/0/500 -Ba2f2:"S residuals (s)":/:"Number of Phase":100f100wSne --LABEL_FONT_SIZE=9p -P  -O -K -Y-0 -X20.0 >>%F%

gawk "{print $1}" %II% | pshistogram -R -J -G100 -L0.5p -W0.2 -F -P -O -K >> %F%


psbasemap -JX7.0/7.5 -R-8/8/0/500 -Ba2f2:"P residuals (s)":/:"Number of Phase":100f100WSne --LABEL_FONT_SIZE=9p -P  -O -K -Y0 -X-8.0 >>%F%

gawk "{print $1}" %I% | pshistogram -R -J -G150 -L0.5p -W0.2 -F -P -O >> %F%

rem echo -3.5 -120 11 0 29 LT  @;red;Gambar 6.@;; Histogram residual travel time gelombang P (kiri) dan gelombang S (kanan)   > tmp
rem echo -3.5 -160 11 0 29 LT  untuk event gempabumi daerah Bali  >> tmp
rem echo -3.5 -200 11 0 29 LT  _>> tmp
rem echo  1.8 480 11 0 29 LT  2867 P >> tmp
rem echo  8.8 480 11 0 29 LT  1307 S >> tmp
rem pstext tmp -JX -R   -O -Gblack -N >> %F%

rem -------------------------------------------------------------------------------------------------------

ps2raster %F% -A -Tg -P -E1200
```

Double klik pada file `residuals.bat maka akan menghasikan gambar sebagai berikut.


![Residual](/img/Velest/Residual_Palu_P.png)

Selamat Mencoba 

