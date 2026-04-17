# 使用Taihe进行enum和const相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

使用Taihe进行枚举类型开发时，可以使用`enum`表示有限状态。使用Taihe进行常量开发时，可以在`enum`上使用`@const`注解。

## 基本概念

Taihe相关代码示例

```rust
enum Color: String {
    RED = "Red",
    GREEN = "Green",
    BLUE = "Blue",
}
```

以下是对应的ets代码

```typescript
export enum Color {
  RED = "Red",
  GREEN = "Green",
  BLUE = "Blue",
}
```

Taihe相关代码示例

```rust
@const
enum Flags: f64 {
    FLAG_F64_A = 1.0,
    FLAG_F64_B = 1.0 + 1.0,
}
```

以下是对应的ets代码

```typescript
export const FLAG_F64_A: double = 1.0;
export const FLAG_F64_B: double = 2.0;
```

## 使用示例

### Taihe声明

```rust
enum Color: String {
    RED = "Red",
    GREEN = "Green",
    BLUE = "Blue",
}
@const
enum Flags: f64 {
    FLAG_F64_A = 1.0,
    FLAG_F64_B = 1.0 + 1.0,
}
function nextEnum(color: Color): Color;
```

注意，在ets的语法中，enum只有number和string两种类型，ets类型与Taihe类型的对应关系可参考[使用Taihe进行primitive type和string相关开发](./use-taihe-about-primitive-type-and-string.md)。

### C++实现

```cpp
Color NextEnum(Color color) {
  return (Color::key_t)(((int)color.get_key() + 1) % 3);
}
```

### ets侧使用

```typescript
let color = Color.GREEN;
let nextColor = nextEnum(color);
console.info("show next Color:", nextColor);
console.info("show const FLAG_F64_A:", FLAG_F64_A);
console.info("show const FLAG_F64_B:", FLAG_F64_B);
```

Output：

```sh
show next Color: Blue
show const FLAG_F64_A: 1
show const FLAG_F64_B: 2
```

## Enum C++使用方法

这里对C++实现中的enum进行介绍

- 创建enum

  用户可以使用`{enum}::key_t::{enum_item}`通过key来构造enum对象，以示例enum为例：

  ```cpp
  Color red = Color::key_t::RED;
  ```

- 读取enum的键与值

  用户可以使用`get_key()`与`get_value()`获取enum的键与值，以本例enum为例：

  ```cpp
  Color::key_t key = color.get_key();
  ::taihe::string val = color.get_value();
  ```
