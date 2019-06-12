---
layout: post
title:  "Penguat Instrumentasi"
date:   2018-12-2T16:52:00+07:00
author: anggoro_dwi
categories: articles
tags: [Instrumentasi, Elektronika]
comments: true
share: true
mathjax: true
---

Dalam bidang sensor, salah satu permasalahannya adalah nilai yang mempresentasikan
dari pengukuran besaran fisik memiliki karakteristik tersendiri. Representasi 
nilai tersebut dapat berupa arus atau tegangan. Permasalahan tersebut, lebih khusus
pada skala nilai yang kecil dan gangguan dari luar maupun dari rangkaian penguat
itu sendiri. Skala nilai yang kecil dapat diselesaikan dengan mengatur gain dari
penguat, sedangkan pada gangguan membutuhkan trik khusus yang sesuai agar representasi
nilai dapat memiliki makna yang berarti. Khasus yang sering terjadi pada bidang sensor
adalah ketika sensor bersifat sebagai sumber arus atau tegangan. Akan terjadi pembebanan
pada sensor apabila rangkian penguat tidak memiliki impedansi yang besar. Padahal yang
dibutuhkan oleh penguat adalah informasi dari sensor saja, tetapi informasi 
tersebut terlalu membebani sensor. Pada artikel kali ini akan dijelaskan tentang
proses bagaimana permasalah tersebut diselsaikan menggunakan 
**penguat instrumentasi**. 
{: .text-justify}

Untuk membahas permasalah tersebut akan dibagi menjadi beberapa subbab, yaitu 
1) [Informasi yang dibutuhkan](#bab1); 
2) [Rekonstruksi ulang permasalahan](#bab2); 
3) [Pembahasan Penguat Instrumentasi](#bab3); 
4) [Kesimpulan](#bab4). 

# Informasi Yang Dibutuhkan <a name="bab1"></a>

## Penguat Differensial

[![differential opamp](/images/instrumentasi/opamp_differential.png)](http://tinyurl.com/y54l9qkk)

Untuk menganalisis output tegangan pada penguat differensial pembahasan dibagi
menjadi 3 bagian, yaitu analisis pada titik $$V_a$$, analisis pada titik
$$V_b$$ dan gabungan dari keduanya.

**Analisis Pada titik $$V_a$$**

Seperti yang telah diketahui bahwa input op-amp memiliki impedansi yang besar
, sehingga tidak ada arus yang masuk kedalam pin input negativ dan positif
pada op-amp, sehingga arus yang mengalir pada $$I_1 = I_f$$. Dengan
memanfaatkan persamaan tersebut, dilakukan analisa secara matematis sebagai
berikut

$$ \begin{eqnarray*}
  I_1 &=& I_f\\
  \frac{V_1 - V_a}{R_1} &=& \frac{V_a - V_{out}}{R_3} \\
  \frac{R_3}{R_1} (V_1 - v_a) &=& V_a - V_{out} \\
  \frac{R_3}{R_1} V_1 -  \frac{R_3}{R_1} V_a - V_a &=& -V_{out} \\
\end{eqnarray*}
$$

dengan menulis ulang hasil persamaan tersebut, diperoleh hasil akhir analisis
pada titik $$V_a$$ sebagai berikut

\begin{equation} \label{eq:6}
  V_{out} = V_a (1 + \frac{R_3}{R_1}) - \frac{R_3}{R_1} V_1 
\end{equation}

**Analisis Pada Titik $$V_b$$**

Sama dengan Analisis pada titik $$ V_a $$ Maka arus yang mengalir pada $$I_2 = I_4$$.
 Dengan memanfaatkan persamaan tersebut, dapat diselesaikan dengan 

$$\begin{eqnarray*}
  I_2 &=& I_4 \\
  \frac{V_2 - V_b}{R_2} &=& \frac{V_b - 0 (\text{Ground})}{R_4} \label{eq:7}\\
  \frac{R_2}{R_4} (V_2 - V_b) &=& V_b \\
  \frac{R_2}{R_4} V_2 &=&  \frac{R_2}{R_4} V_b + V_b \\
  \frac{R_2}{R_4} V_2 &=& V_b (\frac{R_2}{R_4} + 1) \\
  V_b (R_2 + R_4) &=& R_4 V_2 \\
\end{eqnarray*}
$$

Sedangkan beda potensian diantara pin input op-amp memiliki besaran yang sama, 
maka besar tegangan $$V_a = V_b$$. Dengan itu diperoleh hasil akhir persamaan
analisis pada titik $$V_b$$ 

\begin{equation} \label{eq:12}
  V_b = V_a = \frac{R_4}{R_2 + R_4} V_2 
\end{equation}
  
**Analisis Hubungan $$ V_a $$ dan $$V_b$$**

Dengan persamaan \eqref{eq:12} kedalam persamaan \eqref{eq:6}, dengan asumsi
bahwa $$R_1 = R_2 = R$$ dan $$R_3 = R_4 = Ra$$. 

$$\begin{eqnarray*}
  V_{out} &=&  ( \frac{Ra}{R + Ra} ) (1 + \frac{Ra}{R}) V_2 - \frac{Ra}{R} V_1 \\
  V_{out} &=&  \frac{Ra(R+Ra)}{R (R + Ra)} V_2 - \frac{Ra}{R} V_1\\
\end{eqnarray*}
$$

\begin{equation}
  V_{out} = \frac{Ra}{R} (V_2 - V_1)\label{eq:15}
\end{equation}

# Rekonstruksi Ulang Permasalahan <a name="bab2"></a>

Sebagai contoh, apabila sebuah sensor yang memiliki sifat menghasilkan sumber energi, 
dimana sumber energi tersebut mempengaruhi potensi menurunnya waktu pemakaian, 
atau dengan kata lain semakin banyak sensor menghasilkan sumber energi,
semakin cepat sensor tersebut harus diganti. Atau memang sensor tersebut tidak bekerja
apabila sensor terbebani oleh rangkaian penguat.

[![Permasalahan Sensor](/images/instrumentasi/sensor_opamp_differential.png)](http://tinyurl.com/y5sckkb9)

Dapat dilihat pada gambar diatas bahwa sensor mengharuskan mengeluarkan arus.
Itu menunjukkan bahwa sensor terbebani oleh rangkaian penguat.

[![Solusi Permasalahan Sensor](/images/instrumentasi/sensor_instumentasi.png)](http://tinyurl.com/y4ryefue)

Maka dapat diperhatikan bahwa pada penguat instrumentasi menyelesaikan permasalahan 
pembebanan pada sensor. Meskipun dalam kenyataannya op-amp tidak bekerja secara ideal,
akan tetapi dengan cara tersebut dapat mengurangi pembebanan pada sensor tersebut.

# Penguat Instrumentasi <a name="bab3"></a>

Penguat instrumentasi adalah gabungan antara penguat differensial dengan
penguat penyanggah. Tujuan dari penguat penyanggah adalah memberikan
impedansi yang tinggi terhadap input, agar rangkaian input tidak terbebani
oleh rangkaian penguat. Untuk menganalisa rangkaian ini akan jelaskan terlebih
dahulu bagian penguat penyanggah.

[![Rangkaian Penguat Instrumentasi](/images/instrumentasi/penguat_instrumentasi.png "fig:")](http://tinyurl.com/y6cgv6yy)

**Penguat Penyanggah**

Akan dianalisa perbandingan arus yang mengalis antara titik E-F dan $$V_a-V_b$$. 
Arus yang mengalir dari titik E-F dapat dianalisis sebagai berikut.

\begin{equation}   \label{eq:16} 
I_{EF} = \frac{V}{R} = \frac{V_E - V_F}{R_1 + 2R_2} 
\end{equation}

sedangkan arus yang mengalir pada titik $$V_a-V_b$$ dapat dianalisis sebagai
berikut

\begin{equation} \notag
  I_{ab} = \frac{V_a - V_b}{R_1}
\end{equation}

Perbedaan potensial antara kedua input op-amp penyanggah adalah
0 maka pada titik $$V_a = V_1$$ dan $$V_b = V_2$$.

\begin{equation} \label{eq:18}
  I_{ab} = \frac{V_1 - V_2}{R_1}
\end{equation}

dari persamaan \eqref{eq:16} dan \eqref{eq:18} dapat dijadikan perbandingan.

$$\begin{eqnarray*}
  \frac{V_1 - V_2}{R_1} &=& \frac{V_E - V_F}{R_1 + 2R_2}\\
  V_E - V_F &=& \frac{R_1 +2R_2}{R_1} (V_1 - R_2) \\
  V_E - V_F &=& (1 + \frac{2R_2}{R_1} (V_1 - R_2)
\end{eqnarray*}
$$

Apabila kedua ruas dikalikan dengan negatif.

\begin{equation} \label{eq:19}
  V_F - V_E = ( 1 + \frac{2R_2}{R_1} )(V_2 - V_1)
\end{equation}

**Hasil Akhir Penguat Instrumentasi**

Jika diperhatikan $$V_F - V_E$$ adalah tegangan input pada persamaan differensial
\eqref{eq:15} maka persamaan \eqref{eq:15} dapat  disubtitusikan dengan
persamaan \eqref{eq:19}, dengan itu akan menjadi tegangan output penguat instrumentasi. 


\begin{equation} \notag
V_{out} = ( \frac{R_3}{R_4} )( 1 + \frac{2R_2}{R_1} )(V_2 - V_1)
\end{equation}



Umumnya sebuah penguat instrumentasi $$R_3 = R_4$$ sehingga penguatan
differensialnya menjadi 1. Dengan itu maka dapat dikatakan penguat instrumentasi


\begin{equation} \notag 
  a = 1 + \frac{2R_2}{R_1}
\end{equation}

# Kesimpulan <a name="bab4"></a>

Maka dapat disimpulkan bahwa rumus dari penguat instrumentasi 

\begin{equation} \notag
V_{out} = ( 1 + \frac{2R_2}{R_1} )(V_2 - V_1)
\end{equation}

dengan kelebihan mengurangi pembebanan pada sensor.
