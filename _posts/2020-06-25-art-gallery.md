---
layout: post
title:  "Art Gallery"
date:   2020-06-25 00:00:00 +0700
meta:   "Tingkat Kesulitan: Expert (180 Poin)"
categories: problem
---

### Deskripsi

DevC (De Vinci) Art Gallery adalah sebuah galeri lukisan yang terkenal. Jika dilihat dari atas, galeri DevC berbentuk poligon konveks dengan $N$ sisi, di mana verteks ke-$i$ ada di titik $(Gx_i, Gy_i)$ pada koordinat kartesian.

Sekarang di DevC Art Gallery sedang ada ekshibisi lukisan kontemporer, di mana terdapat $M$ lukisan yang sedang ditampilkan. Namun, tentu saja lukisan-lukisan ini tidak diletakkan di dinding galeri tersebut, karena penempatan seperti itu dinilai kurang artistik. Melainkan, ke-$M$ lukisan tersebut didirikan disebar di segala penjuru galeri. Lebih jelasnya, jika dilihat dari atas, lukisan ke-$i$ dapat dianggap sebagai sebuah segmen garis dengan koordinat $(Lax_i, Lay_i)$ dan $(Lbx_i, Lby_i)$.

Sebagai contoh, berikut adalah ilustrasi DevC Art Gallery dengan:

- $(Gx_i, Gy_i)$ = $(-3, -3), (3, -3), (3, 3), (3, -3)$.
- 4 lukisan: $((Lax_i, Lay_i), (Lbx_i, Lby_i))$ = $((-2, -1), (-2, 2))$, $((-1, 0), (0, -2))$, $((1, 0), (2, -2))$, $((2, 0), (2, 2))$.

![image](https://s3.amazonaws.com/hr-assets/0/1592392814-dd9dbfe8aa-WhatsAppImage2020-06-17at18.19.25.jpeg)

Ada satu kekurangan dari DevC Art Gallery: pencahayaan. Hanya ada satu sumber cahaya di galeri tersebut, yaitu sebuah lampu pada koordinat $(0, 0)$. Tentunya, ada bagian-bagian dari galeri tersebut yang tidak terkena cahaya dengan baik (pada soal ini, diasumsikan dinding dan lukisan adalah benda hitam sempurna yang tidak memantulkan cahaya). Lukisan yang ada di tengah-tengah galeri akan bertindak seperti halnya dinding yang menghalangi sumber cahaya tersebut.

Berikut adalah ilustrasi galeri di atas setelah ditambahkan pencahayaan.

![image](https://s3.amazonaws.com/hr-assets/0/1592392824-b08c730510-WhatsAppImage2020-06-17at18.18.48.jpeg)

Pada soal ini, Anda diminta untuk menghitung area galeri yang terkena cahaya!


### Format Masukan

Baris pertama berisi dua buah bilangan bulat $N$ dan $M$, yang menyatakan banyak sisi poligon gedung galeri dan banyaknya lukisan.

$N$ baris berikutnya masing-masing berisi 2 buah bilangan bulat $Gx_i, Gy_i$ yang menyatakan verteks-verteks poligon yang membentuk gedung galeri. Verteks-verteks ini akan diberikan dengan urutan berlawanan arah jarum jam atau *counter-clockwise*.

$M$ baris berikutnya masing-masing berisi 4 buah bilangan bulat $Lax_i, Lay_i, Lbx_i, Lby_i$ yang menyatakan kedua titik ujung segmen yang membentuk lukisan ke-$i$.


### Batasan

**Untuk 10% kasus:**

- $M = 0$. Hint: dengan kata lain, kalian diminta menghitung luas galeri.

**Untuk 30% kasus:**

- Poligon berukuran persegi dengan $(0, 0)$ sebagai pusatnya.
  - Dengan kata lain, $N = 4$, dan $(Gx_i, Gy_i) = (-K, -K), (K, -K), (K, K), (-K, K)$ untuk suatu bilangan bulat $K$.
- Semua lukisan sejajar dengan sumbu $x$, atau $Lay_i = Lby_i$ untuk $i = 1 \dots M$.
- Semua lukisan ada di dalam segitiga yang dibentuk oleh $(0, 0)$, $(-K, K)$, $(K, K)$.
  - Dengan kata lain, dinding galeri di sebelah kiri, bawah, dan kanan seluruhnya terkena cahaya.

**Untuk 100% kasus:**

- $3 \le N \le 5000$.

Untuk semua kasus:

- $0 \le M \le 5000$.
- Untuk semua titik $(x, y)$ pada masukan: $-10000 \le x, y \le 10000$.
- Poligon galeri (sebut dengan $G$) adalah [poligon konveks](https://en.wikipedia.org/wiki/Convex_polygon).
- Titik $(0, 0)$ berada di dalam $G$. “Di dalam” berarti titik ini tidak berada pada sisi-sisi poligon.
- Semua segmen lukisan berada di dalam $G$.
- Tidak ada dua segmen lukisan yang beririsan, termasuk pada kedua ujungnya.
  - Secara tidak langsung, ini juga berarti semua titik pada masukan berbeda-beda.
- Tidak ada segmen lukisan yang melewati titik $(0, 0)$, termasuk pada kedua ujungnya.


### Format Keluaran

Keluarkan sebuah bilangan real yang berisi luas daerah yang terkena cahaya.

Jawaban akan diperiksa dengan *relative error* sebesar $10^{-6}$. Secara formal, jika jawaban kalian adalah $ans_{contestant}$ dan jawaban juri adalah $ans_{judge}$, maka jawaban kalian dianggap benar jika:

\\[
  \left\lvert\dfrac{ans_{contestant} - ans_{judge}}{ans_{judge}}\right\rvert < 10^{-6}
\\]


#### Contoh Masukan 0

```
4 4
-3 -3
3 -3
3 3
-3 3
-2 -1 -2 2
-1 0 0 -2
2 0 2 2
1 0 2 -2
```


#### Contoh Keluaran 0

```
19.5
```

#### Contoh Masukan 1

```
8 9
-6 3
-7 -2
-1 -5
10 -6
11 2
10 4
3 6
-5 5
-4 2 -2 3
-4 4 2 4
1 1 1 3
5 3 8 0
5 1 4 -1
-3 1 -1 -2
-5 -1 -3 -2
1 -4 5 -2
2 -1 2 -2
```

#### Contoh Keluaran 1

```
62.808275303403775
```

#### Penjelasan 1

Berikut adalah ilustrasi pada Sample 1.

![image](https://s3.amazonaws.com/hr-assets/0/1592393082-05d6b9fcbe-WhatsAppImage2020-06-17at18.19.48.jpeg)

Kedua contoh di atas dapat dilihat secara interaktif via Geogebra melalui pranala berikut: [https://www.geogebra.org/m/gx4rw8hh](https://www.geogebra.org/m/gx4rw8hh).
