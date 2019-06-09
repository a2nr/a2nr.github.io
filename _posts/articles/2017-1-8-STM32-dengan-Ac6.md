---
layout: post
title:  "Generate Source dengan STM32Cube"
date:   2017-01-08T14:21:28+07:00
categories: articles
author: anggoro_dwi
tags: [Embedded,STM32,STM32Cube, SW4STM32]
comments: true
share: true
---

## Review


### STM 32

STM 32 adalah microcotroller 32 bit yang dibuat oleh STMElectronics. Baca selanjutnya di [Wikipedia](https://en.wikipedia.org/wiki/STM32) atau langsung ke [st.com](http://www.st.com/en/microcontrollers/stm32-32-bit-arm-cortex-mcus.html?querycriteria=productId=SC1169).


### STM32Cube

[STM32Cube](http://www.st.com/en/embedded-software/stm32cube-embedded-software.html?querycriteria=productId=LN1897) ini adalah tool yang dibuat oleh ST Electronic sendiri yang memudahkan bagi programmer buat generate code dengan configurasi register yang interaktif. Tool ini sangat mempersingkat effort kita buat configurasi register dan lain lain dan nanti bakal bisa langsung di import ke eclipse atau IDE lain. keren ya. :flushed:

## Install & Download

berikut adalah link untuk langkah - langkah installasi atau link download applikasi yang di butuhkan :

- [STM32CubeMX](http://www.st.com/en/development-tools/stm32cubemx.html)

## Step by step

### Generate Source dari STM32Cube

![STM33CubeMX](/images/Tutorial/STM32CubeMX-Screen.png "Screen Awal")

- Click New Project > Pilih Jenis microcontroller (Disini tutorial nya menggunakan STM32F446RETx ~~Itu yang tak punya :p~~) >> OK

	![Step 1](/images/Tutorial/New-Project-step-1.png "New Project Window")

- Configurasi Peripheral yang di inginkan di tab Pinout, Clock configuration dan Utak atik aja disana deh :sparkles:.

	![Step 2](/images/Tutorial/New-Project-step-2.png "Configurasi Pinout")

- Configurasi Clock nya. Disinilah yang membuat tool ini sangat berguna. :sparkles: Kebanyakan configurasi clock nya agak rumit.

	![Step 3](/images/Tutorial/New-Project-step-3.png "Configurasi Clock")

- Configurasi yang lebih specific ke pheripheral ada di Tab Configuration

	![Step 4](/images/Tutorial/New-Project-step-4.png "Configurasi specific Pheriperal")

- Atur tempat untuk meletakkan source nya. Project>>Seting..(Alt+p)
	- :exclamation: Perhatikan Toolchain/IDE >> SW4STM32.
	- :exclamation: Mcu and Firmware Package.

	![Step 5](/images/Tutorial/New-Project-step-5.png "Project Setting")

- Code Generator.

	![Step 6](/images/Tutorial/New-Project-step-6.png "Project Setting")

- Install New Library. Help>>Install New Library (alt+u) >> Select Firmware package for Family STM32F4 yang paling terbaru >> Install Now 

	![Step 7](/images/Tutorial/New-Project-step-7.png "Install New Library")

- Setlah itu Generate Code nya. Project>>Generate Code(Ctrl+Shift+G)

	![Step 8](/images/Tutorial/loading-generate-code.png "Generate Code")
	![Step 9](/images/Tutorial/loading-generate-code-1.png "Generate Code")
