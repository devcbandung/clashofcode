---
layout: post
title:  "Insensitive Palindrome"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Easy |
| **Kategori** | String |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/insensitive-palindrome) |
| **Pranala Solusi** | [Solusi]({{ site.solution_file }}/insensitive-palindrome/solution.cpp), [Solusi (Python)]({{ site.solution_file }}/insensitive-palindrome/solution.py) |

## Cara menentukan sebuah string palindrom atau bukan

Palindrom adalah salah satu persoalan yang sangat umum di pemrograman. Pengecekan suatu string palindrom atau bukan dapat diperiksa dengan melakukan looping secara simultan dari kiri dan kanan. Berikut adalah contoh implementasinya dalam bahasa C++:

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

int main() {
  string s;
  cin >> s;

  int n = s.length();
  bool isPalindrome = true;

  // iterasi dari kiri dan kanan secara simultan.
  // pada tiap iterasi, increment indeks di kiri dan decrement indeks di kanan.
  for (int l = 0, r = n-1; l < r; l++, r--) {
    if (s[l] != s[r]) {
      isPalindrome = false;
      break;
    }
  }

  // lakukan sesuatu dengan isPalindrome
}
{% endhighlight %}

## Solusi Insensitive Palindrome

Kita dapat memodifikasi program di atas untuk soal ini dengan menambahkan satu boolean `isSensitive` yang menyatakan apakah palindrome saat ini masih *case-sensitive* atau tidak.

Kita perlu mengubah huruf menjadi case yang sama saat membandingkan *insensitive palindrome*. Fungsi mengubah case ini ada di sebagian besar bahasa, sebagai contoh `tolower` dan `toupper` pada bahasa C/C++. Namun, kita akan mengimplementasikan fungsi tersebut sendiri di bawah.

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

// Program kita akan tetap benar jika kita menggunakan toLowerCase
char toUpperCase(char c) {
  // Jika c sudah upper-case, maka tidak perlu ubah apa-apa
  if ('A' <= c && c <= 'Z') {
    return c;
  }
  // Jika c bukan upper-case, maka asumsikan c adalah lower-case.
  // Kita dapat mengubah c menjadi upper-case dengan perhitungan sederhana.
  // c - 'a' menyatakan huruf ke berapa c, jika 'a' dihitung 0 dan 'z' dihitung 25.
  // maka, menambahkan nilai ini dengan 'A' akan menghasilkan huruf yang sama tapi dalam case yang berbeda.
  return c - 'a' + 'A';
}

int main() {
  string s;
  cin >> s;

  int n = s.length();
  bool isPalindrome = true;
  bool isSensitive = true;

  // iterasi dari kiri dan kanan secara simultan.
  // pada tiap iterasi, increment indeks di kiri dan decrement indeks di kanan.
  for (int l = 0, r = n-1; l < r; l++, r--) {
    // pertama-tama, bandingkan secara case-insenstive.
    if (toUpperCase(s[l]) != toUpperCase(s[r])) {
      isPalindrome = false;
      isSensitive = false;
      break;
    }
    // kemudian, baru bandingkan secara case-sensitive.
    if (s[l] != s[r]) {
      isSensitive = false;
      break;
    }
  }

  if (isPalindrome && isSensitive) {
    cout << "sensitive palindrome" << endl;
  } else if (isPalindrome) {
    cout << "insensitive palindrome" << endl;
  } else {
    cout << "not a palindrome" << endl;
  }
}
{% endhighlight %}

## Solusi alternatif: reverse string

Cara alternatif untuk mengecek palindrome atau bukan adalah dengan membandingkan apakah string tersebut masih sama setelah dibalik. Berikut adalah contoh implementasinya dengan menggunakan Python:

{% highlight python %}
s = input()
r = s[::-1] # reverse s

if (s == r):
  print('sensitive palindrome')
elif (s.lower() == r.lower()):
  print('insensitive palindrome')
else:
  print('not a palindrome')
{% endhighlight %}
