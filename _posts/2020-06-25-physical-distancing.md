---
layout: post
title:  "Physical Distancing"
date:   2020-06-23 00:00:00 +0700
meta:   "Tingkat Kesulitan: Expert (150 Poin)"
categories: problem
---

### Deskripsi

Di era pandemi seperti sekarang ini, kita semua sudah tidak asing lagi dengan istilah *physical distancing*. Aturan *physical distancing* mengharuskan setiap orang untuk menjaga jaraknya dengan semua orang lain lebih dari $d$ meter setiap saat. Namun, saat aktivitas orang-orang mulai berjalan lagi, aturan ini jadi sangat mungkin untuk dilanggar.

Terdapat $N$ orang, di mana orang ke-$i$ pada awalnya berada di koordinat $(x_i, y_i)$. Koordinat yang digunakan di sini dalam satuan meter, atau dengan kata lain, jarak antara koordinat $(0, 0)$ dan $(0, 1)$ adalah satu meter. Jarak antara dua koordinat mengikuti aturan Pythagoras, yaitu jarak antara koordinat $(a, b)$ dan $(c, d)$ adalah $\sqrt{(a-c)^2 + (b-d)^2}$.

Karena aktivitas sudah mulai berjalan, tentu saja orang-orang ini tidak akan diam saja. Orang ke-$i$ berjalan dengan kecepatan konstan $v_i$ meter per detik, ke utara ataupun ke selatan. Jika orang itu berjalan ke utara, maka koordinat $y$ nya akan bertambah sebanyak $v_i$ meter per detik, dan sebaliknya, jika orang itu berjalan ke selatan, koordinat $y$ nya akan berkurang sebanyak $v_i$ per detik. Koordinat $x$ semua orang tidak akan berubah. Semua orang berjalan secara serentak dengan kecepatannya masing-masing dan tidak akan berhenti.

Sebagai pengamat pandemi, Anda ingin mengamati seberapa sering aturan *physical distancing* ini dilanggar, atau dengan kata lain hitunglah berapa pasang orang yang pada suatu waktu akan berjarak $d$ meter atau kurang.

Perhatikan bahwa jika orang ke-1 melanggar *physical distancing* dengan orang ke-2 dan orang ke-3, maka pelanggarannya dihitung 2 kali (bukan 4 kali, karena pasangan orang (1, 2) dan (2, 1) dianggap sama). Dan jika dua orang berjarak tepat $d$ meter, mereka sudah dianggap melanggar aturan *physical distancing*.

Sebagai contoh, misalkan terdapat 5 orang dengan koordinat awal masing-masing $(3, 1), (5, 4), (2, 3), (7, 4), (6,1)$, dan $d = 2$ meter. Orang pertama bergerak 1 m/s, orang kedua 1 m/s, orang ketiga 2 m/s, orang keempat 1 m/s, dan orang kelima 3 m/s. Semua orang bergerak ke utara kecuali orang kedua. Berikut adalah animasi yang menunjukkan pergerakan kelima orang tersebut selama dua detik pertama.

![image](https://i.imgur.com/91mkzj2.gif)

(Jika animasi tidak berjalan, silakan buka pranala [https://i.imgur.com/91mkzj2.gif](https://i.imgur.com/91mkzj2.gif))

P1 dan P2 melanggar *physical distancing* pada $t = 1.5$ walaupun hanya sekejap, begitu pula dengan P2 dan P4 yang melanggarnya pada $t = 0$ walaupun setelah itu mereka bergerak ke arah yang berbeda. P1 dan P3 tidak akan melanggar karena jarak mereka akan terus menjauh, sedangkan P5 “menyusul” P4 sehingga mereka melanggar. Pasangan yang melanggar adalah (P1, P2), (P2, P5), (P2, P4), (P4, P5), sehingga total ada 4 pelanggaran.


### Format Masukan

Baris pertama berisi dua buah bilangan bulat $N$ dan $d$ yang menyatakan banyaknya orang dan jarak pada aturan *physical distancing*.

Tiap dari $N$ baris berikutnya berisi 3 buah bilangan bulat, $x_i$, $y_i$, $v_i$ yang menjelaskan posisi dan kecepatan orang ke-$i$. $(x_i, y_i)$ adalah posisi awal orang ke-$i$, $v_i$ menyatakan kecepatan orang ke-$i$ dalam meter per detik. $v_i$ dapat berupa bilangan positif atau negatif. Jika $v_i$ positif, maka orang ke-$i$ bergerak ke utara, dan jika $v_i$ negatif, maka orang ke-$i$ bergerak ke selatan.


### Batasan

Untuk 30% kasus:

- $1 \le N \le 1000$
- $0 \le x_i, y_i,  \vert v_i \vert  \le 1000$

Untuk 50% kasus:

- $1 \le N \le 1000$
- $0 \le x_i, y_i,  \vert v_i \vert  \le 100000$

Untuk 100% kasus:

- $1 \le N \le 100000$
- $0 \le x_i, y_i,  \vert v_i \vert  \le 100000$

Untuk semua kasus:

- $1 \le d \le 10$
- Semua bilangan pada masukan adalah bilangan bulat.
- Koordinat $(x_i, y_i)$ tidak dijamin unik. Dengan kata lain, bisa saja ada dua/lebih orang yang berada pada koordinat yang sama pada awalnya. Triplet $(x_i, y_i, v_i)$ juga tidak dijamin unik.
- $v_i$ mungkin 0, atau dengan kata lain orang tersebut tidak bergerak.


### Format Keluaran

Keluarkan sebuah bilangan bulat yang menyatakan berapa pasang orang yang melakukan pelanggaran aturan *physical distancing*, atau dengan kata lain berapa pasang orang yang pada suatu waktu akan berjarak $d$ meter atau kurang.


#### Contoh Masukan 0

```
5 2
3 1 1
5 4 -1
2 3 2
7 4 1
6 1 3
```


#### Contoh Keluaran 0

```
4
```

#### Penjelasan 0

Lihat penjelasan dan animasi di atas
