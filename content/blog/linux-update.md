---
title: "Pengalaman upgrade versi linux bantuan chatgpt"
date: 08 12 2024
draft: false
slug: 'upgrade-versi-linux'
description: 'Pengalaman upgrade versi linux bantuan chatgpt'
thumbnail: 'linux'
author:
    email:
    name: "commander-brains"
    image:
---

#### Pendahuluan
Penggunaan AI (_artificial intelligence_) saat ini banyak diterapkan dan digunakan
pada banyak bidang, bagi saya sendiri ai seperti chatgpt adalah seacrh engine baru
yang lebih baik ketimbag konvensional seperti google search engine. Pada contoh kali 
ini saya menggunakan chatgpt untuk membantu saya akan ketidaktahuan saya tentang
linux terlebih upgrade versi linux, sebagai informasi saya menggunakan linux untuk
kegiatan sehari - hari karena windows terlalu berat untuk saya, dan menurut saya
linux mudah dipahami seperti ubuntu atau kubuntu, tidak semenyeramkan apa yang ada
di internet.

#### Cerita
Versi ubuntu saat ini  untuk LTS (_long term support_) adalah versi 24.04, dan 
pada komputer saya masih versi 23.04 terlewat versi 23.10. Saya sendiri tidak 
tahu bagaimana cara upgrade versi jika kasusnya seperti ini, sebelumnya saya 
melihat banyak video dan membaca artikel terkait upgrade versi ubuntu dengan
terminal. Tidak terlalu sulit akan tetapi untuk kasus lewat versi ini saya 
belum menemukannya, ada salah satu pertanyaan yang sama di stack overflow dan
jawabannya adalah kita tidak bisa melewati atau lompat versi. Dari sini saya
mencoba bertanya ke chatgpt dan jawabannya pun serupa.

Saya pun memberanikan diri untuk upgrade versi, dengan mencari dan bertanya
chatgpt poin langkah yang saya dapatkan : 
1. Mendapatkan repository yang dapat di update `sudo apt update`
2. Upgrade repository yang dapat di update `sudo apt upgrade`
3. Melihat versi ubuntu yang dapat kita upgrade `sudo apt list --upgradable`
4. Melakukan upgrade `sudo do-release-upgrade`
5. Selanjutnya jawab pertanyaan saja yang muncul pada terminal, yes atau no. 
Mudah dihapami untuk pertanyaannya, jangan takut.
6. Reboot `sudo reboot`

Proses ini memakan waktu dan kuota, sekitar 1.3gb kuota saya terkuras dan sekitar
hampir 1 jam untuk proses upgrade versi ini, pastikan komputer kalian tercharging.
Tetapi ada yang aneh, seharusnya saya akan menuju versi 23.10 tetapi saat ini saya
berada di LTS 24.04

{{< figure src="update-versi.jpeg" height="400" width="600" id="1" alt="proses upgrade" caption="doc proses upgrade" >}}
{{< figure src="hasil-upgrade.png" height="400" width="600" id="2" alt="hasil upgrade" caption="hasil upgrade" >}}

Kebetulan saya suka menggunakan produk IDE _JetBrains_
