---
layout: post
title:  "DevC Member Growth"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Easy |
| **Kategori** | Math, Ad Hoc |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/devc-member-growth) |
| **Pranala Solusi** | [Solusi 1 (Loop)]({{ site.solution_file }}/devc-member-growth/solution_loop.cpp), [Solusi 2 (Math)]({{ site.solution_file }}/devc-member-growth/solution_math.cpp), [Solusi 3 (Math 2)]({{ site.solution_file }}/devc-member-growth/solution_math2.cpp) |

Apa yang diminta pada soal ini cukup jelas, yaitu banyak hari sampai DevC X mencapai 10 ribu member, jika saat ini ada $N$ member dan tiap harinya banyak member akan bertambah sebanyak $D$. Ada dua cara untuk menghitung jumlah hari tersebut, yaitu dengan [menggunakan loop](#menggunakan-loop) atau dengan menggunakan sedikit [perhitungan matematika](#menggunakan-matematika).

## Menggunakan loop

Karena batasan yang cukup kecil, kita dapat melakukan perulangan hingga banyak member mencapai 10 ribu. Berikut adalah implementasinya dalam bahasa C++:

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

int main() {
  int n, d;
  cin >> n >> d;

  // lakukan perulangan sampai n >= 10000
  // banyaknya hari dinyatakan dalam variable days berikut
  int days = 0;
  while (n < 10000) {
    n += d; // tambahkan banyak member dengan d
    days++; // jangan lupa increment days
  }

  // outputkan jawaban
  cout << days << endl;
}
{% endhighlight %}

## Menggunakan Matematika

Banyaknya member yang ingin ditambah adalah sebanyak $10000-N$, dan tiap harinya banyak member akan bertambah sebanyak $D$. Maka, banyaknya hari untuk mencapai hal tersebut adalah $\frac{10000-N}{D}$. Perhatikan bahwa kita harus bulatkan nilai ini ke bilangan bulat yang lebih besar. Fungsi untuk membulatkan ke bilangan bulat yang lebih besar disebut juga dengan fungsi `ceil`.

Berikut adalah contoh implementasinya dalam bahasa C++:

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

int main() {
  int n, d;
  cin >> n >> d;

  // Perhatikan bahwa karena 10000-n dan d bertipe int,
  // kita harus melakukan casting ke float.
  // Begitu juga dengan hasil dari fungsi ceil yang
  // bertipe float harus kita cast kembali ke int.
  int days = (int)ceil((float)(10000-n)/(float)d);
  cout << days << endl;
}
{% endhighlight %}

**Tips: cara lain menghitung `ceil`**

Ada cara lain untuk menghitung nilai $ceil(A/B)$ jika $A$ dan $B$ keduanya adalah bilangan bulat positif, yaitu $ceil\left(\dfrac{A}{B}\right) = floor\left(\dfrac{A+B-1}{B}\right)$. Pembuktiannya diserahkan kepada pembaca.

Karena pembagian bilangan bulat pada sebagian besar bahasa pemrograman sudah dibulatkan ke bawah, maka kita dapat menyederhanakan perhitungan days di atas tanpa memanggil fungsi `ceil`:

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

int main() {
  int n, d;
  cin >> n >> d;

  int days = (10000-n + d-1) / d;
  cout << days << endl;
}
{% endhighlight %}
