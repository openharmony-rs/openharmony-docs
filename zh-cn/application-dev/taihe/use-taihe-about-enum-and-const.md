# 使用 Taihe 进行 enum 和 const 相关开发

## 简介

使用 Taihe 进行枚举类型开发时，可以使用 `enum` 表示有限状态。使用 Taihe 进行常量开发时，可以在 `enum` 上使用 `@const` 注解。

## 基本概念

Taihe 相关代码示例

```rust
enum Color: String {
    RED = "Red",
    GREEN = "Green",
    BLUE = "Blue",
}
```

以下是对应的 ets 代码

```typescript
export enum Color {
  RED = "Red",
  GREEN = "Green",
  BLUE = "Blue",
}
```

Taihe 相关代码示例

```rust
@const
enum Flags: f64 {
    FLAG_F64_A = 1.0,
    FLAG_F64_B = 1.0 + 1.0,
}
```

以下是对应的 ets 代码

```typescript
export const FLAG_F64_A: double = 1.0;
export const FLAG_F64_B: double = 2.0;
```

## 使用示例

### Taihe 声明

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

注意，在 ets 的语法中，enum 只有 number 和 string 两种类型，ets 类型与 Taihe 类型的对应关系可参考[使用 Taihe 进行 primitive type 和 string 相关开发](./use-taihe-about-primitive-type-and-string.md)。

### C++ 实现

```cpp
Color NextEnum(Color color) {
  return (Color::key_t)(((int)color.get_key() + 1) % 3);
}
```

### ets 侧使用

```typescript
let color = Color.GREEN;
let nextColor = nextEnum(color);
console.log("show next Color:", nextColor);
console.log("show const FLAG_F64_A:", FLAG_F64_A);
console.log("show const FLAG_F64_B:", FLAG_F64_B);
```

Output：

```sh
show next Color: Blue
show const FLAG_F64_A: 1
show const FLAG_F64_B: 2
```

## Enum C++ 使用方法

这里对 C++ 实现中的 enum 进行介绍

- 创建 enum

  用户可以使用 `{enum}::key_t::{enum_item}` 通过 key 来构造 enum 对象，以示例 enum 为例：

  ```cpp
  Color red = Color::key_t::RED;
  ```

- 读取 enum 的键与值

  用户可以使用 `get_key()` 与 `get_value()` 获取 enum 的键与值，以本例 enum 为例：

  ```cpp
  Color::key_t key = color.get_key();
  ::taihe::string val = color.get_value();
  ```
