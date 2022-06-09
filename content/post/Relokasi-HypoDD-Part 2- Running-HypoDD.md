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
