---
title: "Relokasi Velest Part 4 Plot Vektor Pergeseran"
date: 2020-08-16T11:21:40+07:00
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

Jika sebelumnya kita sudah melakukan plotting lokasi hiposenter baik sebelum dan sesudah relokasi, kita juga perlu tahu seberapa besar dan ke arah mana hiposenternya bergeser.

Gimana cara ngeplotnya ? yak betul...

Gunakan `psvelo` dari **GMT4**.

Pertama-tama sediakan file 1 

Lalu siapkan file 2

Berikit adalah script `vektor_pergeseran.bat`

``` batch
pscoast  -V -O -J -R -W1.5 -B2WSne -Lf119.2/-3.1/50/200 -T118.6/0.2/0.9i -Df -K >> %F%
psvelo %V% -J -R -Se.023/0.95/0 -G0 -A0.015/0.12/0.03 -K -O -V >> %F%
psxy %V% -R -J -Sc.06/0/0/0 -W1/0/0/0 -G255 -V -K -O >> %F% 
```

Jalankan seperti biasa dengan double klik dan hasilnya akan seperti ini

Gambar

