---
layout: post
title:  "Closing the Portal"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Hard |
| **Kategori** | Graph, DFS/BFS, Game Theory |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/closing-the-portal) |
| **Pranala Solusi** | [Solusi 50% (Bitmask)]({{ site.solution_file }}/closing-the-portal/solution_bitmask.cpp), [Solusi 100%]({{ site.solution_file }}/closing-the-portal/solution.cpp) |

## Solusi untuk $N,M \le 4$

Saat $N, M \le 4$, hanya ada paling banyak $2^{14} = 16384$ kemungkinan permainan (karena 2 petak adalah portal yang tidak bisa diubah-ubah). Kita dapat menyimulasikan semua kemungkinan permainan, dengan menyimpan state yang sudah pernah dikunjungi (atau memoisasi).

Kita dapat menyimpan state maze sebagai bilangan biner, dengan 1 menyatakan tembok dan 0 menyatakan petak kosong. Teknik ini disebut juga dengan DP Bitmask.

## Solusi untuk $N,M \le 100$

Untuk nilai $N$ dan $M$ yang besar, tentu kita tidak dapat menyimulasikan semua kemungkinan permainan. Kita perlu melakukan beberapa observasi tentang kondisi apa yang menyebabkan Alif atau Bella menang.

Pertama-tama, kita bisa mencari jalan dari portal yang satu ke portal yang lainnya dengan menggunakan DFS/BFS (lihat [pembahasan DevC Meetup Venue]({{ '/editorial/devc-meetup-venue' | relative_url }})). Jika tidak ada jalan antara keduanya, maka Bella pasti menang.

Jika ada jalan antara kedua portal, perhatikan langkah terakhir yang dilakukan salah satu pemain sebelum dia kalah. Perhatikan bahwa pada saat ini, **semua petak kecuali salah satu jalan di antara kedua portal pasti sudah menjadi tembok**.

Misalkan kita mempunyai sebuah peta awal sebagai berikut:

```
.O#..
....O
.#.#.
.....
#....
```

Berikut adalah beberapa kemungkinan kondisi peta sebelum langkah terakhir dilakukan.

```
#O###  #O###  #O###  #O###  #O###  .O###
#...O  #..#O  #..#O  ..##O  ..##O  .#..O
#####  ##.#.  ##.#.  .###.  .###.  .#.##
#####  ##...  ##.#.  ..##.  ..#..  ...##
#####  #####  ##...  #....  #...#  #####
```

Apakah kesamaan dari semua kemungkinan di atas? Perhatikan **banyaknya petak kosong di antara kedua portal**. Tiap-tiap kemungkinan di atas mempunyai masing-masing 3, 7, 11, 11, dan 9 petak kosong, dan semuanya adalah bilangan ganjil. Ini bukan suatu kebetulan, karena **ganjil/genapnya panjang jalur hanya ditentukan dari posisi kedua portal**.

Pembuktiannya adalah sebagai berikut. Pada contoh di atas, coba perhatikan langkah vertikal (ke atas/bawah) saat kita berjalan dari portal kiri ke portal kanan. Posisi portal kedua adalah satu langkah di bawah portal pertama. Bagaimanapun jalan yang ditempuh, pasti akan terdapat $k$ kali langkah ke atas dan $k+1$ kali langkah ke bawah untuk suatu $k$, dengan total $2k+1$ langkah. Ganjil/genapnya nilai ini tidak bergantung pada nilai $k$. Cara yang sama dapat dilakukan untuk langkah horizontal (ke kiri/kanan). Jadi, terbukti bahwa genap/ganjilnya panjang jalur hanya ditentukan oleh posisi kedua portal.

Sekarang kita dapat menentukan pemenangnya dengan tambahan informasi di atas. Kembali ke contoh di atas, ambil contoh kemungkinan pertama:

```
.O#..     #O###
....O     #...O
.#.#. --> #####
.....     #####
#....     #####
-----     -----
 4 #       20 #
```

Dari kondisi awal ke kondisi akhir, ada selisih 16 tembok, atau dengan kata lain ada 16 langkah dari awal hingga akhir. Berarti, kita tahu bahwa pada kondisi akhir ini, Alif lah yang akan jalan, karena 16 merupakan angka genap. Dan kita juga tahu bahwa di semua kemungkinan lainnya, tetap Alif yang akan jalan, karena banyaknya langkah akan selalu genap. Sehingga apapun kasusnya, Alif pasti kalah.

Jadi, untuk menentukan pemenangnya, **kita dapat menentukan berapa banyak langkah yang diperlukan dari kondisi awal hingga *salah satu* kondisi akhir**. Setelah itu, kita cukup melihat genap/ganjil nilai tersebut.

```
// misalkan shortest adalah langkah terpendek dari portal yang
// satu ke yang lainnya, dengan mengikutsertakan kedua petak
// portal di dalam perhitungannya.
shortest = shortestPath()

// perhatikan bahwa kita tidak harus mencari langkah terpendek;
// sebagai contoh, solusi dengan DFS yang tidak mencari jalan
// yang terpendek tetap akan menghasilkan jawaban yang benar.

// kalau tidak ada jalan antara kedua portal, maka Bella yang menang
if (shortest == -1) {
  print("Bella")
  return
}

// selain itu, hitung banyaknya tembok pada kondisi awal
nWalls = ...

// kemudian hitung berapa langkah yang dibutuhkan dari kondisi
// awal hingga akhir
turns = (R*C - shortest) - nWalls

// jika angka ini genap, maka Bella yang menang.
// sebaliknya jika angka ini ganjil, maka Alif yang menang.
if (turns mod 2 == 0) {
  print("Bella")
} else {
  print("Alif")
}
```
