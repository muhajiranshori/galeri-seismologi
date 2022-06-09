---
title: "Moment Yagi"
date: 2022-06-01T09:40:58+07:00
draft: false
toc: true
comments: true
categories:
- moment_tensor
- waveform_inversion
- waveform_treatment
- sac
tags:
- linux
- moment
- SAC
- rdseed
---

# 1. Pendahuluan

# 2. Struktur Folder 

	(base) muhajir@galeri-seismologi:/mnt/e/GALERI_SEISMOLOGI/Moment-Yagi$ 
	.
	├── README.md
	├── [1] Reserach Area
	│   ├── Palu.bat
	│   ├── Palu.png
	│   ├── Palu.ps
	│   ├── mainshock.dat
	│   ├── station.dat
	│   └── volcano.dat
	├── [2] Convert and Picking Waveform
	│   ├── 2018.271.10.00.33.0625.IA.APSI..BHZ.D.SAC
	│   ├── BH_EN_end_time.dat
	│   ├── BH_EN_start_time.dat
	│   ├── STA.E.RTJ
	│   ├── STA.N.RTJ
	│   ├── STA.Z.RTJ
	│   ├── IA.STA.BHE.SAC
	│   ├── IA.STA.BHN.SAC
	│   ├── IA.STA.BHZ.SAC
	│   ├── Makefile
	│   ├── Palu.seed
	│   ├── SAC_PZs_IA_STA_BHE_00_2018.271.10.00.24.4875_2018.271.10.12.53.2875
	│   ├── SAC_PZs_IA_STA_BHN_00_2018.271.10.00.24.4875_2018.271.10.12.53.2875
	│   ├── SAC_PZs_IA_STA_BHZ_00_2018.271.10.00.24.4875_2018.271.10.12.53.2875
	│   ├── raw.mac
	│   ├── raw2.mac
	│   └── stn_3c.id
	├── [3] Waveform Preparation
	│   ├── STA.E.RTJ
	│   ├── STA.N.RTJ
	│   ├── STA.Z.RTJ
	│   ├── IA.STA.BHE.SAC
	│   ├── IA.STA.BHN.SAC
	│   ├── IA.STA.BHZ.SAC
	│   ├── SAC_PZs_IA_STA_BHE_00_2018.271.10.01.25.3625_2018.271.10.08.50.5125
	│   ├── SAC_PZs_IA_STA_BHN_00_2018.271.10.01.25.3625_2018.271.10.08.50.5125
	│   ├── SAC_PZs_IA_STA_BHZ_00_2018.271.10.01.25.3625_2018.271.10.08.50.5125
	│   └── raw.mac
	└── [4] Moment
		├── FILTER.DAT
		├── STA.E.RTJ
		├── STA.N.RTJ
		├── STA.Z.RTJ
		├── STRUCTURE.DAT
		├── WAVE.GRN
		├── WAVE.OBS
		├── i_greenM
		├── i_inv
		├── i_obsdata
		├── plotwave.csh
		├── sac.wav
		├── solution.dat
		├── solution.list
		└── solution.ps
		
		
# 3. Data dan Software

## Data

Data yang digunakan adalah wavefprm gempa Palu yang terjadi pada 28 septembr 2018 Mw.7.1.

Data di download **disini** dari 5 stasiun seismik di sekitar pusat gempa. 



## Software yang digunakan 

Software yang diguankan adalah software **Moment** yang dibuat oleh Yagi, Profesor dari Tohoku University. 

Anda dapat meilihat publikasinya **disini**.

OS yang saya gunakan adalah Linux Ubuntu LTS 20.0

# 4. *Waveform Alignment*
		