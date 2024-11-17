---
title: "Iterable Iterator"
date: 12 jan 2024
draft: true
slug: "iterable-iterator-java"
description:
author:
    email:
    name: "black-depressionises"
    image:
---

### Pendahuluan

{{< callout >}}

Sebelum mempelajari iterable dan iterator anda diharuskan memahami collection atau setidaknya tipe data array.

{{< /callout >}}

Iterable dan iterator merupakan interface yang digunakan untuk iterasi atau membaca data pada suatu list. Interface `Collection` extends `iterable` yang berarti subclass atau class implementasinya bisa diterapkan `foreach` untuk iterasi. Didalam interface `Iterable` memiliki method `getIterator` yang mengembalikan `iterator`, perbedaan diantara kedua interface tersebut adalah iterator berfokus untuk iterasi saja sedangkan iterable dapat mengiterasi dan memiliki method `splititerator` (belum ada informasi lanjut).

### Contoh

