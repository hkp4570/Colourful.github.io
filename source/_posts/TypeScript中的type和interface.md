---
title: TypeScript中的type和interface
date: 2024-7-9 10:19:55
categories:	
  - 记录
tags:
  - typescript
---

在`TypeScript`中，`type`和`interface`都用来定义类型，但它们在使用方式和功能上有一些关键区别。

### type

------

`type`用于定义类型别名，可以是任意类型的组合，包括基本类型、联合类型、交叉类型等。使用非常灵活，可以表示复杂的类型结构。

<!-- more -->

使用示例：

```typescript
type StringOrNumber = string | number;

type User = {
  name: string;
  age: number;
};

type PartialUser = {
  name?: string;
  age?: number;
};

type UserOrPartialUser = User | PartialUser;
```

### interface

------

`interface`是对象的模板，可以描述对象的属性及其类型。它支持继承，可以扩展和合并其他接口。

使用示例：

```typescript
interface A {
  name: string;
  age: number;
}

interface B {
  color: string;
}
// 接口继承
interface Circle extends A {
  employeeId: number;
}
interface Rect extends A, B {
}
// 接口合并
interface A {
  card: object,
}

interface Animal {
  name: string;
  move(distance: number): void;
}

class Dog implements Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  move(distance: number) {
    console.log(`${this.name} moved ${distance} meters.`);
  }
}

```

### 关键区别

------

1. 用途和灵活性
   - `type`可以用来定义基本类型、联合类型、交叉类型，元祖等，使用更灵活。
   - `interface`主要用来定义对象的模板。
2. 扩展和合并
   - `interface`可以通过`extends`关键字来继承其他接口，可以多次声明同一个接口，所有声明会被合并。
   - `type`可以通过交叉类型（`&`）来组合类型，但不能多次声明同一个类型别名。
3. 实现类：
   - `interface`可以被类实现（`implements`）。
   - `type`不支持直接被类实现。
4. 语法特性：
   - `interface`可以有可选属性（通过`?`标记）。
   - `type`也可以通过联合类型和交叉类型实现类似的功能，但语法上不如`interface`明确。
