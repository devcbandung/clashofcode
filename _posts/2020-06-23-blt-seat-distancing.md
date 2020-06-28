---
layout: post
title:  "BLT Seat Distancing"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Easy |
| **Kategori** | Ad Hoc |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/blt-seat-distancing) |
| **Pranala Solusi** | [Solusi 1]({{ site.solution_file }}/blt-seat-distancing/solution.cpp), [Solusi 2]({{ site.solution_file }}/blt-seat-distancing/solution2.cpp) |

Pada soal ini, kita cukup mencetak apa yang diminta soal dengan menggunakan perulangan sederhana.

Salah satu cara yang dapat memudahkan adalah dengan menyimpan dua buah variable string sepanjang $x$ yang berisi `*` dan ` ` (spasi). Dengan begitu, kita dapat menghilangkan satu level perulangan.


{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

int main() {
  int x, p, l;
  cin >> x >> p >> l;
  
  string seat = string(x, '*');  // '*' sebanyak x kali
  string space = string(x, ' '); // ' ' sebanyak x kali

  for (int i = 0; i < p; ++i) {
    for (int j = 0; j < x; ++j) {
      for (int k = 0; k < l; ++k) {
        // saat i+k genap, keluarkan '*'
        // saat i+k ganjil, keluarkan ' '
        if ((i+k) % 2 == 0) {
          cout << seat;
        } else {
          cout << space;
        }
      }
      cout << endl;
    }
  }
}
{% endhighlight %}

