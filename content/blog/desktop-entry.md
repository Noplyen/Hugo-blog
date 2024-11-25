---
title: "Membuat Desktop Entry"
date: 20 jan 2024
draft: false
slug: 'desktop-entry'
description: 'how to create desktop entry linux ubuntu'
thumbnail: 'linux'
author:
    email:
    name: "Rey-Li-Gionese"
    image:
---

### Pendahuluan
Saat menginstal perangkat lunak di Linux dengan format `.tar.gz`, kita biasanya perlu mengekstraknya 
terlebih dahulu sebelum dapat menggunakan aplikasinya. File yang diekstrak sering kali berupa skrip `.sh` atau file `AppImage`. 
Namun, sangat merepotkan jika kita harus masuk ke folder penyimpanan setiap kali ingin menjalankan aplikasi tersebut.
Bagaimana cara agar aplikasi tersebut muncul di menu utama atau desktop Anda? Solusinya adalah dengan membuat Desktop Entry, simak langkahnya berikut.

### Langkah - langkah

1. Buat file berekstensi `.desktop`
2. Kalian bisa membuka terminal lalu gunakan command `touch nama_file.desktop`
3. Buka file dengan file editor atau dengan `nano`  menggunakan command  `nano nama_file.desktop`
4. Paste kode berikut dan sesuaikan 
```shell
    [Desktop Entry]
    Name= application name ex : IntelliJ IDEA
    Comment= a short description for app ex:IntelliJ IDEA IDE for development
    Exec= path to the applications bash file Ex : /downloads/intellij/idea.sh
    Icon= path for icon desktop entry
    Terminal=false
    Type=Application
    Categories= category desktop entry ex: Development;IDE;
```


5. Pindahkan file tersebut ke   `/usr/share/applications`

### Informasi Lanjut
1. Command line

{{< figure src="desktop-entry-1.png" width="600" id="1" alt="desktop entry" caption="desktop entry" >}}


2. Target file

{{< figure src="desktop-entry-2.png" id="2" alt="file target" caption="file target" >}}


tekan `ctrl+l` untuk copy path, lalu gunakan `.svg` untuk value icon dan `.sh` untuk value exec 

