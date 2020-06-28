---
layout: post
title:  "DevC Volunteers"
date:   2020-06-23 00:00:00 +0700
meta:   "Tingkat Kesulitan: Advanced (120 Poin)"
categories: problem
---

### Deskripsi

Seperti yang kalian ketahui, peran volunteer di DevC sangatlah penting. Tanpa mereka, event-event DevC tidak mungkin dapat terlaksana dengan baik.

Anda sebagai DevC lead ingin menjadwalkan meetup untuk $N$ hari ke depan. DevC dapat mengadakan maksimal satu meetup tiap harinya. Dan tentu saja DevC ingin mengadakan meetup sebanyak mungkin dalam $N$ hari tersebut.

Agar meetup dapat terlaksana, harus ada paling tidak satu volunteer yang hadir. DevC mempunyai $M$ orang volunteer yang dinomori dari 1 hingga $M$. Volunteer ke-$i$ hanya punya waktu kosong dari hari $A_i$ sampai hari $B_i$ saja. Selain itu, jika seorang volunteer sudah hadir di meetup pada hari ke-$d$, dia harus istirahat keesokan harinya, dan paling cepat baru bisa hadir di meetup pada hari ke-$d+2$. **Dengan kata lain, setiap volunteer tidak dapat menghadiri dua meetup pada hari yang berurutan.**

Dengan syarat seperti itu, buatlah jadwal meetup untuk $N$ hari ke depan, beserta volunteer mana saja yang harus hadir di tiap meetup. Buatlah jadwal yang **memaksimalkan banyaknya meetup** yang dapat terlaksana. Jika ada lebih dari satu kemungkinan jadwal dan *assignment* volunteer, Anda dapat memilih yang mana saja.


### Format Masukan

Baris pertama berisi dua buah bilangan bulat, $N$ dan $M$, yang menyatakan jumlah hari dan banyaknya volunteer.

$M$ baris berikutnya masing-masing berisi 2 buah bilangan bulat, $A_i$ dan $B_i$, yang menyatakan waktu kosong dari volunteer ke-$i$, inklusif (artinya volunteer ke-$i$ kosong pada semua hari $d$ untuk semua $A_i \le d \le B_i$).


### Batasan

Untuk 50% kasus:

- $1 \le N, M \le 500$

Untuk 100% kasus:

- $1 \le N, M \le 100000$

Untuk semua kasus:

- $1 \le A_i \le B_i \le N$


### Format Keluaran

Keluarkan jadwal meetup yang memaksimalkan banyaknya meetup dalam $N$ hari.

Baris pertama dari keluaran berisi sebuah bilangan bulat yang menyatakan banyaknya meetup yang dapat terlaksana.

Tiap baris berikutnya berisi detail tiap meetup, dalam format `d x_1 x_2 ... x_k`, di mana $d$ adalah hari meetup tersebut dilaksanakan, dan $x_1, x_2, \dots x_k$ adalah volunteer-volunteer yang harus hadir pada meetup tersebut.

Jawaban harus diurutkan secara menaik berdasarkan hari meetup ($d$), sedangkan urutan $x_i$ dapat diabaikan, asalkan:

- paling tidak ada satu volunteer pada tiap meetup ($k \ge 1$),
- nilai-nilai $x_i$ unik dalam sebuah meetup,
- semua volunteer $x_i$ sedang kosong pada hari tersebut, dan
- tidak ada volunteer yang hadir dua hari berturut-turut.

Jika ada banyak kemungkinan jawaban, jawaban manapun akan dianggap benar, asalkan jawaban tersebut memaksimalkan banyaknya meetup dan memenuhi syarat-syarat di atas.


#### Contoh Masukan 0

```
5 3
1 3
2 4
3 5
```


#### Contoh Keluaran 0

```
5
1 1
2 2
3 1 3
4 2
5 3
```

#### Penjelasan 0

Ada 3 volunteer dengan hari kosong masing-masing $[1, 3]$, $[2, 4]$, dan $[3, 5]$. Perhatikan bahwa kita bisa mengadakan meetup setiap hari, dengan pemilihan volunteer yang tepat.

Berikut adalah jadwal meetup dan pemilihan volunteer jika direpresentasikan dalam tabel. tanda `[]` menyatakan bahwa volunteer itu kosong pada rentang hari tersebut

```
Hari        | 1 | 2 | 3 | 4 | 5 |
------------ --- --- --- --- --- 
Volunteer 1 |[x |   | x]|   |   |
Volunteer 2 |   |[x |   | x]|   |
Volunteer 3 |   |   |[x |   | x]|
```

#### Contoh Masukan 1

```
3 2
1 1
1 3
```

#### Contoh Keluaran 1

```
2
1 1 2
3 2
```

#### Penjelasan 1

Perhatikan bahwa bagaimanapun caranya, kita tidak bisa mengadakan 3 meetup berturut-turut dengan kedua volunteer yang diberikan.