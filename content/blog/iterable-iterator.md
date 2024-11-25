---
title: "Iterable Iterator"
date: 12 jan 2024
draft: false
slug: "iterable-iterator-java"
description:
thumbnail: "java"
author:
    email:
    name: "black-depressionises"
    image:
---

### Pendahuluan

{{< callout >}}

Sebelum mempelajari iterable dan iterator anda diharuskan memahami collection atau setidaknya tipe data array.

{{< /callout >}}

Iterable dan iterator merupakan interface yang digunakan untuk iterasi atau membaca data pada suatu list. Interface `Collection` extends `iterable` yang berarti subclass 
atau class implementasinya bisa diterapkan `foreach` untuk iterasi. Didalam interface `Iterable` 
memiliki method `getIterator` yang mengembalikan `iterator`, perbedaan diantara kedua interface 
tersebut adalah iterator berfokus untuk iterasi saja sedangkan iterable dapat mengiterasi dan memiliki method `splititerator` (belum ada informasi lanjut).

### Contoh

```java
//class user entities
public class User {
    private String name;
    private int age;

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

```java
//class list user implement iterable
public class ListUser implements Iterable<User> {
    ArrayList<User> list;

    public ListUser(ArrayList<User> list) {
        this.list = list;
    }

    @Override
    public Spliterator<User> spliterator() {
        return list.spliterator();
    }

    @Override
    public Iterator<User> iterator() {
        return list.iterator();
    }
}
```


```java 
public static void main(String[] args) {

        User x = new User("x",1);
        User y = new User("y",2);

        // membuat array list user
        ArrayList<User> users = new ArrayList<>();
        users.add(x);
        users.add(y);

        // instance list user
        ListUser listUser = new ListUser(users);

        // printout data list user dengan iterator
        listUser.iterator().forEachRemaining(s->System.out.println(s.getName()));

        // mendapatkan spliterator
        Spliterator<User> data = listUser.spliterator();
        // mendapatkan ukuran list
        System.out.println(data.getExactSizeIfKnown());
    }
```

### Penjelasan
Pada contoh kode diatas kita asumsikan ada data user pada database, lalu kita buat sebuah class
`ListUser` untuk menampung list dari user dan kita implement `Iterable<User>` agar data dapat 
di iterasi dan menggunakan method yang ada pada iterable.

Sebetulnya antara iterator dan iterable jarang kita buat secara mandiri, karena pada list atau 
collection java, sudah implement iterable.
