---
layout: post
title:  "Clock Angle"
date:   2020-06-23 00:00:00 +0700
categories: editorial
---

| **Tingkat Kesulitan** | Medium |
| **Kategori** | Math |
| **Pranala Soal** | [Pranala Soal]({{ '/problem' | relative_url }}/clock-angle) |
| **Pranala Solusi** | [Solusi]({{ site.solution_file }}/clock-angle/solution.cpp) |

Perhatikan bahwa mungkin akan sulit jika kita harus langsung menghitung sudut antara kedua jarum jam, tapi **lebih mudah untuk menghitung sudut antara pukul 12 dan jarum jam/menit**.

Misalkan kita ingin menghitung sudut pada pukul 07:22.

![]({{ '/assets/images/clock-angle-1.jpg' | relative_url }})

Kita perlu menghitung sudut $m$ dan $h$. Sudut di antara keduanya adalah nilai absolut dari $h-m$.

## Menghitung $h$

Kita tahu bahwa sudut di pada satu lingkaran penuh adalah $360^\mathrm{o}$, berarti setiap jamnya, sudut $h$ akan bertambah sebesar $30^\mathrm{o}$. Berarti, tiap menitnya, sudut $h$ akan bertambah sebesar $\dfrac{30^\mathrm{o}}{60} = 0.5^\mathrm{o}$. Berarti, rumus untuk sudut $h$ adalah:

\\[h = HH \times 30 + MM \times 0.5\\]

di mana $HH:MM$ adalah jam pada masukan. Jangan lupa juga untuk mengurangi 12 dari $HH$ jika nilainya 12 atau lebih.

## Menghitung $m$

Sama seperti cara di atas, tiap 60 menit, jarum menit berputar satu lingkaran penuh atau $360^\mathrm{o}$. Berarti, tiap menitnya, jarum menit akan bertambah sebesar $6^\mathrm{o}$.

## Sudut antara kedua jarum

Menggabungkan keduanya, maka kita akan mendapatkan sudutnya:

\\[
\begin{align} angle & = \left\lvert h-m \right\rvert \\\\ & = \left\lvert HH \times 30 + MM \times 0.5 - MM \times 6 \right\rvert \\\\ & = \left\lvert HH \times 30 - MM \times 5.5\right\rvert \end{align}
\\]

## Perhatikan sudut > $180^\mathrm{o}$

Rumus di atas belum cukup, kita harus memastikan bahwa sudut yang dihasilkan kurang atau sama dengan 180 derajat. Cukup dengan memeriksa apakah nilai $angle$ lebih dari $180^\mathrm{o}$ atau tidak. Jika iya, maka jawaban yang diminta adalah $360 - angle$. Atau dengan kata lain:

\\[ans = \min(angle, 360-angle)\\]
