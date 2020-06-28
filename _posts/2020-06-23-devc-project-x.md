---
layout: post
title:  "DevC Project X"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Medium |
| **Kategori** | Graph |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/devc-project-x) |
| **Pranala Solusi** | [Solusi]({{ site.solution_file }}/devc-project-x/solution.cpp), [Solusi (Javascript)]({{ site.solution_file }}//devc-project-x/solution.js) |

Kita bisa melihat soal ini sebagai persoalan *graph*. Karyawan dapat dianggap sebagai sebuah *node* dan hubungan antara karyawan dengan atasan dapat dianggap sebagai *vertex*. Untuk mencari tahu seluruh atasan seorang karyawan, kita cukup menelusuri *graph* tersebut dari *node* awal. 

Bila jumlah karyawan yang terlibat langsung hanya satu, soal ini menjadi sangat sederhana. Kita cukup menghitung jumlah atasan yang dimiliki dari karyawan tersebut.

{% highlight cpp %}
while (employee != 0) {
  employee = report_to[employee];
  count_employee_x++;
}
{% endhighlight %}

Tetapi karena karyawan yang terlibat langsung bisa lebih satu, kita perlu mengatasi kasus dimana beberapa karyawan dapat memiliki atasan yang sama. Hal ini dapat diatasi dengan menggunakan sebuah *array* untuk menghindari *double counting*.

{% highlight cpp %}
while (employee != 0 && !is_counted[employee]) {
  employee = report_to[employee];
  count_employee_x++;
  is_counted[employee] = true;
}
{% endhighlight %}


Setelah mengetahui hal tersebut, implementasi dari persoalan ini menjadi cukup sederhana - Kita cukup mengeksekusi logika diatas untuk setiap karyawan ki.

Berikut adalah contoh implementasinya dalam bahasa C++.


{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

#define MAXN 100100

int n, k;
int report_to[MAXN];
bool is_counted[MAXN];
int count_employee_x = 0;

int main() {
  cin >> n >> k;
  for (int i = 1; i <= n; ++i) {
    cin >> report_to[i];
  }
  for (int i = 0; i < k; ++i) {
    int employee;
    cin << employee;
    while (employee != 0 && !is_counted[x]) {
      count_employee_x++;
      is_counted[x] = true;
      employee = report_to[x];
    }
  }
  count << count_employee_x << endl;
}
{% endhighlight %}

## Solusi alternatif: BFS.

Karena pola penelusuran graph yang kita gunakan tidak ada pengaruhnya terhadap soal ini, kita juga dapat menyelesaikannya dengan menelusuri graph menggunakan BFS. Idenya tetap sama yaitu dengan menggunakan array untuk menghindari *double counting*. 

Karyawan yang terlibat langsung dapat dijadikan *node* awal yang dimasukkan ke sebuah *queue* untuk ditelusuri.

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

#define MAXN 100100

int n, k;
int report_to[MAXN];
bool is_counted[MAXN];
int count_employee_x = 0;
queue<int> q;

int main() {
    cin >> n >> k;
    for (int i=0; i<n; i++) {
        cin >> report_to[i+1];
    }
    for (int i=0; i<k; i++) {
        int employee;
        cin >> employee;
        q.push(employee);
    }
    while (!q.empty()) {
        int front = q.front();
        q.pop();
        if (is_counted[front]) {
            continue;
        }
        count_employee_x++;
        is_counted[front] = true;
        if (front == 1) {
            continue;
        }
        q.push(report_to[front]);
    }
    cout << count_employee_x << endl;
    return 0;
}
{% endhighlight %}
