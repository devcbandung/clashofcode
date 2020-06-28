---
layout: post
title:  "BLT Seat Distancing"
date:   2020-06-25 00:00:00 +0700
meta:   "Tingkat Kesulitan: Easy (20 Poin)"
categories: problem
---

### Deskripsi

Bimo merupakan salah satu panitia yang membagikan bantuan BLT dari pemerintah, dan dia ditugaskan untuk mengatur kursi duduk untuk para warga agar tidak saling berdekatan. Kursi duduk dapat direpresentasikan sebagai kotak dengan ukuran $x \times x$. Area tempat duduk berukuran $p$ baris dan $l$ kolom.

Agar memudahkan pekerjaannya, Bimo ingin mencetak penempatan kursi tersebut. Setiap tempat duduk akan diberikan tanda `*` berukuran $x \times x$, dan tiap kotak di sebelah kursi dikosongkan atau diberi spasi ` ` yang juga berukuran $x \times x$ untuk menjaga jarak antar warga.

Untuk lebih jelasnya, di bawah ini adalah penempatan kursi untuk $x = 3$, $p = 2$, dan $l = 4$.

```
***   ***   
***   ***   
***   ***   
   ***   ***
   ***   ***
   ***   ***
```

Bantulah Bimo untuk membuat program yang mencetak penempatan kursi tersebut!


### Format Masukan

Masukan terdiri dari sebuah baris yang berisi 3 buah bilangan bulat yang dipisahkan oleh spasi, $x$, $p$, dan $l$, yang masing-masing menyatakan ukuran kursi, banyak baris, dan kolom area tempat duduk.

### Batasan

$1 \le x, p, l \le 20$

### Format Keluaran

Keluarkan penempatan kursi seperti pada contoh.

Perhatikan bahwa keluaran **harus menuliskan semua spasi, termasuk pada akhir baris** (sebagai contoh, 3 baris pertama pada sample 0 diakhiri dengan 3 buah spasi). Keluaran juga **harus menuliskan *newline* setelah baris paling terakhir**.

#### Contoh Masukan 0

```
3 2 4
```


#### Contoh Keluaran 0

```
***   ***   
***   ***   
***   ***   
   ***   ***
   ***   ***
   ***   ***
```

#### Contoh Masukan 1

```
5 3 2
```

#### Contoh Keluaran 1

```
*****     
*****     
*****     
*****     
*****     
     *****
     *****
     *****
     *****
     *****
*****     
*****     
*****     
*****     
*****     
```
