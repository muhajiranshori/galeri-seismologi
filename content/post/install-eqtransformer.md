---
title: "Install Eqtransformer"
date: 2021-08-01T08:08:42+07:00
draft: false
comments: true
categories:
- machine_learning
- deep_learning
tags:
- eqtransformer
---

Kali ini kita akan belajar meng-install EQTransformer dengan miniconda

``` python
conda create -n eqt python=3.7
```

maka akan muncul seperti di bawah ini, ketik `y` untuk pertanyaan `Proceed ([y]/n)?`


	Collecting package metadata (current_repodata.json): done
	Solving environment: done
	
	## Package Plan ##
	
	environment location: C:\Users\WIN 10\.conda\envs\eqt
	
	added / updated specs:
		- python=3.7
	
	
	The following packages will be downloaded:
	
		package                    |            build
		---------------------------|-----------------
		pip-22.1.2                 |     pyhd8ed1ab_0         1.5 MB  conda-forge
		------------------------------------------------------------
											Total:         1.5 MB
	
	The following NEW packages will be INSTALLED:
	
	ca-certificates    conda-forge/win-64::ca-certificates-2022.5.18.1-h5b45459_0
	openssl            conda-forge/win-64::openssl-3.0.3-h8ffe710_0
	pip                conda-forge/noarch::pip-22.1.2-pyhd8ed1ab_0
	python             conda-forge/win-64::python-3.7.12-h900ac77_100_cpython
	python_abi         conda-forge/win-64::python_abi-3.7-2_cp37m
	setuptools         conda-forge/win-64::setuptools-62.3.2-py37h03978a9_0
	sqlite             conda-forge/win-64::sqlite-3.38.5-h8ffe710_0
	ucrt               conda-forge/win-64::ucrt-10.0.20348.0-h57928b3_0
	vc                 conda-forge/win-64::vc-14.2-hb210afc_6
	vs2015_runtime     conda-forge/win-64::vs2015_runtime-14.29.30037-h902a5da_6
	wheel              conda-forge/noarch::wheel-0.37.1-pyhd8ed1ab_0
	
	
	Proceed ([y]/n)? y
	
	
	Downloading and Extracting Packages
	pip-22.1.2           | 1.5 MB    | ############################################################################### | 100%
	Preparing transaction: done
	Verifying transaction: done
	Executing transaction: done
	#
	# To activate this environment, use
	#
	#     $ conda activate eqt
	#
	# To deactivate an active environment, use
	#
	#     $ conda deactivate

Aktifkan environment `eqt` lalu install `EQTransformer` menggunakan `pip`

```
conda activate eqt
pip install EQTransformer
```



	(eqt) E:\>pip install EQTransformer
	Collecting EQTransformer
	Using cached EQTransformer-0.1.59-py3-none-any.whl (78 kB)
	Collecting tqdm==4.48.0
	Using cached tqdm-4.48.0-py2.py3-none-any.whl (67 kB)
	Collecting matplotlib
	Using cached matplotlib-3.5.2-cp37-cp37m-win_amd64.whl (7.2 MB)
	Collecting keras==2.3.1
	Using cached Keras-2.3.1-py2.py3-none-any.whl (377 kB)
	Collecting obspy
	Using cached obspy-1.3.0-cp37-cp37m-win_amd64.whl (13.9 MB)
	Collecting tensorflow==2.0.0
	Using cached tensorflow-2.0.0-cp37-cp37m-win_amd64.whl (48.1 MB)
	Collecting keyring>=15.1
	Downloading keyring-23.5.1-py3-none-any.whl (33 kB)
	Collecting pytest
	Downloading pytest-7.1.2-py3-none-any.whl (297 kB)
		---------------------------------------- 297.0/297.0 kB 965.6 kB/s eta 0:00:00
	Collecting pandas
	Using cached pandas-1.3.5-cp37-cp37m-win_amd64.whl (10.0 MB)
	Collecting jupyter
	Using cached jupyter-1.0.0-py2.py3-none-any.whl (2.7 kB)
	Collecting scipy==1.4.1
	Using cached scipy-1.4.1-cp37-cp37m-win_amd64.whl (30.9 MB)
	Collecting h5py==2.10.0
	Using cached h5py-2.10.0-cp37-cp37m-win_amd64.whl (2.5 MB)
	Collecting pkginfo>=1.4.2
	Using cached pkginfo-1.8.2-py2.py3-none-any.whl (26 kB)
	Collecting six
	Using cached six-1.16.0-py2.py3-none-any.whl (11 kB)
	Collecting numpy>=1.7
	Using cached numpy-1.21.6-cp37-cp37m-win_amd64.whl (14.0 MB)
	Collecting keras-applications>=1.0.6
	Using cached Keras_Applications-1.0.8-py3-none-any.whl (50 kB)
	Collecting pyyaml
	Using cached PyYAML-6.0-cp37-cp37m-win_amd64.whl (153 kB)
	Collecting keras-preprocessing>=1.0.5
	Using cached Keras_Preprocessing-1.1.2-py2.py3-none-any.whl (42 kB)
	Collecting tensorboard<2.1.0,>=2.0.0
	Using cached tensorboard-2.0.2-py3-none-any.whl (3.8 MB)
	Collecting tensorflow-estimator<2.1.0,>=2.0.0
	Using cached tensorflow_estimator-2.0.1-py2.py3-none-any.whl (449 kB)
	Collecting google-pasta>=0.1.6
	Using cached google_pasta-0.2.0-py3-none-any.whl (57 kB)
	Collecting termcolor>=1.1.0
	Using cached termcolor-1.1.0-py3-none-any.whl
	Collecting astor>=0.6.0
	Using cached astor-0.8.1-py2.py3-none-any.whl (27 kB)
	Collecting absl-py>=0.7.0
	Downloading absl_py-1.1.0-py3-none-any.whl (123 kB)
		---------------------------------------- 123.7/123.7 kB 1.2 MB/s eta 0:00:00
	Collecting opt-einsum>=2.3.2
	Using cached opt_einsum-3.3.0-py3-none-any.whl (65 kB)
	Collecting grpcio>=1.8.6
	Downloading grpcio-1.46.3-cp37-cp37m-win_amd64.whl (3.5 MB)
		---------------------------------------- 3.5/3.5 MB 991.9 kB/s eta 0:00:00
	Collecting wrapt>=1.11.1
	Downloading wrapt-1.14.1-cp37-cp37m-win_amd64.whl (35 kB)
	Requirement already satisfied: wheel>=0.26 in c:\users\win 10\.conda\envs\eqt\lib\site-packages (from tensorflow==2.0.0->EQTransformer) (0.37.1)
	Collecting gast==0.2.2
	Using cached gast-0.2.2-py3-none-any.whl
	Collecting protobuf>=3.6.1
	Downloading protobuf-4.21.1-cp37-cp37m-win_amd64.whl (524 kB)
		---------------------------------------- 524.6/524.6 kB 844.6 kB/s eta 0:00:00
	Collecting pywin32-ctypes!=0.1.0,!=0.1.1
	Using cached pywin32_ctypes-0.2.0-py2.py3-none-any.whl (28 kB)
	Collecting importlib-metadata>=3.6
	Using cached importlib_metadata-4.11.4-py3-none-any.whl (18 kB)
	Collecting ipywidgets
	Downloading ipywidgets-7.7.0-py2.py3-none-any.whl (123 kB)
		---------------------------------------- 123.4/123.4 kB 1.0 MB/s eta 0:00:00
	Collecting jupyter-console
	Downloading jupyter_console-6.4.3-py3-none-any.whl (22 kB)
	Collecting ipykernel
	Using cached ipykernel-6.13.0-py3-none-any.whl (131 kB)
	Collecting nbconvert
	Using cached nbconvert-6.5.0-py3-none-any.whl (561 kB)
	Collecting notebook
	Using cached notebook-6.4.11-py3-none-any.whl (9.9 MB)
	Collecting qtconsole
	Downloading qtconsole-5.3.0-py3-none-any.whl (120 kB)
		---------------------------------------- 120.6/120.6 kB 1.0 MB/s eta 0:00:00
	Collecting fonttools>=4.22.0
	Using cached fonttools-4.33.3-py3-none-any.whl (930 kB)
	Collecting kiwisolver>=1.0.1
	Using cached kiwisolver-1.4.2-cp37-cp37m-win_amd64.whl (54 kB)
	Collecting pillow>=6.2.0
	Using cached Pillow-9.1.1-cp37-cp37m-win_amd64.whl (3.3 MB)
	Collecting pyparsing>=2.2.1
	Using cached pyparsing-3.0.9-py3-none-any.whl (98 kB)
	Collecting python-dateutil>=2.7
	Using cached python_dateutil-2.8.2-py2.py3-none-any.whl (247 kB)
	Collecting packaging>=20.0
	Using cached packaging-21.3-py3-none-any.whl (40 kB)
	Collecting cycler>=0.10
	Using cached cycler-0.11.0-py3-none-any.whl (6.4 kB)
	Collecting lxml
	Downloading lxml-4.9.0-cp37-cp37m-win_amd64.whl (3.6 MB)
		---------------------------------------- 3.6/3.6 MB 659.5 kB/s eta 0:00:00
	Collecting requests
	Using cached requests-2.27.1-py2.py3-none-any.whl (63 kB)
	Collecting sqlalchemy
	Downloading SQLAlchemy-1.4.37-cp37-cp37m-win_amd64.whl (1.6 MB)
		---------------------------------------- 1.6/1.6 MB 910.0 kB/s eta 0:00:00
	Collecting decorator
	Using cached decorator-5.1.1-py3-none-any.whl (9.1 kB)
	Requirement already satisfied: setuptools in c:\users\win 10\.conda\envs\eqt\lib\site-packages (from obspy->EQTransformer) (62.3.2)
	Collecting pytz>=2017.3
	Using cached pytz-2022.1-py2.py3-none-any.whl (503 kB)
	Collecting colorama
	Using cached colorama-0.4.4-py2.py3-none-any.whl (16 kB)
	Collecting iniconfig
	Using cached iniconfig-1.1.1-py2.py3-none-any.whl (5.0 kB)
	Collecting tomli>=1.0.0
	Using cached tomli-2.0.1-py3-none-any.whl (12 kB)
	Collecting py>=1.8.2
	Using cached py-1.11.0-py2.py3-none-any.whl (98 kB)
	Collecting attrs>=19.2.0
	Using cached attrs-21.4.0-py2.py3-none-any.whl (60 kB)
	Collecting pluggy<2.0,>=0.12
	Using cached pluggy-1.0.0-py2.py3-none-any.whl (13 kB)
	Collecting atomicwrites>=1.0
	Using cached atomicwrites-1.4.0-py2.py3-none-any.whl (6.8 kB)
	Collecting typing-extensions>=3.6.4
	Using cached typing_extensions-4.2.0-py3-none-any.whl (24 kB)
	Collecting zipp>=0.5
	Using cached zipp-3.8.0-py3-none-any.whl (5.4 kB)
	Collecting google-auth-oauthlib<0.5,>=0.4.1
	Using cached google_auth_oauthlib-0.4.6-py2.py3-none-any.whl (18 kB)
	Collecting google-auth<2,>=1.6.3
	Using cached google_auth-1.35.0-py2.py3-none-any.whl (152 kB)
	Collecting markdown>=2.6.8
	Downloading Markdown-3.3.7-py3-none-any.whl (97 kB)
		---------------------------------------- 97.8/97.8 kB 1.1 MB/s eta 0:00:00
	Collecting werkzeug>=0.11.15
	Downloading Werkzeug-2.1.2-py3-none-any.whl (224 kB)
		---------------------------------------- 224.9/224.9 kB 1.2 MB/s eta 0:00:00
	Collecting idna<4,>=2.5
	Using cached idna-3.3-py3-none-any.whl (61 kB)
	Collecting certifi>=2017.4.17
	Using cached certifi-2022.5.18.1-py3-none-any.whl (155 kB)
	Collecting urllib3<1.27,>=1.21.1
	Using cached urllib3-1.26.9-py2.py3-none-any.whl (138 kB)
	Collecting charset-normalizer~=2.0.0
	Using cached charset_normalizer-2.0.12-py3-none-any.whl (39 kB)
	Collecting ipython>=7.23.1
	Downloading ipython-7.34.0-py3-none-any.whl (793 kB)
		---------------------------------------- 793.8/793.8 kB 1.1 MB/s eta 0:00:00
	Collecting matplotlib-inline>=0.1
	Using cached matplotlib_inline-0.1.3-py3-none-any.whl (8.2 kB)
	Collecting debugpy>=1.0
	Using cached debugpy-1.6.0-cp37-cp37m-win_amd64.whl (4.3 MB)
	Collecting psutil
	Using cached psutil-5.9.1-cp37-cp37m-win_amd64.whl (246 kB)
	Collecting jupyter-client>=6.1.12
	Using cached jupyter_client-7.3.1-py3-none-any.whl (130 kB)
	Collecting traitlets>=5.1.0
	Downloading traitlets-5.2.2.post1-py3-none-any.whl (106 kB)
		---------------------------------------- 106.8/106.8 kB 1.0 MB/s eta 0:00:00
	Collecting tornado>=6.1
	Using cached tornado-6.1-cp37-cp37m-win_amd64.whl (422 kB)
	Collecting nest-asyncio
	Using cached nest_asyncio-1.5.5-py3-none-any.whl (5.2 kB)
	Collecting nbformat>=4.2.0
	Using cached nbformat-5.4.0-py3-none-any.whl (73 kB)
	Collecting ipython-genutils~=0.2.0
	Using cached ipython_genutils-0.2.0-py2.py3-none-any.whl (26 kB)
	Collecting widgetsnbextension~=3.6.0
	Downloading widgetsnbextension-3.6.0-py2.py3-none-any.whl (1.6 MB)
		---------------------------------------- 1.6/1.6 MB 1.0 MB/s eta 0:00:00
	Collecting jupyterlab-widgets>=1.0.0
	Downloading jupyterlab_widgets-1.1.0-py3-none-any.whl (245 kB)
		---------------------------------------- 245.1/245.1 kB 1.2 MB/s eta 0:00:00
	Collecting prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0
	Using cached prompt_toolkit-3.0.29-py3-none-any.whl (381 kB)
	Collecting pygments
	Using cached Pygments-2.12.0-py3-none-any.whl (1.1 MB)
	Collecting jupyter-core>=4.7
	Using cached jupyter_core-4.10.0-py3-none-any.whl (87 kB)
	Collecting pandocfilters>=1.4.1
	Using cached pandocfilters-1.5.0-py2.py3-none-any.whl (8.7 kB)
	Collecting mistune<2,>=0.8.1
	Using cached mistune-0.8.4-py2.py3-none-any.whl (16 kB)
	Collecting entrypoints>=0.2.2
	Using cached entrypoints-0.4-py3-none-any.whl (5.3 kB)
	Collecting nbclient>=0.5.0
	Downloading nbclient-0.6.4-py3-none-any.whl (71 kB)
		---------------------------------------- 71.8/71.8 kB 1.3 MB/s eta 0:00:00
	Collecting jupyterlab-pygments
	Using cached jupyterlab_pygments-0.2.2-py2.py3-none-any.whl (21 kB)
	Collecting jinja2>=3.0
	Using cached Jinja2-3.1.2-py3-none-any.whl (133 kB)
	Collecting bleach
	Using cached bleach-5.0.0-py3-none-any.whl (160 kB)
	Collecting beautifulsoup4
	Using cached beautifulsoup4-4.11.1-py3-none-any.whl (128 kB)
	Collecting defusedxml
	Using cached defusedxml-0.7.1-py2.py3-none-any.whl (25 kB)
	Collecting tinycss2
	Using cached tinycss2-1.1.1-py3-none-any.whl (21 kB)
	Collecting MarkupSafe>=2.0
	Using cached MarkupSafe-2.1.1-cp37-cp37m-win_amd64.whl (17 kB)
	Collecting terminado>=0.8.3
	Using cached terminado-0.15.0-py3-none-any.whl (16 kB)
	Collecting pyzmq>=17
	Downloading pyzmq-23.1.0-cp37-cp37m-win_amd64.whl (1.0 MB)
		---------------------------------------- 1.0/1.0 MB 1.0 MB/s eta 0:00:00
	Collecting Send2Trash>=1.8.0
	Using cached Send2Trash-1.8.0-py3-none-any.whl (18 kB)
	Collecting argon2-cffi
	Using cached argon2_cffi-21.3.0-py3-none-any.whl (14 kB)
	Collecting prometheus-client
	Using cached prometheus_client-0.14.1-py3-none-any.whl (59 kB)
	Collecting qtpy>=2.0.1
	Downloading QtPy-2.1.0-py3-none-any.whl (68 kB)
		---------------------------------------- 68.2/68.2 kB 742.9 kB/s eta 0:00:00
	Collecting greenlet!=0.4.17
	Using cached greenlet-1.1.2-cp37-cp37m-win_amd64.whl (101 kB)
	Collecting pyasn1-modules>=0.2.1
	Using cached pyasn1_modules-0.2.8-py2.py3-none-any.whl (155 kB)
	Collecting cachetools<5.0,>=2.0.0
	Using cached cachetools-4.2.4-py3-none-any.whl (10 kB)
	Collecting rsa<5,>=3.1.4
	Using cached rsa-4.8-py3-none-any.whl (39 kB)
	Collecting requests-oauthlib>=0.7.0
	Downloading requests_oauthlib-1.3.1-py2.py3-none-any.whl (23 kB)
	Collecting jedi>=0.16
	Using cached jedi-0.18.1-py2.py3-none-any.whl (1.6 MB)
	Collecting pickleshare
	Using cached pickleshare-0.7.5-py2.py3-none-any.whl (6.9 kB)
	Collecting backcall
	Using cached backcall-0.2.0-py2.py3-none-any.whl (11 kB)
	Collecting pywin32>=1.0
	Using cached pywin32-304-cp37-cp37m-win_amd64.whl (12.2 MB)
	Collecting fastjsonschema
	Using cached fastjsonschema-2.15.3-py3-none-any.whl (22 kB)
	Collecting jsonschema>=2.6
	Downloading jsonschema-4.6.0-py3-none-any.whl (80 kB)
		---------------------------------------- 80.4/80.4 kB 899.8 kB/s eta 0:00:00
	Collecting wcwidth
	Using cached wcwidth-0.2.5-py2.py3-none-any.whl (30 kB)
	Collecting pywinpty>=1.1.0
	Using cached pywinpty-2.0.5-cp37-none-win_amd64.whl (1.4 MB)
	Collecting argon2-cffi-bindings
	Using cached argon2_cffi_bindings-21.2.0-cp36-abi3-win_amd64.whl (30 kB)
	Collecting soupsieve>1.2
	Using cached soupsieve-2.3.2.post1-py3-none-any.whl (37 kB)
	Collecting webencodings
	Using cached webencodings-0.5.1-py2.py3-none-any.whl (11 kB)
	Collecting parso<0.9.0,>=0.8.0
	Using cached parso-0.8.3-py2.py3-none-any.whl (100 kB)
	Collecting pyrsistent!=0.17.0,!=0.17.1,!=0.17.2,>=0.14.0
	Using cached pyrsistent-0.18.1-cp37-cp37m-win_amd64.whl (61 kB)
	Collecting importlib-resources>=1.4.0
	Using cached importlib_resources-5.7.1-py3-none-any.whl (28 kB)
	Collecting pyasn1<0.5.0,>=0.4.6
	Using cached pyasn1-0.4.8-py2.py3-none-any.whl (77 kB)
	Collecting oauthlib>=3.0.0
	Downloading oauthlib-3.2.0-py3-none-any.whl (151 kB)
		---------------------------------------- 151.5/151.5 kB 1.0 MB/s eta 0:00:00
	Collecting cffi>=1.0.1
	Using cached cffi-1.15.0-cp37-cp37m-win_amd64.whl (179 kB)
	Collecting pycparser
	Using cached pycparser-2.21-py2.py3-none-any.whl (118 kB)
	Installing collected packages: webencodings, wcwidth, termcolor, tensorflow-estimator, Send2Trash, pywin32-ctypes, pywin32, pytz, pyasn1, pkginfo, pickleshare, mistune, ipython-genutils, iniconfig, fastjsonschema, backcall, zipp, wrapt, werkzeug, urllib3, typing-extensions, traitlets, tqdm, tornado, tomli, tinycss2, soupsieve, six, rsa, pyzmq, pyyaml, pywinpty, pyrsistent, pyparsing, pygments, pycparser, pyasn1-modules, py, psutil, protobuf, prompt-toolkit, prometheus-client, pillow, parso, pandocfilters, oauthlib, numpy, nest-asyncio, MarkupSafe, lxml, jupyterlab-widgets, jupyterlab-pygments, idna, greenlet, gast, fonttools, entrypoints, defusedxml, decorator, debugpy, cycler, colorama, charset-normalizer, certifi, cachetools, attrs, atomicwrites, astor, absl-py, terminado, scipy, requests, python-dateutil, packaging, opt-einsum, matplotlib-inline, kiwisolver, keras-preprocessing, jupyter-core, jinja2, jedi, importlib-resources, importlib-metadata, h5py, grpcio, google-pasta, google-auth, cffi, bleach, beautifulsoup4, sqlalchemy, requests-oauthlib, qtpy, pluggy, pandas, matplotlib, markdown, keyring, keras-applications, jupyter-client, jsonschema, ipython, argon2-cffi-bindings, pytest, obspy, nbformat, keras, ipykernel, google-auth-oauthlib, argon2-cffi, tensorboard, qtconsole, nbclient, jupyter-console, tensorflow, nbconvert, notebook, widgetsnbextension, ipywidgets, jupyter, EQTransformer
	Successfully installed EQTransformer-0.1.59 MarkupSafe-2.1.1 Send2Trash-1.8.0 absl-py-1.1.0 argon2-cffi-21.3.0 argon2-cffi-bindings-21.2.0 astor-0.8.1 atomicwrites-1.4.0 attrs-21.4.0 backcall-0.2.0 beautifulsoup4-4.11.1 bleach-5.0.0 cachetools-4.2.4 certifi-2022.5.18.1 cffi-1.15.0 charset-normalizer-2.0.12 colorama-0.4.4 cycler-0.11.0 debugpy-1.6.0 decorator-5.1.1 defusedxml-0.7.1 entrypoints-0.4 fastjsonschema-2.15.3 fonttools-4.33.3 gast-0.2.2 google-auth-1.35.0 google-auth-oauthlib-0.4.6 google-pasta-0.2.0 greenlet-1.1.2 grpcio-1.46.3 h5py-2.10.0 idna-3.3 importlib-metadata-4.11.4 importlib-resources-5.7.1 iniconfig-1.1.1 ipykernel-6.13.0 ipython-7.34.0 ipython-genutils-0.2.0 ipywidgets-7.7.0 jedi-0.18.1 jinja2-3.1.2 jsonschema-4.6.0 jupyter-1.0.0 jupyter-client-7.3.1 jupyter-console-6.4.3 jupyter-core-4.10.0 jupyterlab-pygments-0.2.2 jupyterlab-widgets-1.1.0 keras-2.3.1 keras-applications-1.0.8 keras-preprocessing-1.1.2 keyring-23.5.1 kiwisolver-1.4.2 lxml-4.9.0 markdown-3.3.7 matplotlib-3.5.2 matplotlib-inline-0.1.3 mistune-0.8.4 nbclient-0.6.4 nbconvert-6.5.0 nbformat-5.4.0 nest-asyncio-1.5.5 notebook-6.4.11 numpy-1.21.6 oauthlib-3.2.0 obspy-1.3.0 opt-einsum-3.3.0 packaging-21.3 pandas-1.3.5 pandocfilters-1.5.0 parso-0.8.3 pickleshare-0.7.5 pillow-9.1.1 pkginfo-1.8.2 pluggy-1.0.0 prometheus-client-0.14.1 prompt-toolkit-3.0.29 protobuf-4.21.1 psutil-5.9.1 py-1.11.0 pyasn1-0.4.8 pyasn1-modules-0.2.8 pycparser-2.21 pygments-2.12.0 pyparsing-3.0.9 pyrsistent-0.18.1 pytest-7.1.2 python-dateutil-2.8.2 pytz-2022.1 pywin32-304 pywin32-ctypes-0.2.0 pywinpty-2.0.5 pyyaml-6.0 pyzmq-23.1.0 qtconsole-5.3.0 qtpy-2.1.0 requests-2.27.1 requests-oauthlib-1.3.1 rsa-4.8 scipy-1.4.1 six-1.16.0 soupsieve-2.3.2.post1 sqlalchemy-1.4.37 tensorboard-2.0.2 tensorflow-2.0.0 tensorflow-estimator-2.0.1 termcolor-1.1.0 terminado-0.15.0 tinycss2-1.1.1 tomli-2.0.1 tornado-6.1 tqdm-4.48.0 traitlets-5.2.2.post1 typing-extensions-4.2.0 urllib3-1.26.9 wcwidth-0.2.5 webencodings-0.5.1 werkzeug-2.1.2 widgetsnbextension-3.6.0 wrapt-1.14.1 zipp-3.8.0
	
	(eqt) E:\>

Maka `EQTransformer` telah berhasil terinstall, Selamat mencoba















