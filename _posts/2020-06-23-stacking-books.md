---
layout: post
title:  "Stacking Books"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Medium |
| **Kategori** | Math |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/stacking-books) |
| **Pranala Solusi** | [Solusi]({{ site.solution_file }}/stacking-books/solution.cpp), [Solusi (Loop)]({{ site.solution_file }}/stacking-books/solution_loop.cpp) |

Walaupun memungkinkan untuk menangani semua kasus yang mungkin, tapi ada cara yang sangat sederhana yang dapat melingkupi semua kasus.

**Perhatikan persegi panjang minimal yang menutupi kedua buku. Keliling yang kita cari sama dengan keliling dari persegi panjang tersebut.**

![]({{ '/assets/images/stacking-books-1.jpg' | relative_url }})

Pembuktiannya cukup sederhana. Perhatikan bahwa bangun datar yang dibentuk dari kedua persegi panjang tersebut sama saja dengan persegi panjang yang menutupi kedua buku tersebut, yang di ujung-ujungnya (bisa beberapa) "dipotong". Tiap potongan ini berbentuk persegi panjang juga.

Perhatikan bahwa di tiap potongan, sisi bangun datar tersebut dapat "dipindahkan" ke sisi persegi panjang, tanpa mengubah total panjangnya. Jadi, keliling bangun datar tersebut sama dengan keliling persegi panjang yang besar.

Persoalan ini mirip dengan persoalan "menghitung panjang tangga" yang diilustrasikan sebagai berikut. Perhatikan bahwa total panjang anak tangga (yang berwarna biru) sama dengan total panjang segmen berwarna merah.

![]({{ '/assets/images/stacking-books-2.jpg' | relative_url }})

Terakhir, kita cukup mencari persegi panjang minimal tersebut. Perhatikan bahwa persegi panjang yang kita cari adalah persegi panjang dengan titik kiri bawah dan kanan atas:

\\[ (\min(x), \min(y)), (\max(x), \max(y)) \\]

di mana $\min(x)$ adalah minimum dari semua nilai $x$ pada masukan.

Berikut adalah contoh implementasinya dalam bahasa C++.

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

int main() {
  int minx, maxx, miny, maxy;
  int x, y;

  // baca titik pertama, assign menjadi semua nilai min/max
  cin >> x >> y;
  minx = maxx = x;
  miny = maxy = y;

  // baca 3 titik lainnya.
  // perhatikan bahwa kita tidak perlu memedulikan titik mana
  // termasuk ke persegi panjang yang mana.
  for (int i = 0; i < 3; i++) {
    cin >> x >> y;
    minx = min(minx, x);
    maxx = max(maxx, x);
    miny = min(miny, y);
    maxy = max(maxy, y);
  }

  // outputkan keliling dari persegi panjang besar
  cout << 2 * (maxx - minx + maxy - miny) << endl;
}
{% endhighlight %}
