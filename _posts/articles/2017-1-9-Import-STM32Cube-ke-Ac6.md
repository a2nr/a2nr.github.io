---
layout: post
title:  "Import STM32Cube ke Ac6"
date:   2017-01-09 12:34:00 +0700
tags: Eclipse Ac6 STM32 STM32Cube
author: anggoro_dwi
categories: articles
author: anggoro_dwi
tags: [Embedded, Eclipse, Ac6, STM32, STM32Cube]
comments: true
share: true
---


# بِسْمِ اللهِ الرَّحْمٰنِ الرَّحِيْمِ


# Review


## Eclipse IDE C/C++

[Eclipse](https://eclipse.org/downloads/) ? tau lah... :wink:


## Work Space Ac6 

System Workbench adalah toolchain. biasanya di sebut SW4STM32, ini adalah software development enviroment yang multi platform dan gratis, dimana mensupport banya jenis dari microcontroller STM32 dan board yang lain.
Toolchain System Workbench dan collaborative website dibuat oleh [AC6](http://www.openstm32.org/HomePage).


# Install & Download

berikut adalah link untuk langkah - langkah installasi atau link download applikasi yang di butuhkan :

- [Eclipse IDE for C/C++ Developers](http://www.eclipse.org/downloads/packages/)
	pilih yang paling terbaru ya.

- [Install Ac6](http://www.openstm32.org/Installing+System+Workbench+for+STM32+from+Eclipse?structure=Documentation)
	Sebelum masuk ke link nya harus log in dulu, jadi harus bikin akun) :stuck_out_tongue_winking_eye:

## Step by Step
![Workspace](/images/170801/workspace_Eclipse.png)

- Install Eclipse IDE for C/C++ Developers.
- Install System Workbench Ac6 di Eclipse. Ikuti langkah langkah instalasinya di [sini](http://www.openstm32.org/Installing+System+Workbench+for+STM32+from+Eclipse?structure=Documentation)
- Lakukan Generate Source dulu di [sini](https://mori3rti.github.io/blog/STM32-dengan-Ac6) dan pastikan didalam foldernya dengan membukanya. :thumbsup: 
	![Tree Folder](/images/170801/Tree_SW4STM32.png)
- kembali ke Eclipse nya. File >> Import >> Existing Projects into Workspace >> Next
	![Import](/images/170801/Import_SW.png)
- Pilih [x] Select root directory >> Browse ... >> Pilih tempat Foldernya >> Project : [x] ... (Nama_foldermu / Select All) >>[ ] Copy projects into workspace (optional) >> Finish
	![Import](/images/170801/Import_SW_1.png)
    
- Nanti akan muncul folder tree dieclipse
    ![Tree](/images/170801/Tree_eclipse.png)
