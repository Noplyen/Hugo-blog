---
title: "Functional Programming 1"
date: 10 jan 2024
draft: false
slug: 'functional-programming-java-part-1' 
description: 'learn functional programming java part 1'
thumbnail: 'java'
author:
    email:
    name: "anton-zuckeberg"
    image:
---

#### Pendahuluan
Fungsional programming adalah suatu cara paradigma untuk menggunakan fungsi/method
dalam memecahkan masalah, umumnya pada parameter method kita akan melihat variable
apa saja yang dibutuhkan, tetapi pada fungsional programming kita dapat menaruh kode
proses dalam parameter tersebut. Di java kita mengenal lambda, untuk melakukan
fungsional programming, fitur ini sangat bagus jika digabung bersama api stream. Pada
kesempatan kali ini kita akan mencoba fungsional programming dengan java.

#### Praktik
##### 1. Merubah data ke bentuk lain
Pada kasus ini kita akan merubah suatu objek ke objek lain

1. Membuat employee class
```java
public class Employee {
    private short id;
    private String name;
    private String fullName;
    private String email;
    private short age;
    
    // Setter dan getter
    }
```
2. Membuat userDto class
```java 
public class UserDTO {
    private short id;
    private String name;
    private String email;

    // setter dan getter
}
```
3. Membuat class repository employee sederhana yang menampung data employee
```java 
public class EmployeeRepository {
    private ArrayList<Employee> employees;

    public EmployeeRepository() {
        employees = new ArrayList<>();

        Employee employee1 = new Employee((short)1,"Agustina","Agustina Anggraeni","agustina@yoo.co.id",(short)29);
        Employee employee2 = new Employee((short)2,"Mahendra","Muali Mahendra","mahendra@yoo.co.id",(short)22);
        Employee employee3 = new Employee((short)3,"Eka","Kusnaedi Ekawati","eka@yoo.co.id",(short)30);
        Employee employee4 = new Employee((short)4,"Christian","Christian Yonex","yonex@yoo.co.id",(short)33);
        Employee employee5 = new Employee((short)5,"Bram","Bramesta Jonnet","bram@yoo.co.id",(short)23);


        employees.add(employee1);
        employees.add(employee2);
        employees.add(employee3);
        employees.add(employee4);
        employees.add(employee5);

    }

    public ArrayList<Employee> getEmployees() {
        return employees;
    }

} 
```
4. Membuat class service dan implementasi fungsional programming
```java 
public class EmployeeService {
    private EmployeeRepository employeeRepository;
    public EmployeeService() {
        employeeRepository = new EmployeeRepository();
    }

    // Case 1 parsing data (DTO)
    // without functional programming
    public List<UserDTO> getUserDTO_Type1(){
        ArrayList<Employee> employees = employeeRepository.getEmployees();
        ArrayList<UserDTO> userDTOS = new ArrayList<>();

        for (Employee employee : employees){
            UserDTO userDTO = new UserDTO();

            userDTO.setEmail(employee.getEmail());
            userDTO.setId(employee.getId());
            userDTO.setName(employee.getName());

            userDTOS.add(userDTO);
        }

        return  userDTOS;
    }

    // Case 1 parsing data (DTO)
    // with functional programming
    public List<UserDTO> getUserDTO_type2(){
       return employeeRepository.getEmployees()
                .stream()
                .map(employee -> {
                    UserDTO userDTO = new UserDTO();

                    userDTO.setEmail(employee.getEmail());
                    userDTO.setId(employee.getId());
                    userDTO.setName(employee.getName());
                    return userDTO;
                }).toList();
    }

    // Case 1 parsing data (DTO)
    // with functional programming
    public List<UserDTO> getUserDTO_type3(){
        return employeeRepository.getEmployees()
                .stream()
                .map(this::toUserDTO).toList();
    }

    public UserDTO toUserDTO(Employee employee){
        UserDTO userDTO = new UserDTO();

        userDTO.setEmail(employee.getEmail());
        userDTO.setId(employee.getId());
        userDTO.setName(employee.getName());
        return userDTO;

    }

    // Case 1 parsing data (DTO)
    // with functional programming
    public List<UserDTO> getUserDTO_type4(){
        return employeeRepository.getEmployees()
                .stream()
                .map(UserDTO::new).toList();
    }
}
```

### Penjelasan
Kita fokus ke no 4 pada bagian service, dimana proses penggunaan
fungsional terjadi. Pada service diatas kita sedang merubah list
employee menjadi userDto, ada beberapa cara dalam penerapannya.

1. tanpa fungsional programming
Disini terlihat sangat panjang tetapi masih mudah untuk dipahami,
dimana kita menampung data employee pada `employees` lalu membuat
arraylist userDto untuk menampung data yang sudah diubah. Dan proses
foreach adalah proses perubahan dari employee menjadi userDto terjadi.
```java 
public List<UserDTO> getUserDTO_Type1(){
        ArrayList<Employee> employees = employeeRepository.getEmployees();
        ArrayList<UserDTO> userDTOS = new ArrayList<>();

        for (Employee employee : employees){
            UserDTO userDTO = new UserDTO();

            userDTO.setEmail(employee.getEmail());
            userDTO.setId(employee.getId());
            userDTO.setName(employee.getName());

            userDTOS.add(userDTO);
        }

        return  userDTOS;
}
```

2. Menggunakan fungsional programming
Pada fungsi tipe ke 2 sudah menggunakan fungsional programming (lambda),
kita menggunakan stream (aliran) lalu dipetakan dengan `map` yang didalamnya
terdapat lambda ekspresi yang akan merubah setiap data employee menjadi userDto,
dan terakhir di collect menjadi list. Tipe ini sudah cukup baik tetapi saya
memiliki cara yang lebih baik pada tipe ke 3 dan 4.
```java 
public List<UserDTO> getUserDTO_type2(){
       return employeeRepository.getEmployees()
                .stream()
                
                // employee disini merupakan data iterasi yang berlangsung
                // jika ada 10 data maka akan diiterasi sebanyak 10x
                // setiap data akan diubah menjadi userDto
                // dan ditempatkan pada suatu penampung hingga 10 data
                // berhasil di iterasi, dan semua data akan ditampung
                // pada list lihat (.toList())
                .map(employee -> {
                    UserDTO userDTO = new UserDTO();

                    userDTO.setEmail(employee.getEmail());
                    userDTO.setId(employee.getId());
                    userDTO.setName(employee.getName());
                    return userDTO;
                }).toList();
    }
```

Pada tipe ke 3 kita memisahkan logika dalam merubah setiap data employee
menjadi userDto ke dalam sebuah fungsi `toUserDto`, jadi pada **map**
akan memanggil fungsi tersebut.

```java 
 public List<UserDTO> getUserDTO_type3(){
        return employeeRepository.getEmployees()
                .stream()
                .map(this::toUserDTO).toList();
    }

    public UserDTO toUserDTO(Employee employee){
        UserDTO userDTO = new UserDTO();

        userDTO.setEmail(employee.getEmail());
        userDTO.setId(employee.getId());
        userDTO.setName(employee.getName());
        return userDTO;

    }
```

Pada tipe ke 4, ini lebih canggih dimana kita akan membuat 
konstruktor tambahan pada `userDto` dengan parameter `employee`
untuk merubah data employee menjadi userdto.

```java 
 public List<UserDTO> getUserDTO_type4(){
        return employeeRepository.getEmployees()
                .stream()
                .map(UserDTO::new).toList();
    }
```

pada class userDto
```java 
 public UserDTO(Employee employee) {
        this.id = employee.getId();
        this.email = employee.getEmail();
        this.name = employee.getName();
    }
```

---
_Ilmu ini saya dapat dari Victor Rentea pada video devoxx_ [here](https://www.youtube.com/watch?v=YnzisJh-ZNI)