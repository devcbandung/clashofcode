---
layout: post
title:  "Clock Angle"
date:   2020-06-25 00:00:00 +0700
meta:   "Tingkat Kesulitan: Medium (40 Poin)"
categories: problem
---

### Deskripsi

Jarum jam dan menit pada jam analog pasti membentuk sebuah sudut. Kita semua tahu bahwa sudut yang terbentuk pada jam 3 tepat adalah 90 derajat, dan pada pukul 06:00 adalah sudut lurus atau 180 derajat.

Tugas kalian pada soal ini sangatlah mudah. Hitunglah besar sudut yang dibentuk antara jarum jam dan menit pada waktu yang diberikan!

![](https://i.imgur.com/Rr9unL3.jpg)

### Format Masukan

Masukan berisi sebuah string dengan format `HH:MM` yang menyatakan waktu.

### Batasan

- `HH` di antara `00` dan `23`.
- `MM` di antara `00` dan `59`.

### Format Keluaran

Keluarkan sebuah bilangan real yang menyatakan sudut (dalam derajat) yang dibentuk antara jarum jam dan menit pada pukul `HH:MM`. Bulatkan hingga 1 angka di belakang koma.

Tentunya keluarkan sudut yang lebih kecil, atau dengan kata lain $0 \le angle \le 180$.

#### Contoh Masukan 0

```
03:00
```

#### Contoh Keluaran 0

```
90.0
```

#### Contoh Masukan 1

```
15:00
```

#### Contoh Keluaran 1

```
90.0
```

#### Contoh Masukan 2

```
00:00
```

#### Contoh Keluaran 2

```
0.0
```

#### Contoh Masukan 3

```
00:01
```

#### Contoh Keluaran 3

```
5.5
```
