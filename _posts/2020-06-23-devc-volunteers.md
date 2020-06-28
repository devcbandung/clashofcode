---
layout: post
title:  "DevC Volunteers"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Advanced |
| **Kategori** | Dynamic Programming |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/devc-volunteers) |
| **Pranala Solusi** | [Solusi (DP $O(MN^2)$)]({{ site.solution_file }}/devc-volunteers/solution_dp_nm2.cpp), [Solusi DP $O(N + M \log M)$]({{ site.solution_file }}/devc-volunteers/solution.cpp) |

Sebelum menyelesaikan soal ini, salah satu observasi yang penting adalah **kita tidak perlu meng-*assign* lebih dari satu volunteer untuk setiap meetup.**

Kita dapat menyelesaikan soal ini dengan menggunakan [dynamic programming (DP)](https://en.wikipedia.org/wiki/Dynamic_programming).

## Solusi untuk $1 \le N,M \le 500$

Misalkan $dp[i][j]$ menyatakan banyaknya meetup paling banyak sampai $i$ hari pertama, jika pada hari ke-$i$, volunteer ke-$j$ yang di-*assign*. $dp[i][0]$ akan menyatakan banyak meetup paling banyak sampai $i$ hari pertama jika tidak ada meetup pada hari ke-$i$.

Maka, formula untuk transisi DP-nya adalah sebagai berikut:

- $dp[i][j] = 0$, jika $j > 0$ dan $i < A_j$ atau $i > B_j$,
- $dp[i][j] = 1 + \max_{j \ne k}(dp[i-1][k]), k = 0 \dots M$, jika $j > 0$ dan $A_j \le i \le B_j$,
- $dp[i][j] = \max(dp[i-1][k]), k = 0 \dots M$, jika $j = 0$.

Jawaban yang diminta adalah $\max(dp[N][j]), j = 0 \dots M$.

*Assignment* volunteer dapat dilakukan dengan cara *backtracking*.

Kompleksitas waktu dan memori untuk cara ini adalah $O(NM^2)$.

## Solusi untuk $1 \le N, M \le 100000$

Tentu cara di atas tidak dapat langsung kita gunakan untuk batasan $N$ dan $M$ hingga 100 ribu. Namun, kita dapat mengembangkan solusi di atas dengan tambahan sebuah observasi.

Misalkan di hari ke-$k$, hanya ada satu volunteer yang kosong. Kita tidak bisa langsung yakin bahwa jawaban yang optimal adalah dengan meng-*assign* volunteer tersebut di hari ke-$k$, karena bisa saja jawaban yang optimal adalah satu volunteer tersebut di-*assign* di hari sesudahnya atau sebelumnya.

Begitu pula saat ada dua volunteer yang kosong, karena bisa saja jawaban yang optimal adalah dengan meng-*assign* satu volunteer di hari sebelumnya dan volunteer yang kedua di hari yang sesudahnya.

Tapi, **saat ada paling tidak tiga volunteer yang kosong pada hari ke-$k$, kita pasti bisa mengadakan meetup di hari tersebut.** Mengapa? Karena siapapun yang di-*assign* di hari sebelumnya dan di hari sesudahnya, *pasti* ada paling tidak satu volunteer yang tersisa di hari tersebut.

Maka, kita dapat mengembangkan solusi DP di atas sebagai berikut. Misalkan $V[k]$ adalah himpunan semua volunteer yang kosong di hari ke-$k$, dan $\left\lvert V[k] \right\rvert$ menyatakan banyaknya volunteer yang kosong di hari ke-$k$.

- Jika $\left\lvert V[k] \right\rvert \ge 3$, maka sebut $dp[k][1]$ adalah banyaknya meetup maksimal sampai hari ke-$k$ tanpa peduli volunteer mana yang akan di-*assign*. Karena argumen di atas, maka kita tahu bahwa kita selalu dapat mengadakan meetup di hari ke-$k$ ini. Volunteer yang akan di-*assign* dapat kita cari belakangan.
  - $dp[k][1] = 1 + \max(dp[k-1][j])$.
- Jika $\left\lvert V[k] \right\rvert \le 2$, maka kita simpan indeks volunteer-volunteer yang available di hari ini, dan nilai $dp[k][j]$ adalah saat kita meng-*assign* volunteer ke-$j$ pada $V[k]$. Sama seperti di atas, $dp[k][0]$ menyatakan saat pada hari ke-$k$ tidak ada volunteer yang kosong.
  - $dp[k][j] = 1 + dp[k-1][1]$, jika $\left\lvert V[k-1] \right\rvert \ge 3$.
  - $dp[k][j] = 1 + dp[k-1][0]$, jika $\left\lvert V[k-1] \right\rvert = 0$.
  - $dp[k][j] = 1 + \max(dp[k-1][i]), V[k-1][i] \ne V[k][j]$, jika $1 \le \left\lvert V[k-1] \right\rvert \le 2$.

Kompleksitas DP di atas menjadi $O(N)$.

Sekarang, untuk *assignment* volunteer, pertama-tama *assign* semua volunter pada hari-hari di mana $\left\lvert V[k] \right\rvert \le 2$. Setelah semua volunteer di-*assign*, maka lakukan iterasi kedua untuk meng-*assign* volunteer-volunteer di mana $\left\lvert V[k] \right\rvert \ge 3$. Menurut argumen di atas, kita pasti dapat mencari paling tidak satu volunteer di hari tersebut.

**Catatan: cara menentukan $V$**

Solusi di atas membutuhkan kita untuk tahu semua volunteer yang kosong pada tiap-tiap hari dari 1 hingga $N$. Salah satu caranya adalah sebagai berikut.

Kita buat list `add` dan `remove` yang menyatakan volunteer yang perlu ditambah dan dikurangi di hari tersebut. Kita dapat mengisi keduanya dengan cara berikut ini:

```
for (i = 1 to M) {
  add[A[i]].push(i)
  remove[B[i]].push(i)
}
```

Setelah kita mengisi kedua list ini, maka kita dapat me-*maintain* sebuah set `V` yang berisi volunteer yang sedang available saat ini.

```
V = set<int>
for (day = 1 to N) {
  // tambah volunteer yang kosong mulai hari ini
  for (v in add[day]) {
    V.insert(v)
  }

  ... proses DP

  // hapus volunteer yang hari ini adalah hari kosong terakhirnya
  for (v in remove[day]) {
    V.remove(v)
  }
}
```

Kompleksitasnya adalah $O(M \log M)$, karena untuk setiap volunteer, ada tepat satu operasi `insert` dan satu operasi `remove` pada `V` (dengan asumsi operasi `insert` dan `remove` memiliki kompleksitas $O(\log M)$).
