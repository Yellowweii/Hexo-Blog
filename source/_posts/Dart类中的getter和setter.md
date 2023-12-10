---
title: Dart类中的getter和setter
date: 2023-12-10 13:00:00
abbrlink: 60549
tags: ["Dart", "Flutter"]
categories: ["Flutter"]
cover: https://www.yellowwei.cn/img/2023-12-10.jpg
---

# Dart 类中的 getter 和 setter

> Dart 类中的 getter 和 setter 修饰符允许程序分别初始化和检索类字段的值。
> 使用 get 关键字定义 getter 或访问器。Setter 或存取器是使用 set 关键字定义的。
> 默认的 getter/setter 与每个类相关联。
> 但是，可以通过显式定义 setter/getter 来覆盖默认值。getter 没有参数并返回一个值，setter 只有一个参数但不返回值。

## Dart 不使用 getter 和 setter 修饰符的例子

定义一个 Rect 类，在初始化构造函数的时候可以传入宽度高度，调用 area 方法可以计算面积。

```dart
class Rect{
  num height;
  num width;

  Rect(this.height,this.width);
  area(){
    return this.height*this.width;
  }
}

void main(){
  Rect r=new Rect(10,4);
  print("面积:${r.area()}");
}
```

## Dart 中使用 getter 和 setter 修饰符的例子

定义一个 Rect 类，在初始化构造函数的时候可以传入宽度高度，调用 areaHeight 可以设置属性的值，调用 area 可以获取值。具体代码如下

```dart
class Rect{
  late num height;
  late num width;
  Rect(this.height,this.width);
  get area{    				//dart中定义一个getter
    return this.height*this.width;
  }
  set areaHeight(value){    //dart中定义一个setter
    this.height=value;
  }
}

void main(){
  Rect r=new Rect(10,4);

  r.areaHeight=6;   //调用setter 设置值

  print(r.area);    //调用getter 获取值

}
```
