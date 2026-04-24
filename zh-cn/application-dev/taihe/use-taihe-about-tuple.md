# 使用Taihe进行tuple相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

在Taihe中声明的struct上可以使用`@tuple`注解来指定该struct在ArkTS侧以tuple的形式进行投影。使用`@tuple`注解后，Taihe会将该struct的成员按照声明顺序映射为ArkTS中的tuple元素。

## 基本概念

Taihe相关代码示例

```rust
@tuple
struct Color{
    R: i32;
    G: i32;
    B: i32;
}
```

以下是对应的ets代码

```typescript
export type Color = [int, int, int];
```

## 使用示例

### Taihe声明

```rust
@tuple
struct Color{
    R: i32;
    G: i32;
    B: i32;
}

function convert_color(a: Color): Color;
```

### C++实现

```cpp
Color convert_color(Color const& color) {
    return Color{255 - color.R, 255 - color.G, 255 - color.B};
}
```

### ets侧使用

```typescript
let color1: [int, int, int] = [0x39, 0xC5, 0xBB];
let color2: [int, int, int] = convert_color(color1);
console.info(`Color1 is ${color1[0]} ${color1[1]} ${color1[2]}`);
console.info(`Color2 is ${color2[0]} ${color2[1]} ${color2[2]}`);
```

输出结果如下：

```sh
Color1 is 57 197 187
Color2 is 198 58 68
```
