---
layout: post
title:  "DevC Online Meetup"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Easy |
| **Kategori** | Ad Hoc |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/devc-online-meetup) |
| **Pranala Solusi** | [Solusi]({{ site.solution_file }}/devc-online-meetup/solution.cpp) |

Solusi soal ini cukup sederhana, yaitu kita diminta mencari **nilai maksimal viewer**. Kita dapat mencarinya dengan menyimpan banyak viewer saat ini, dan terus membandingkannya dengan nilai maksimal pada setiap notifikasi.

Berikut adalah contoh implementasinya dalam bahasa C++.

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

int main() {
  int viewers = 0, maxViewers = 0;
  int n, x;
  cin >> n;

  // untuk tiap notifikasi, update nilai viewers,
  // dan update maxViewers jika viewers > maxViewers
  for (int i = 0; i < n; i++) {
    cin >> x;
    viewers += x;
    if (viewers > maxViewers) {
      maxViewers = viewers;
    }
  }
  cout << maxViewers << endl;
}
{% endhighlight %}


