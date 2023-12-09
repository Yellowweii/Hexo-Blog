---
title: Dart中的静态成员和静态方法
tags:
  - Dart
  - Flutter
categories:
  - Flutter
abbrlink: 54667
date: 2023-12-09 14:00:00
cover:
---

# Dart 中的静态成员和静态方法

**Dart 中的静态成员:**

1. 使用 static 关键字来实现类级别的变量和函数
1. 静态方法不能访问非静态成员，非静态方法可以访问静态成员

## Dart 中的静态属性和静态方法可以直接使用类名称访问。

```dart
class Person {
  static String name = '张三';
  static void show() {
    print(name);
  }
}

main(){
  print(Person.name);
  Person.show();
}
```

## 静态方法不能访问非静态成员，非静态方法可以访问静态成员

```dart
class Person {
  static String name = '张三';
  int age=20;
  static void show() {
    print(name);
  }
  void printInfo(){  /*非静态方法可以访问静态成员以及非静态成员*/
      print(name);  //访问静态属性 不要加this
      print(this.age);  //访问非静态属性
      show();   //调用静态方法

  }
  static void printUserInfo(){//静态方法
        print(name);   //静态属性
        show();        //静态方法

        print(this.age);    //错误：静态方法没法访问非静态的属性
        this.printInfo();   //错误: 静态方法没法访问非静态的方法
        printInfo();        //错误:
  }
}

main(){

  Person.printUserInfo();

}
```
