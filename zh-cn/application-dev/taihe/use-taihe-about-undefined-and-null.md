# 使用Taihe进行undefined和null相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

使用Taihe进行undefined和null相关开发时，可以使用unit类型。@null unit类型对应ets中的null类型，@undefined unit类型对应ets中的undefined类型。

## 基本概念

Taihe相关代码示例

```rust
union NullableValue {
    uValue: @undefined unit;
    sValue: String;
    iValue: i32;
    nValue: @null unit;
}
```

以下是对应的ets代码

```typescript
export type NullableValue = undefined | string | int | null;
```

## 使用示例

### Taihe声明

```rust
union NullableValue {
    uValue: @undefined unit;
    sValue: String;
    iValue: i32;
    nValue: @null unit;
}

function makeNullableValue(tag: i32): NullableValue;
```

### C++实现

```cpp
constexpr int32_t TAG_NULL = 0;
constexpr int32_t TAG_STRING = 1;
constexpr int32_t TAG_INT = 2;

NullableValue makeNullableValue(int32_t tag) {
  switch (tag) {
  case TAG_NULL:
    return NullableValue::make_nValue();
  case TAG_STRING:
    return NullableValue::make_sValue("hello");
  case TAG_INT:
    return NullableValue::make_iValue(123);
  default:
    return NullableValue::make_uValue();
  }
}
```

### ets侧使用

```typescript
let nvalue = makeNullableValue(0);
console.info("null: " + nvalue);
let svalue = makeNullableValue(1);
console.info("string: " + svalue);
let ivalue = makeNullableValue(2);
console.info("int: " + ivalue);
let uvalue = makeNullableValue(10);
console.info("undefined: " + uvalue);
```

Output：

```sh
null: null
string: hello
int: 123
undefined: undefined
```
