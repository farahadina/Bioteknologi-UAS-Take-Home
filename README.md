# Bioteknologi-UAS-Take-Home

Berikut README yang bisa kamu taruh di repository/folder tugas **Q2C – Kinetic Modeling Simulation with Feedback Inhibition**.

# README.md

## Q2C – Dynamic Simulation of a Metabolic Pathway Using ODEs

### Overview

Proyek ini mensimulasikan dinamika suatu jalur metabolik sederhana menggunakan **Ordinary Differential Equations (ODEs)**. Model menggambarkan konversi substrat menjadi produk melalui beberapa metabolit antara serta mempertimbangkan mekanisme **feedback inhibition non-competitive** oleh produk akhir.

Jalur metabolik yang dimodelkan:

```
X → A → B → P
     ↓
  Byproduct
```

Reaksi:

* v1: X → A
* v2: A → B
* v3: B → P
* v4: A → Byproduct

---

## Objective

Tujuan simulasi adalah:

1. Memodelkan perubahan konsentrasi metabolit A, B, dan P terhadap waktu.
2. Mengamati efek akumulasi produk akhir (P) terhadap laju pembentukan A.
3. Memahami perilaku regulasi diri (*self-regulating behavior*) pada sistem metabolik.

---

## Mathematical Model

### Reaction Rates

#### v1 (Non-competitive Feedback Inhibition)

[
v_1=\frac{V_{1,max}[X]}{(K_{m1}+[X])\left(1+\frac{[P]}{K_i}\right)}
]

#### v2

[
v_2=k_2[A]
]

#### v3

[
v_3=k_3[B]
]

#### v4

[
v_4=k_4[A]
]

---

## Differential Equations

[
\frac{d[A]}{dt}=v_1-v_2-v_4
]

[
\frac{d[B]}{dt}=v_2-v_3
]

[
\frac{d[P]}{dt}=v_3
]

---

## Parameters

| Parameter | Value |
| --------- | ----- |
| V1max     | 5.0   |
| Km1       | 2.0   |
| Ki        | 3.0   |
| X         | 10.0  |
| k2        | 1.0   |
| k3        | 0.8   |
| k4        | 0.3   |

---

## Initial Conditions

Pada awal simulasi:

| Metabolite | Initial Concentration |
| ---------- | --------------------- |
| A          | 0                     |
| B          | 0                     |
| P          | 0                     |

Rentang simulasi:

* Start time = 0 jam
* End time = 48 jam

---

## Software Requirements

Python 3.x

Library yang digunakan:

```bash
numpy
scipy
matplotlib
```

Instalasi:

```bash
pip install numpy scipy matplotlib
```

---

## Running the Simulation

Jalankan script:

```bash
python q2c_simulation.py
```

Output yang dihasilkan:

* Grafik konsentrasi A, B, dan P terhadap waktu
* File gambar:

```bash
simulation_plot.png
```

---

## Expected Results

Hasil simulasi menunjukkan bahwa:

1. Konsentrasi A meningkat lebih dahulu karena dibentuk langsung dari substrat X.
2. Konsentrasi B meningkat setelah A mulai terakumulasi.
3. Produk akhir P terus bertambah selama simulasi.
4. Akumulasi P menyebabkan penurunan laju v1 melalui mekanisme feedback inhibition.
5. Sistem menunjukkan perilaku self-limiting, yaitu produksi produk akhir secara bertahap menghambat pembentukan metabolit awal.

---

## Biological Interpretation

Model ini menggambarkan mekanisme regulasi yang umum ditemukan pada sistem biologis, di mana produk akhir suatu jalur metabolik menghambat langkah awal jalur tersebut untuk mencegah produksi berlebihan dan menjaga homeostasis sel.

---
