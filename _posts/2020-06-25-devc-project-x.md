---
layout: post
title:  "DevC Project X"
date:   2020-06-23 00:00:00 +0700
meta:   "Tingkat Kesulitan: Medium (50 Poin)"
categories: problem
---

### Deskripsi

Dirgantara Enterprise Vehicle Corporation (DevC) adalah sebuah perusahaan besar yang bergerak di bidang aviasi dan otomotif. Terdapat $n$ karyawan di perusahaan DevC yang dinomori dari 1 hingga $n$, dengan karyawan nomor 1 sebagai CEO DevC. Tiap karyawan kecuali CEO mempunyai tepat satu orang atasan langsung (atau direct report), sehingga struktur karyawan di perusahaan DevC menyerupai pohon (atau tree). Berikut adalah contoh strukturnya untuk $n = 8$.


![image](https://s3.amazonaws.com/hr-assets/0/1591706822-8152b60952-UntitledDiagram.jpg)

DevC mengerjakan banyak proyek, salah satunya adalah proyek X. Proyek X ini dikerjakan oleh $k$ orang karyawan, yaitu $x_1, x_2, \dots, x_k$. Untuk memastikan kelancaran proyek ini, tiap karyawan yang terlibat harus melaporkan progressnya kepada atasan langsungnya. Tiap atasan ini juga harus melaporkan ke atasannya lagi, begitu seterusnya hingga CEO mengetahui progress proyek X ini.

Sebagai contoh, misalnya proyek X dikerjakan oleh karyawan 3, 4, dan 8. Maka, banyaknya orang yang mengetahui progress proyek X ada sebanyak 6 orang, yaitu karyawan 1, 2, 3, 4, 6, dan 8. Untuk lebih jelasnya, lihat diagram berikut. Warna biru menyatakan karyawan yang terlibat langsung dalam proyek X, sedangkan warna hijau menyatakan karyawan yang mendapatkan laporan progress dari bawahannya.


![image](https://s3.amazonaws.com/hr-assets/0/1591706833-ad719ea685-UntitledDiagram1.jpg)

Tugas Anda pada persoalan ini adalah menentukan banyaknya karyawan yang pada akhirnya mengetahui progress report proyek X tersebut!

### Format Masukan

Baris pertama berisi 2 buah bilangan, $n$ dan $k$, yang masing-masing menyatakan banyaknya karyawan DevC dan banyaknya karyawan yang terlibat dalam proyek X.

Baris kedua berisi $n$ buah bilangan $d_i$, di mana $d_i$ menyatakan atasan langsung karyawan ke-$i$. Karena CEO tidak mempunyai atasan langsung, maka $d_1 = 0$.

Baris ketiga berisi $k$ buah bilangan $x_i$, yang menyatakan karyawan-karyawan yang terlibat dalam proyek X.

### Batasan

Untuk 50% kasus:

- $1 \le n \le 1000$.

Untuk semua kasus:

- $1 \le n \le 100000$.
- $d_1 = 0$, dan $1 \le d_i < i$ untuk $i = 2 \dots n$. Artinya, indeks atasan langsung $i$ pasti lebih kecil dari $i$.
- $1 \le k \le n$.
- $1 \le x_i \le n$ untuk $i = 1 \dots k$, dan $x_i$ pasti berbeda-beda.


### Format Keluaran

Keluarkan sebuah bilangan yang menyatakan banyaknya karyawan yang pada akhirnya mengetahui progres report proyek X. Perhatikan bahwa $k$ orang yang terlibat langsung dalam proyek X ini pasti termasuk di dalamnya.

#### Contoh Masukan 0

```
8 3
0 1 1 2 2 2 6 6
3 4 8
```


#### Contoh Keluaran 0

```
6
```
