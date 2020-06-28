---
layout: post
title:  "DevC Meetup Venue"
date:   2020-06-23 00:00:00 +0700
meta:   "Tingkat Kesulitan: Hard (80 Poin)"
categories: problem
---

### Deskripsi

Acep ingin menghadiri meetup DevC, tapi Acep tersesat! Peta lokasi Acep sekarang dapat direpresentasikan sebagai kotak $n \times n$, di mana tiap sel dapat berupa kotak kosong yang bisa dilewati, atau tembok. Sel pada baris $r$ dan kolom $c$ bisa kita notasikan dengan koordinat $(r, c)$, di mana baris dan kolom dinomori dari $1 \dots n$.

Sekarang, Acep berada di koordinat $(A_r, A_c)$, atau di baris $A_r$ dan kolom $A_c$. Acep hanya bisa bergerak ke sel yang bersebelahan di atas, bawah, kiri, atau kanannya saja, dan tentu saja dia tidak bisa melewati tembok. Acep juga tahu bahwa venue meetup berada di koordinat $(M_r, M_c)$. Bantulah Acep untuk mencari jalan mencapai venue meetup!


### Format Masukan

Baris pertama berisi bilangan bulat $n$ yang menyatakan ukuran maze.

Baris kedua berisi 4 buah bilangan bulat, $A_r, A_c, M_r, M_c$ yang menyatakan koordinat Acep dan venue.

$n$ buah baris berikutnya masing-masing berisi $n$ buah karakter, yang menggambarkan peta. Karakter `.` menyatakan kotak kosong yang bisa dilewati, dan karakter `#` menyatakan tembok yang tidak bisa dilewati.


### Batasan

$1 \le n \le 100$

$1 \le A_r, A_c, M_r, M_c \le n$

Koordinat $(A_r, A_c)$ dan $(M_r, M_c)$ berbeda, dan keduanya bukan tembok


### Format Keluaran

Jika Acep tidak dapat mencapai venue meetup, keluarkan string `tersesat`.

Jika Acep dapat mencapai venue meetup, Keluarkan jalan yang harus Acep tempuh dari lokasi dia sekarang hingga ke venue meetup. Jalan ini direpresentasikan dengan string yang terdiri atas karakter `R` (right/kanan), `L` (left/kiri), `U` (up/atas), `D` (down/bawah), sedemikian sehingga jika Acep mengikuti jalan tersebut, dia dapat mencapai venue meetup dari lokasinya sekarang. Untuk lebih jelas, lihat penjelasan Sample 0.

Perhatikan bahwa Anda tidak harus mencari jalan yang paling pendek dalam soal ini. Jika ada lebih dari satu jalan yang memenuhi, Anda dapat mengeluarkan jawaban manapun. Tapi, pastikan panjang jawaban Anda tidak melebihi 10 ribu karakter.

#### Contoh Masukan 0

```
4
2 3 4 1
....
.#..
.##.
....
```


#### Contoh Keluaran 0

```
ULLDDD
```

#### Penjelasan 0

Jalan yang ditempuh Acep jika mengikuti output di atas adalah sebagai berikut, di mana `A` adalah lokasi Acep saat ini, `M` adalah lokasi venue meetup, dan `x` adalah jalan yang akan dia tempuh.

```
xxx.
x#A.
x##.
M...
```

Perhatikan bahwa `RDDLLL` juga merupakan solusi yang valid untuk contoh ini.


#### Contoh Masukan 1

```
4
2 3 4 1
..#.
.#..
.##.
...#
```

#### Contoh Keluaran 1

```
tersesat
```
