---
layout: post
title:  "Stacking Books"
date:   2020-06-23 00:00:00 +0700
meta:   "Tingkat Kesulitan: Medium (60 Poin)"
categories: problem
---

### Deskripsi

Sandra sangat suka membaca! Dia mempunyai banyak buku di rumahnya. Tiap buku yang sedang dia baca biasanya dia letakkan di atas meja agar tidak lupa.

Saat ini Sandra sedang membaca dua buku dan dia menumpuk kedua bukunya di atas meja. Jika dilihat dari atas, gabungan kedua buku tersebut membentuk suatu bangun datar.

Meja Sandra bisa dianggap sebagai koordinat kartesian dengan $x, y \ge 0$. Tiap buku berupa persegi panjang yang sisi-sisinya sejajar dengan sumbu $x$ dan $y$. Buku pertama memilki koordinat kiri bawah $(ax_1, ay_1)$ dan kanan atas $(ax_2, ay_2)$, dan buku kedua memililki koordinat kiri bawah $(bx_1, by_1)$ dan kanan atas $(bx_2, by_2)$. Untuk lebih jelasnya, perhatikan diagram di bawah ini.

![image](https://s3.amazonaws.com/hr-assets/0/1592391757-3ac0f8d9c5-WhatsAppImage2020-06-17at18.02.24.jpeg)

Buku pertama (yang berwarna merah) memiliki koordinat $(2, 1)$ dan $(5, 6)$, dan buku kedua (yang berwarna biru) memiliki koordinat $(4, 3)$ dan $(9, 7)$.

Sandra penasaran dengan keliling bangun datar yang dibentuk dari gabungan kedua buku tersebut. Pada kasus di atas, bangun datar yang terbentuk adalah yang diberi warna hitam, dan kelilingnya adalah 26.

Sandra penasaran, namun dia sibuk membaca buku. Oleh karena itu, dia meminta bantuan Anda untuk mencari tahu jawabannya!


### Format Masukan

Baris pertama berisi 4 buah bilangan bulat $ax_1, ay_1, ax_2, ay_2$, dan baris kedua berisi 4 buah bilangan bulat $bx_1, by_1, bx_2, by_2$, yang masing-masing menyatakan koordinat buku pertama dan kedua seperti yang dijelaskan di atas.


### Batasan

- $0 \le ax_1, ay_1, ax_2, ay_2, bx_1, by_1, bx_2, by_2 \le 1000000$.
- $ax_1 <  ax_2, ay_1 < ay_2, bx_1 < bx_2, by_1 < by_2$.
- Luas daerah irisan kedua buku > 0.


### Format Keluaran

Keluarkan sebuah bilangan bulat yang berisi keliling bangun datar yang terbentuk dari kedua buku tersebut.

#### Contoh Masukan 0

```
2 1 5 6
4 3 9 7
```


#### Contoh Keluaran 0

```
26
```
