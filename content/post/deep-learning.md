---
title: "Deep Learning"
date: 2021-07-03T11:05:13+07:00
draft: false
comments: true
categories:
- machine_learning
- deep_learning
tags:
- jupyter_notebook
- python

---

Kali ini saya kaan mengulas tentang **Deep Learning (DL)**

Apa itu DL sudah pernah saya singgung **disini**.

Sebagai contoh kita akan mengklasidikasikan penderita diabetes atau bukan berdasarkan data rekam medis dari 1000 orang sehingga kita data x sebanyak 1000. 

Jumlah jenis data medis yang digunakan sebanyak 8 item sperti pada tabel berikut.

Kita membuat 4 layer dimana setiap layer terdiri dari beberapa node.

Saya akan menjelaskan bagaimana tranformasi data bekerja.

Ibaratkan ada 1000 orang yang masing-masing membawa 8 data, dia harus melewati setiap layer yang terdiri dari beberapa node satu persatu secara berurutan.

Bayangkan bahwa node itu adalah loket, jadi setiap orang yang masuk ke dalam loket (node) akan keluar membawa 1 data saja dari sebelumnya 8 data.

Darimana 1 data tersebut diperoleh ?

Dari rumus berikut :

Jadi setiap node itu memiliki sejumlah x nilai weight (w) dan nilai sejumlah node nilai bias (b).

Ok kembali ke awal. Setelah seluruh orang masuk ke semua node pada layer 1 maka sekarang 1000 orang tersebut memiliki tinggal memiliki 4 data saja atau sejumlah jumlah loket (node).

Nah proses tersebut dilakukan di setiap layer secara berututan hingga layer terakhir atau output layer. Katakan kita set hanya 2 node yang ada pada layer output dengan nilai [1 0] untuk klasifikasi penderita diabetes, dan (0 1) untuk klasifisika si sehat.

Untuk lebih jelasnya mari kita simak coding berikut.

Coding berikut dijalankan dengan jupyter notebook, bagi anda yang belum menginstall nya bisa membaca artikel berikut 




Catatan :

Pengolahan data ini sudah pernah di bahas pada channel yotub berikut namund engan beberapa modifikasi.  
  

 