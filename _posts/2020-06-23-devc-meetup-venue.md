---
layout: post
title:  "DevC Meetup Venue"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Hard |
| **Kategori** | Graph, DFS/BFS |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/devc-meetup-venue) |
| **Pranala Solusi** | [Solusi DFS]({{ site.solution_file }}/devc-meetup-venue/solution_dfs.cpp), [Solusi BFS]({{ site.solution_file }}/devc-meetup-venue/solution.cpp) |

Ada dua permasalahan yang harus diselesaikan di soal ini:
1. Apakah terdapat jalan yang valid antara point A (Acep) dan point B (Venue)?
2. Bila iya, rute apa yang harus Acep ambil?

Ada dua cara untuk menyelesaikan soal semacam ini, yaitu dengan menggunakan DFS atau BFS.

## Depth First Search (DFS)

[Depth First Search (DFS)](https://en.wikipedia.org/wiki/Depth-first_search) adalah algoritma yang digunakan untuk menelusuri sebuah graph dari sebuah titik awal. Dari sebuah titik awal, algoritma ini akan memilih sebuah langkah dan mencoba menelusuri graph sejauh mungkin sebelum "kembali" dan mencoba langkah lain. Karena kita tidak peduli apakah langkah yang diambil adalah langkah terpendek atau bukan, kita dapat menggunakan DFS untuk mencari rute dari Acep ke Venue.

Untuk menyelesaikan permasalahan (1), solusi DFS yang perlu dibuat cukup sederhana. 

{% highlight cpp %}

int n, target_r, target_c;
string maze[MAXN];
int visited[MAXN][MAXN];
string final_path;

bool dfs(int r, int c) {
  // Cek apakah koordinat sekarang melewati batas
  if (r < 0 || r >= n || c < 0 || c >= n) return false;

  // Jangan lupa cek apakah koordinat sekarang tembok atau bukan
  if (maze[r][c] == '#') return false;

  // Kalau koordinat ini sudah dikunjungi sebelumnya,
  // kita bisa mengabaikannya
  if (visited[r][c]) return false;

  visited[r][c] = true;

  // Jika koordinat ini sudah sama dengan target, return true
  if (r == target_r && c == target_c) return true;

  // Selain itu, kita cari secara rekursif ke empat arah
  return dfs(r, c+1) || dfs(r+1, c) ||
    dfs(r, c-1) || dfs(r-1, c);
}
{% endhighlight %}

Tetapi kode itu tidak cukup untuk menyelesaikan soal ini. Bagaimana cara untuk mengetahui rute yg diambil dari kode diatas? Salah satu caranya yaitu dengan menyimpan rute sebagai argument.

{% highlight cpp %}

int n, target_r, target_c;
string maze[MAXN];
int visited[MAXN][MAXN];
string final_path;

// Pada awalnya, path akan sama dengan string kosong
bool dfs(int r, int c, string path) {
  // Cek apakah koordinat sekarang melewati batas
  if (r < 0 || r >= n || c < 0 || c >= n) return false;

  // Jangan lupa cek apakah koordinat sekarang tembok atau bukan
  if (maze[r][c] == '#') return false;

  // Kalau koordinat ini sudah dikunjungi sebelumnya,
  // kita bisa mengabaikannya
  if (visited[r][c]) return false;

  visited[r][c] = true;

  // Jika koordinat ini sudah sama dengan target, return true
  if (r == target_r && c == target_c) return true;

  // Selain itu, kita cari secara rekursif ke empat arah.
  // Jangan lupa menambahkan arah yang kita tuju ke path.
  return dfs(r, c+1, path+"R") || dfs(r+1, c, path+"D") ||
    dfs(r, c-1), path+"L" || dfs(r-1, c, path+"U");
}

{% endhighlight %}

Solusi di atas akan mendapatkan verdict Accepted. Namun, kita dapat mengoptimasi algoritma tersebut supaya tidak terus menerus meng-*copy* path pada setiap pemanggilan fungsi `dfs`. Cara di atas dapat memakan memori yang lebih dari yang seharusnya.

Kita dapat menggunakan sebuah variable global untuk menyimpan path yang kita cari seperti berikut.

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

#define MAXN 110

int n, target_r, target_c;
string maze[MAXN];
int visited[MAXN][MAXN];
string final_path;

bool dfs(int r, int c) {
  // Cek apakah koordinat sekarang melewati batas
  if (r < 0 || r >= n || c < 0 || c >= n) return false;

  // Jangan lupa cek apakah koordinat sekarang tembok atau bukan
  if (maze[r][c] == '#') return false;

  // Kalau koordinat ini sudah dikunjungi sebelumnya,
  // kita bisa mengabaikannya
  if (visited[r][c]) return false;

  visited[r][c] = true;

  // Jika koordinat ini sudah sama dengan target, return true
  if (r == target_r && c == target_c) return true;

  // Selain itu, kita cari secara rekursif ke empat arah.
  // Jika kita menemukan satu arah yang return true (atau dengan kata
  // lain, target dapat tercapai), maka kita ubah final_path dan
  // pastikan kita tidak mencari ke arah lainnya.
  if (dfs(r, c+1)) {
    final_path = "R" + final_path;
    return true;
  } 
  if (dfs(r+1, c)) {
    final_path = "D" + final_path;
    return true;
  }
  if (dfs(r-1, c)) {
    final_path = "U" + final_path;
    return true;
  }
  if (dfs(r, c-1)) {
    final_path = "L" + final_path;
    return true;
  }
  return false;
}

int main() {
  int r, c;
  cin >> n;
  cin >> r >> c >> target_r >> target_c;
  for (int i=0; i<n; i++) {
    cin >> maze[i];
  }
  r--; c--; target_r--; target_c--;
  bool found = dfs(r, c);
  if (found) {
    cout << final_path << endl;
  } else {
    cout << "tersesat" << endl;
  }
  return 0;
}
{% endhighlight %}

Kompleksitas waktu dan memori dari kode di atas adalah setara dengan jumlah *node* pada graf, karena tiap *node* hanya dikunjungi sekali. Dalam hal ini, kompleksitasnya adalah $O(N^2)$.

## Breadth First Search (BFS)

Solusi BFS diserahkan kepada pembaca sebagai latihan.
