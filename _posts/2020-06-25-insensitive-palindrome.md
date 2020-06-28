---
layout: post
title:  "Insensitive Palindrome"
date:   2020-06-23 00:00:00 +0700
meta:   "Tingkat Kesulitan: Easy (30 Poin)"
categories: problem
---

### Deskripsi

Kalian pasti pernah mendengar apa itu palindrome. Palindrome adalah sebuah string yang sama jika dibaca dari depan ataupun belakang. Contohnya adalah `kasurrusak`.

Sebuah palindrome dikatakan *sensitive* jika string yang dibalik memiliki huruf kapital dan huruf kecil yang sama persis dengan string aslinya. Sebaliknya, sebuah palindrome dikatakan *insensitive* jika string yang dibalik dibaca sama, namun ada huruf-huruf yang kapitalisasinya berbeda.

Sebagai contoh, `KasurRusak` adalah *insensitive* palindrome karena jika dibalik akan menjadi `kasuRrusaK`, sedangkan `KasuRRusaK` adalah *sensitive* palindrome.

Tugas kalian pada soal ini adalah menentukan sebuah string merupakan *sensitive* atau *insensitive* palindrome atau bukan.


### Format Masukan

Masukan berisi sebuah string $s$, yang terdiri dari huruf-huruf `a-zA-Z` saja.


### Batasan

Panjang $s$ di antara 1 hingga 10000 karakter.

$s$ hanya terdiri dari huruf-huruf `a-zA-Z` dan tidak mengandung spasi.


### Format Keluaran

Jika $s$ adalah *sensitive* palindrome, keluarkan `sensitive palindrome`.

Jika $s$ adalah *insensitive* palindrome, keluarkan `insensitive palindrome`.

Selain itu, atau dengan kata lain jika $s$ bukan palindrome, keluarkan `not a palindrome`.

#### Contoh Masukan 0

```
KasurRusak
```


#### Contoh Keluaran 0

```
insensitive palindrome
```

#### Contoh Masukan 1

```
KasuRRusaK
```

#### Contoh Keluaran 1

```
sensitive palindrome
```

#### Contoh Masukan 2

```
kasur
```

#### Contoh Keluaran 2

```
not a palindrome
```
