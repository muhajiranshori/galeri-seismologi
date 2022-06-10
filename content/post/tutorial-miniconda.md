---
title: "Tutorial miniconda"
date: 2020-01-03T10:30:56+07:00
draft: false
toc: true
comments: true
categories:
- installation
- environment_management
tags:
- miniconda
- windows
- linux
---

# 1. Pendahuluan

Python adalah bahasa pemrograman yang bisa dikatakan paling populer saat ini tak terkecali dalam dunia geosains.

Perkembangan python ditandai dengan bekembanganya beraneka *package* dan *module* berbasis python yang sangat lengkap.

Mengapa harus menggunakan conda ?

Sebelum memluia tutirial ini, pastikan anda sudah meng-install miniconda terlebih dahulu. Cara install nya dapat dilihat **disini**.

# 2. Tutorial conda

## Membuat environtment

Untuk mengetahui cara penggunaan dasar conda anda dapat melihatnya dengan perintah `conda help`

maka akan mucul tampilan berikut

	(base) muhajir@galeri-seismologi~$ conda help
	usage: conda [-h] [-V] command ...
	
	conda is a tool for managing and deploying applications, environments and packages.
	
	Options:
	
	positional arguments:
	command
		clean        Remove unused packages and caches.
		config       Modify configuration values in .condarc. This is modeled
					after the git config command. Writes to the user .condarc
					file (/home/muhajir/.condarc) by default.
		create       Create a new conda environment from a list of specified
					packages.
		help         Displays a list of available conda commands and their help
					strings.
		info         Display information about current conda install.
		init         Initialize conda for shell interaction. [Experimental]
		install      Installs a list of packages into a specified conda
					environment.
		list         List linked packages in a conda environment.
		package      Low-level conda package utility. (EXPERIMENTAL)
		remove       Remove a list of packages from a specified conda environment.
		uninstall    Alias for conda remove.
		run          Run an executable in a conda environment. [Experimental]
		search       Search for packages and display associated information. The
					input is a MatchSpec, a query language for conda packages.
					See examples below.
		update       Updates conda packages to the latest compatible version.
		upgrade      Alias for conda update.
	
	optional arguments:
	-h, --help     Show this help message and exit.
	-V, --version  Show the conda version number and exit.
	
	conda commands available from other packages:
	build
	convert
	debug
	develop
	env
	index
	inspect
	metapackage
	render
	server
	skeleton
	verify
	(base) muhajir@galeri-seismologi~$

berdasarkan hasil yang muncul dengan perintah diatas, sepintas dapat kita pahami bahwa kita dapat melakukan pembuatan `env` baru, menghapusnya, menginstall program pada `env` tertentu, mengupdate program dan lain-lain.

Kali ini saya akan menunjukkan cara penggunaan conda yang dasar saja atau yang sering dilakukan. 


## mengetahui env yang terinstall

```
conda info -e
```
	# conda environments:
	#
	base                  *  /home/muhajir/anaconda3
	eqt                      /home/muhajir/anaconda3/envs/eqt
	prc                      /home/muhajir/anaconda3/envs/prc
	ql                       /home/muhajir/anaconda3/envs/ql

tanda `*` menunjukkan environment yang sedang aktif. Kebetulan saya belum mengajtifkan env apapun sehingga tnda `*` masih berada pada base.

Tips

Usahakan jangan meninstall apapun pada `base` kecuali **Jupyter Notebook** dan **nb_conda_kernels**.

Mengapa demikian ?



## mengetahui versi package

## Menghapus Environment

Jika suatu saat anda sudah selesai dengan suatu program atau env tertentu dan misal untuk tujuan efisiensi memori komputer anda, anda dapat menghapus sebuah `env`.

Bagaimana caranya ?

Mari kita praktekkan. 

Sebagai contoh kita akan mencoba menghapus env obspy

Caranya adalah dengan mengetik perintah 

``` python
conda remove --name obspy --all
```

Perintah tersebut akan menghaspus semua `env` obspy secara keseluruhan hingga habis tak bersisa.

Maka akan meuncul sebagai berikut :
	
	Remove all packages in environment C:\Users\WIN 10\.conda\envs\obspy:
	
	
	## Package Plan ##
	
	environment location: C:\Users\WIN 10\.conda\envs\obspy
	
	
	The following packages will be REMOVED:
	
	ca-certificates-2021.10.8-h5b45459_0
	openssl-3.0.2-h8ffe710_1
	pip-22.0.4-pyhd8ed1ab_0
	python-3.7.12-h900ac77_100_cpython
	python_abi-3.7-2_cp37m
	setuptools-61.1.1-py37h03978a9_0
	sqlite-3.37.1-h8ffe710_0
	ucrt-10.0.20348.0-h57928b3_0
	vc-14.2-hb210afc_6
	vs2015_runtime-14.29.30037-h902a5da_6
	wheel-0.37.1-pyhd8ed1ab_0
	
	
	Proceed ([y]/n)? y
	
	Preparing transaction: done
	Verifying transaction: done
	Executing transaction: done
	
Obspy telah berhasil dihapus dan telah hilang dari daftar environment conda.