---
layout: post
title:  "DevC Online Meetup"
date:   2020-06-23 00:00:00 +0700
meta:   "Tingkat Kesulitan: Easy (20 Poin)"
categories: problem
---

### Deskripsi

Di masa seperti sekarang ini, DevC tetap mengadakan meetup walaupun secara online. Meetup dilakukan dengan menggunakan fitur Live Streaming di grup.

Pada saat streaming dimulai, tidak ada orang yang menonton. Oleh karena itu biasanya tiap meetup online dimulai dengan sekitar 3 menit *splash background* untuk mengumpulkan orang-orang. Seiring berjalannya waktu, tentu saja orang-orang akan berdatangan dan tentu juga bisa jadi ada orang yang meninggalkan live streaming di tengah-tengah meetup.

Anda akan diberikan $N$ notifikasi sepanjang live streaming, yang berisi berapa banyak orang yang bergabung atau pergi. Notifikasi-notifikasi ini tentunya diberikan secara berurutan sesuai waktu.

Anda sebagai DevC lead penasaran berapa orang paling banyak yang menonton live streaming pada saat yang bersamaan.

### Format Masukan

Baris pertama berisi bilangan bulat $N$ yang menyatakan banyaknya notifikasi.

Baris berikutnya berisi $N$ buah bilangan bulat $D_i$, yang menyatakan banyaknya orang yang bergabung atau pergi pada tiap notifikasi. Nilai $D_i$ yang positif berarti ada $D_i$ orang yang bergabung, dan nilai $D_i$ yang negatif berarti ada $\vert D_i\vert $ orang yang pergi.

### Batasan

- $1 \le N \le 1000000$
- $1 \le \vert D_i\vert  \le 1000$
- Banyaknya orang yang menonton pada setiap waktu non-negatif.

### Format Keluaran

Keluarkan sebuah bilangan bulat yang menyatakan berapa orang paling banyak yang menonton live streaming pada saat yang bersamaan.


#### Contoh Masukan 0

```
8
1 4 9 -2 -1 6 -4 1
```


#### Contoh Keluaran 0

```
17
```

#### Penjelasan 0

Pada notifikasi ke-6, ada tepat 17 orang yang menonton secara bersamaan.
