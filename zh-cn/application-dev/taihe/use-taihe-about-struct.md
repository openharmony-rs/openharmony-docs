# 使用Taihe进行struct相关开发

## 简介

使用 Taihe 进行纯数据类型的接口相关开发时，可以使用 struct。struct 是数据成员的组合，其成员可以是任意 Taihe 中的数据类型，包括[基础类型](./use-taihe-about-primitive-type-and-string.md)、[枚举类型](./use-taihe-about-enum-and-const.md)、[接口类型](./use-taihe-about-interface.md)、[标签联合](./use-taihe-about-union.md)和其他[结构体类型](./use-taihe-about-struct.md)等。

## 基本概念

Taihe 相关代码示例

```rust
struct Color{
    R: i32;
    G: i32;
    B: i32;
}
```

以下是对应的 ets 代码

```typescript
export interface Color {
  R: int;
  G: int;
  B: int;
}
```

要设置 struct 中的只读属性，可以使用 @readonly 注解。

Taihe 相关代码示例

```rust
struct Student {
    @readonly name: String;
    age: i32;
}
```

以下是对应的 ets 代码

```typescript
export interface Student {
  readonly name: string;
  age: int;
}
```

## 使用示例

### Taihe 声明

```rust
struct Color{
    R: i32;
    G: i32;
    B: i32;
}
function convert_color(a: Color): Color;

struct Student {
    @readonly name: String;
    age: i32;
}
function create_student(): Student;
function process_student(a: Student): Student;
```

### C++ 实现

```cpp
Color convert_color(Color const &a) {
  return Color{a.G, a.B, a.R};
}
Student create_student() {
  return Student{"Mary", 15};
}
Student process_student(Student const &a) {
  return {a.name + " student", a.age + 10};
}
```

### ets 侧使用

```typescript
let Color1: Color = { R: 0, G: 255, B: 255 };
console.log("Color1 is " + Color1.R + " " + Color1.G + " " + Color1.B);
let Color2 = convert_color(Color1);
console.log("Color2 is " + Color2.R + " " + Color2.G + " " + Color2.B);

let student: Student = { name: "Jack", age: 10 };
let pro_student = process_student(student);
console.log("process student:", pro_student.name, pro_student.age);
```

Output：

```sh
Color1 is 0 255 255
Color2 is 255 255 0
process student: Jack student 20
```

## Struct C++ 使用方法

在 C++ 中创建和初始化结构体对象：

```cpp
// 使用花括号语法
Color color_rgb = Color{0x39, 0xC5, 0xBB};

// 或者使用命名初始化
Color color_rgb = Color{
    .R = 0x39,
    .G = 0xC5,
    .B = 0xBB,
};
```
