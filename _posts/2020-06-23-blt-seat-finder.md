---
layout: post
title:  "BLT Seat Finder"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Medium |
| **Kategori** | Special |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/blt-seat-finder) |
| **Pranala Solusi** | [Solusi (Hardcode)]({{ site.solution_file }}/blt-seat-finder/solution_hardcode.cpp), [Solusi (1 Submisi)]({{ site.solution_file }}/blt-seat-finder/solution_blt-seat-distancing_1submission.cpp) |

Soal-soal seperti ini menyerupai soal-soal pada [Codeforces April Fool's Contest](https://codeforces.com/contest/1331) atau kebanyakan soal-soal CTF (Capture the Flag), di mana tidak ada *problem statement* yang jelas, dan kita harus mencari tahu apa yang dimaksud oleh soal tersebut. Berikut contoh salah satu soal dari [Codeforces April Fool's Contest 2020](https://codeforces.com/contest/1331/problem/C) yang lalu:

![]({{ '/assets/images/blt-seat-finder-1.png' | relative_url }})

Sekarang kembali ke soal BLT Seat Finder. Dari hint kita tahu bahwa soal ini berhubungan dengan soal BLT Seat Distancing. Dan setelah kita melihat kedua contoh, kita akan menemukan bahwa **keluaran dari kedua contoh sama dengan contoh masukan pada soal BLT Seat Distancing**. Hal ini membuat kita bisa menebak bahwa yang diminta pada soal ini adalah **mencari kasus uji pada soal BLT Seat Distancing**. Jika kalian lihat pada hasil submisi pada soal BLT Seat Distancing, semua kasus uji dinomori dari 0 hingga 11, sesuai dengan batasan masukan $tc$.

## Cara 1: Coba-Coba

Cara yang paling "mudah" adalah dengan mencoba-coba, karena nilai batasan $x$, $p$, dan $l$ yang cukup kecil (hanya 1 hingga 20). Ada banyak cara untuk melakukan hal ini, salah satunya adalah sebagai berikut:

```
read(x, p, l)
if (x == 1) {
  // outputkan jawaban yang benar
} else {
  // outputkan jawaban yang salah (contohnya, jangan outputkan apa-apa)
}
```

Maka, jika kita mendapatkan hasil `Accepted` pada suatu kasus uji, maka kita tahu bahwa nilai $x$ adalah 1.

Hal ini dilakukan berulang kali untuk nilai $x$ dari 1-20, dan juga untuk masing-masing nilai $p$ dan $l$. Kasus terburuknya, solusi ini membutuhkan 60 kali submisi pada soal BLT Seat Distancing. Ada cara yang lebih "tidak coba-coba" dari ini

## Cara 2: Perhatikan pesan output

Sebelum kita submit solusi kita, kita bisa mencoba-coba program kita dengan contoh masukan yang diberikan, dengan cara mengklik tombol `Run Code`. Apa yang terjadi jika kita tidak mengeluarkan apa-apa?

![]({{ '/assets/images/blt-seat-finder-2.jpg' | relative_url }})

Sekarang apa yang terjadi jika kita mengeluarkan suatu karakter yang lain? Misalnya kita submit kode berikut:

```
printf("X")
```

Maka hasilnya adalah:

![]({{ '/assets/images/blt-seat-finder-2.jpg' | relative_url }})

Jika kita coba submit kode tersebut, "Compiler Message" ini juga bisa kita dapatkan pada tiap test case. **Berarti, kita bisa mendapatkan informasi mengenai karakter yang kita tuliskan. Kita bisa menggunakan informasi ini untuk mendapatkan nilai test case.**

Caranya adalah petakan nilai $x$ dari angka 1 hingga 20 ke karakter `A` hingga `T`, dan outputkan karakter tersebut. Maka, jika misalnya *compiler message* mengeluarkan pesan:

```
Failure: expecting [*] at line 1 and col 1, got [R]
```

berarti kita tahu bahwa nilai $x$ adalah 18.

Berikut adalah contoh implementasinya di bahasa C++.

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

int main() {
  int x, p, l;
  cin >> x >> p >> l;

  // petakan nilai x dari 1-20 ke karakter A-T.
  // outputkan karakter tersebut.
  char c = 'A' + x - 1;
  cout << c;
}
{% endhighlight %}

Kita cukup perlu mengulang ini tiga kali untuk nilai $p$ dan $l$. Maka hanya dibutuhkan 3 submisi untuk mendapatkan semua nilai test case.

## Cara 3: Hanya perlu 1 submisi

Perhatikan bahwa pada compiler output, **tidak hanya ada informasi karakter yang salah, melainkan juga ada informasi `line` dan `col`. Kita dapat memanfaatkan semuanya untuk mendapatkan nilai $x$, $p$, dan $l$ sekaligus!**

Caranya adalah dengan memodifikasi solusi yang sudah Accepted pada BLT Seat Distancing dengan menghitung baris dan kolom saat ini. Jika kita sudah ada pada baris $p$ dan kolom $l$, maka kita outputkan karakter untuk mencari nilai $x$ seperti pada cara sebelumnya.

Maka jika kita mendapatkan hasil seperti di bawah ini:

![]({{ '/assets/images/blt-seat-finder-4.jpg' | relative_url }})

berarti kita tahu bahwa test case ke-6 adalah $x=11$, $p=17$, dan $l=9$.

Program untuk BLT Seat Distancing yang memakai cara ini dapat dilihat [di sini]({{ site.solution_file }}/blt-seat-finder/solution_blt-seat-distancing_1submission.cpp).
