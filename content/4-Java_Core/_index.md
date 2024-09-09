---
title : "Java Core "
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4 </b> "
---
## **Java Core Theory**

Java Core là nền tảng cốt lõi của ngôn ngữ lập trình Java. Các khái niệm cơ bản và thành phần chính của Java bao gồm cú pháp cơ bản, lớp, đối tượng, kế thừa, đa hình, xử lý ngoại lệ, và các khái niệm hướng đối tượng khác. 
Java Core giúp lập trình viên hiểu sâu hơn về cơ cấu và cách hoạt động của ngôn ngữ Java.

### **1. Lớp và Đối Tượng (Class & Object)**
- **Lớp (Class)** là một bản thiết kế (blueprint) từ đó các đối tượng được tạo ra. 
- Nó chứa các `thuộc tính`và `phương thức` mô tả hành vi của đối tượng.
- **Đối tượng (Object)** là một thực thể cụ thể của lớp. Một đối tượng có trạng thái (biến) và hành vi (phương thức).

**Ví dụ:**
```java
class Animal {
    String name;
    int age;

    void sound() {
        System.out.println(name + " makes a sound");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Animal();
        dog.name = "Dog";
        dog.age = 5;
        dog.sound();  // Output: Dog makes a sound
    }
}
```
### **2. Kế Thừa (Inheritance)**
- **Kế thừa** là một tính năng cho phép một lớp con (subclass) `thừa hưởng` các `thuộc tính` và `phương thức` từ lớp cha (superclass). Điều này giúp tái sử dụng mã và tăng tính linh hoạt.
   **Ví dụ**

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.sound();  // Output: Dog barks
    }
}

```

### **3. Đa hình (Polymorphism)**
- **Đa hình** cho phép một hành động có thể được thực hiện theo nhiều cách khác nhau. Trong Java, điều này có thể đạt được thông qua ghi đè phương thức (method overriding) và nạp chồng phương thức (method overloading).
- **Ví Dụ Tính Đa Hình Trong Thực Tế** : Mình có 2 con vật, khi nhận mệnh lệnh kêu thì chó sẽ kêu "gâu gâu" con mèo sẽ kêu "meo meo". 
>Thì 2 con vật trên đều được nhận mệnh lệnh là hãy kêu nx mà thực hiện theo cách của chúng  
- **Ví Dụ**
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Cat();
        animal.sound();  // Output: Cat meows
    }
}
```
### **4. Tính đóng gói (Encapsulation)**
- **Tính đóng gói (Encapsulation)** là một nguyên tắc trong lập trình hướng đối tượng, cho phép ẩn thông tin của đối tượng và chỉ cho phép các phương thức trong lớp đó truy cập vào các thuộc tính. Điều này giúp bảo vệ dữ liệu khỏi sự can thiệp trực tiếp từ bên ngoài và giảm sự phụ thuộc giữa các đối tượng.
- Trong Java, tính đóng gói được thực hiện bằng cách sử dụng các từ khóa truy cập như `defaut`, `public`, `private`, và `protected` để điều khiển quyền truy cập vào các biến và phương thức.

- **Ví Dụ**
```java
class Person {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```
### **5.Tính Trừu Tượng (Abstract Class)** 
- **Tính trừu tượng (Abstract Class)** là một lớp không thể tạo đối tượng trực tiếp và có thể chứa các phương thức trừu tượng (abstract methods) và các phương thức thông thường.
#### Tính trừu tượng thể hiện trong Java
 Bạn có thể đạt được trừu tượng thông qua hai cơ chế chính:

- `Abstract class trong Java (Lớp trừu tượng)` giúp đạt được tính trừu tượng từ 0 đến 100%.
- `Interfaces trong Java (giao diện)` giúp đạt tính trừu tượng đến 100%. 
```java 
abstract class Shape {
    protected int x, y;

    public Shape(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public abstract void draw();
}

class Circle extends Shape {
    private int radius;

    public Circle(int x, int y, int radius) {
        super(x, y);
        this.radius = radius;
    }

    @Override
    public void draw() {
        System.out.println("Drawing a circle at (" + x + ", " + y + ") with radius " + radius);
    }
}
```
#### **5.1 (Interface)**
- **Interface** : Interface là một dạng lớp trừu tượng (abstract class) mà tất cả các phương thức đều là phương thức trừu tượng. Lớp kế thừa interface phải thực thi toàn bộ các phương thức của nó.
- `Interface` không phải là 1 lớp(class) mà nó chỉ chứ các phuơng thức để các class khác implement nó 

```java
  interface Animal {
    void sound();
  }
 ```

```java
class Dog implements Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Dog();
        dog.sound();  // Output: Dog barks
    }
}
```

- Nếu là class thường thì phải implement lại tất cả các phương thức của class interface
- Nếu là class abtract class thì không cần phải implement của tất cả class interface

```java
interface HinhDang {
    void ve();  // Phương thức trừu tượng
    void xoa(); // Phương thức trừu tượng
}

class HinhTron implements HinhDang {
    @Override
    public void ve() {
        System.out.println("Vẽ hình tròn");
    }

    @Override
    public void xoa() {
        System.out.println("Xóa hình tròn");
    }
}
```

```java
interface HinhDang {
    void ve();  // Phương thức trừu tượng
    void xoa(); // Phương thức trừu tượng
}

abstract class Hinh implements HinhDang {
    @Override
    public void ve() {
        System.out.println("Vẽ hình");
    }
    // Phương thức xoa() không được triển khai trong lớp trừu tượng này
}

class HinhVuong extends Hinh {
    @Override
    public void xoa() {
        System.out.println("Xóa hình vuông");
    }
}
```


##### So Sánh interface và abtract class 
| Abtract Class                                                                                  | Interface                                            |
|------------------------------------------------------------------------------------------------|------------------------------------------------------|
| Abtract Class có phương thức `abtract` (không có thân hàm) và phương thúc `non-abtract`(có thân hàm) | interface có phương thức abtract,defaut và static    |
| Không hỗ trợ `tính đa kế thừa`                                                                 | Có hỗ trợ tính `đa kế thừa   `                       |
| Có các biến `final`,`non-final`,`static` và `non-static`                                       | Chỉ có tính `final` và `static`                      |
| Có thể cung cấp nôij dung cài đặt cho `interface`                                              | Không thể cung cấp nd cài đặt cho `abtract`          |
| Ví Dụ : public abtract class Shape public abtract void draw();                                 | Ví Dụ : public interface Drawable <br/> void draw(); | 


#### Map<String, String> errors= new HashMap<>();


