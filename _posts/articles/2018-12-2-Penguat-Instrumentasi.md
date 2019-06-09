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
  


# Penguat Differensial
--------------------

 ![Rangkaian Penguat Differensial](/images/instrumentasi/opamp_differential.png "fig:")

Untuk menganalisis keluaran tegangan pada penguat differensial dibagi
menjadi 3 bagian, yaitu analisis pada titik $$V_a$$, analisis pada titik
$$V_b$$ dan gabungan dari keduanya.

## Analisis Pada titik \\(V_a\\)

Seperti yang telah diketahui bahwa resistansi pada pin input op-amp
bernilai besar, sehingga tidak ada arus yang masuk kedalam pin input
op-amp negative maupun positif. Sehingga arus yang mengalir pada
\\(i_1 = i_f \\) . 

$$ \begin{eqnarray}
  i_1 &=& i_f\\
  \frac{V_1 - V_a}{R_1} &=& \frac{V_a - V_{out}}{R_3} \\
  \frac{R_3}{R_1} (V_1 - v_a) &=& V_a - V_{out} \\
  \frac{R_3}{R_1} V_1 -  \frac{R_3}{R_1} V_a - V_a &=& -V_{out} \\
  V_{out} &=& V_a (1 + \frac{R_3}{R_1}) - \frac{R_3}{R_1} V_1 \label{eq:6}
\end{eqnarray}
$$

## Analisis Pada Titik \\(V_b\\)

Sama dengan Analisis pada titik \\(V_a\\) bahwa arus yang masuk pada pin
input op-amp mendekati 0. Apabila arus yang mengalir pada titik $$V_b$$
menuju ground melewati resistansi \\(R_1\\) dinotasikan dengan \\(i_4\\), Maka
arus yang mengalir pada \\(i_2 = i_4\\). Sedangkan beda potensian diantara
pin input op-amp memiliki besaran yang sama, sehingga \\(V_a = V_b\\).
$$\begin{eqnarray}
  i_2 &=& i_4 \\
  \frac{V_2 - V_b}{R_2} &=& \frac{V_b - 0 (\text{Ground})}{R_4} \label{eq:7}\\
  \frac{R_2}{R_4} (V_2 - V_b) &=& V_b \\
  \frac{R_2}{R_4} V_2 &=&  \frac{R_2}{R_4} V_b + V_b \\
  \frac{R_2}{R_4} V_2 &=& V_b (\frac{R_2}{R_4} + 1) \\
  V_b (R_2 + R_4) &=& R_4 V_2 \\
  V_b &=& V_a = \frac{R_4}{R_2 + R_4} V_2 \label{eq:12}
\end{eqnarray}
$$

## Analisis Hubungan \\(V_a\\) dan \\(V_b\\)

Dengan persamaan (\eqref{eq:12}) kedalam persamaan \eqref{eq:6}, dengan asumsi
bahwa \\(R_1 = R_2 = R\\) dan \\(R_3 = R_4 = Ra\\). $$\begin{eqnarray}
  V_{out} &=&  ( \frac{Ra}{R + Ra} ) (1 + \frac{Ra}{R}) V_2 - \frac{Ra}{R} V_1 \\
  V_{out} &=&  \frac{Ra(R+Ra)}{R (R + Ra)} V_2 - \frac{Ra}{R} V_1\\
  v_{out} &=& \frac{Ra}{R} (V_2 - V_1)\label{eq:15}
\end{eqnarray}
$$

# Penguat Instrumentasi

Penguat instrumentasi adalah gabungan antara penguat differensial dengan
penguat penyanggah. Penguat penyanggah digunakan untuk memberikan
impedansi yang tinggi terhadap tegangan input. Untuk menganalisa
rangkaian ini, terlebih dahulu menganalisa penguat penyanggahnya.

![Rangkaian Penguat
Instrumentasi](/images/instrumentasi/penguat_instrumentasi.png "fig:")

...
### Penguat Penyanggah

apabila titik antara $$R_1$$ (atas) dan pin keluaran op-amp $$A_1$$
dinotasikan E dan titik antara $$R_1$$(bawah) dan pin keluaran op-amp $$A_2$$ dinotasikan
F. Maka dengan ini akan dianalisa perbandingan arus yang mengalis antara titik
E-F dan $$V_a-V_b$$. Arus yang mengalir dari titik E-F dapat dianalisis sebagai
berikut.
\begin{equation}  i_{EF} = \frac{V}{R} = \frac{V_E - V_F}{R_1 + 2R_2}  \label{eq:16} \end{equation}
sedangkan arus yang mengalir pada titik $$v_a-V_b$$ dapat dianalisis sebagai
berikut:
\begin{equation}
  i_{ab} = \frac{V_a - V_b}{R_1}
\end{equation}
dimana op-amp $$A_1$$ dan $$A_2$$ , perbedaan potensial antara kedua inputnya adalah
0 maka pada titik $$V_a = V_1$$ dan $$V_b = V_2$$.
\begin{equation} \label{eq:18}
  i_{ab} = \frac{V_1 - V_2}{R_1}
\end{equation}
dari persamaan (\eqref{eq:16}) dan (\eqref{eq:18}) dapat dijadikan perbandingan.
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

Jika diperhatikan $$V_F - V_E$$ adalah tegangan input pada persamaan differensial
(\eqref{eq:15}) maka persamaan (\eqref{eq:15}) dapat  disubtitusikan dengan
persamaan (\eqref{eq:19}), dengan itu akan menjadi tegangan output penguat instrumentasi. 
\begin{equation}\label{eq:20}
V_{out} = ( \frac{R_3}{R_4} )( 1 + \frac{2R_2}{R_1} )(V_2 - V_1)
\end{equation}
Umumnya sebuah penguat instrumentasi $$R_3 = R_4$$ sehingga penguatan
differensialnya menjadi 1. Dengan itu maka dapat dikatakan penguat instrumentasi
\begin{equation} \label{eq:21}
  a = 1 + \frac{2R_2}{R_1}
\end{equation}


<span>9</span> biblabel\#1
@bibitem\#1<span>@bibitem<span>\#1</span>-</span>

Siwindarto, Ponco. 2018. *Presentasi Sistem Instrumentasi Elektronika
Lanjut*. Malang: Universitas Brawijaya.

[^1]: Datasheet pH Sensor yang dipublish oleh
    [DFRobot](https://media.digikey.com/pdf/Data%20Sheets/DFRobot%20PDFs/SEN0161_SEN0169_Web.pdf)
