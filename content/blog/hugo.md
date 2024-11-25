---
title: "Berkenalan Dengan Hugo"
date: 13 jan 2024
draft: false
slug: "introduction-to-hugo"
description: "whats is hugo ssg"
author:
    email:
    name: "black-depressionises"
    image:
---

### Pendahuluan

Website dibagi menjadi 2 kategori yakni, statis dan dinamis. Perbedaan mendasar dan 
mudah dikenali adalah bagaimana website tersebut menyajikan data, apakah menggunakan
database dan bagaimana interaksi website tersebut dengan user, apakah user dapat 
mencari konten yang dibutuhkan atau user dapat membuat dan menghasilkan data pada 
website tersebut. Jika hal diatas dapat dilakukan maka website tersebut adalah jenis
website dinamis, contoh saja website berita, atau elearning sekolah. Contoh website 
statis seperti halaman portofolio yang hanya memberikan data profile seseorang atau
seperti website ini.

Hugo merupakan teknologi _SSG_ _(static site generator)_, saat ini teknologi ssg 
banyak digunakan karena kemudahan dalam membuat website yang bersifat dokumentatif
atau seperti blog, selain itu akses deployment pada website statis banyak yang gratis
dan kemudahan dalam membuat konten dikarenakan menggunakan [markdown](https://www.markdownguide.org/).

### Struktur Folder

{{< figure src="hugo-1.png" height="400" width="300" id="1" alt="struktur folder" caption="struktur folder hugo" >}}

Struktur folder hugo diatas merupakan contoh, ada beberapa folder dan file tambahan
yang saya gunakan seperti `node_modules`. 

1. `archtypes` berisi template untuk konten
2. `assets` berisi asset yang digunakan pada konten, dengan dukungan hugo pipelines. Saya
sendiri lebih menggunakan penyimpanan `static`
3. `content` isi konten kamu
4. `data` isi data format seperti json (info saya sedikit)
5. `layout` template yang digunakan pada website
6. `static` seperti folder public yang dapat diakses public, dan digunakan
untuk assets seperti `css`,`js` dan sebagainya.
7. `themes` template yang kalian gunakan, semisalnya kalian menggunakan template orang lain

_Download template seperti website ini disini [here](https://drive.google.com/file/d/1NKnaD2XbdxKYqlKIwQbu5OhSTtWaJsuh/view?usp=sharing)_

### Command Line Hugo

#### 1. Hugo serve
Saya tidak tahu kenapa terkadang cache pada hugo masih menempel. Jika kalian 
merubah css terkadang tidak langsung di apply oleh hugo maka dari itu gunakan sintaksis
dibawah ini dan lebih baik gunakan mode private browser.

```go
 hugo serve --ignoreCache --disableFastRender
```


#### 2. Hugo membuat konten

```go
 hugo new content nama_file_dapat_disertakan_folder
 
 hugo new --kind nama_template nama_file_dapat_disertakan_folder
 
 // contoh
 // akan membuat konten dengan template default pada folder content\blog\helo.md
 hugo new content blog/helo.md

```