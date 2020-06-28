---
layout: post
title:  "Closing the Portal"
date:   2020-06-25 00:00:00 +0700
meta:   "Tingkat Kesulitan: Hard (100 Poin)"
categories: problem
---

### Deskripsi

Alif dan Bella sedang bermain sebuah permainan yang dinamakan “Closing the Portal”. Dalam permainan ini, ada grid dengan ukuran $R$ baris dan $C$ kolom. Tiap kotak pada grid bisa berupa kotak kosong, tembok, atau portal. Ada tepat dua portal pada grid tersebut. Kedua pemain harus menjaga kedua portal agar tetap terhubung, atau dengan kata lain, ada jalan yang dapat dilalui dari portal yang satu ke yang lainnya tanpa melalui tembok, jika gerakan yang diperbolehkan hanyalah ke atas, kiri, bawah, dan kanan.

![image](https://s3.amazonaws.com/hr-assets/0/1592392542-1e997a709f-portal.jpg)

Alif dan Bella bermain secara bergantian, dengan Alif yang mengambil langkah pertama. Pada tiap langkahnya, mereka harus mengubah satu kotak kosong menjadi tembok. **Jika setelah giliran X, tidak ada jalan yang menghubungkan kedua portal, maka X dinyatakan kalah**. Kejadian ini disebut juga dengan *closing the portal*. Perhatikan bahwa mengubah portal menjadi tembok bukanlah jalan yang valid. Dapat dipastikan bahwa pasti ada jalan yang valid sampai salah satu dari Alif dan Bella kalah.

Alif dan Bella sangat kompetitif, sehingga mereka berdua pasti bermain secara optimal. Diberikan konfigurasi awal grid, tentukan siapa dari mereka yang memenangkan permainan tersebut!


### Format Masukan

**Pada soal ini, program kalian diharuskan untuk menyelesaikan banyak kasus uji sekaligus, tidak seperti pada soal-soal lainnya yang hanya berisi satu kasus uji pada tiap berkas masukan.**

Baris pertama berisi $T$ yang menyatakan banyaknya kasus uji. Kemudian masukan diikuti oleh $T$ buah kasus uji sebagai berikut.

Baris pertama berisi dua buah bilangan bulat $R$ dan $C$ yang menyatakan ukuran grid.

$R$ baris berikutnya masing-masing berisi string sepanjang $C$ karakter, yang merupakan isi dari grid. Tiap string berisi karakter-karakter berikut:

- `.`: kotak kosong
- `#`: tembok
- `O`: portal (huruf O besar)


### Batasan

Hanya ada dua berkas masukan yang berbobot sama pada soal ini.

Masukan pertama:

- $T = 100$.
- $1 \le R, C \le 4$.

Masukan kedua:

- $T = 100$.
- $1 \le R, C \le 100$.

Untuk kedua kasus uji:

- Ada tepat dua buah portal pada grid (ada tepat dua buah karakter `O` pada masukan).
- Ada paling tidak satu kotak kosong (sehingga pemain pertama bisa jalan).
- Kedua portal tidak bersebelahan.

### Format Keluaran

Keluaran berisi $T$ baris di mana masing-masing baris adalah jawaban dari tiap kasus uji.

Untuk tiap kasus uji, tuliskan `Alif` jika Alif menang, dan `Bella` jika Bella yang menang.


#### Contoh Masukan 0

```
2
3 3
O..
.#.
..O
1 10
..O.#...O.
```


#### Contoh Keluaran 0

```
Alif
Bella
```

#### Penjelasan 0

Pada kasus uji pertama, salah satu permainan yang optimal adalah sebagai berikut.

![image](https://s3.amazonaws.com/hr-assets/0/1592560884-aad134144d-portal2.jpg)

Sekarang adalah giliran Bella, dan apapun langkah yang dia ambil, dia pasti menutup jalan antara kedua portal.

Sedangkan pada kasus kedua, dari awal memang sudah tidak ada jalan antara kedua portal. Jadi, langkah apapun yang Alif ambil, dia pasti kalah.
