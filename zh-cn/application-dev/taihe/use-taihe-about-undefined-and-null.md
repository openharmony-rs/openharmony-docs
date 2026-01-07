# 使用Taihe进行undefined和null相关开发

## 简介

使用 Taihe 进行 undefined 和 null 相关开发时，可以使用 unit 类型。@null unit 类型对应 ets 中的 null 类型，@undefined unit 类型对应 ets 中的 undefined 类型。

## 基本概念

Taihe 相关代码示例

```rust
union NullableValue {
    uValue: @undefined unit;
    sValue: String;
    iValue: i32;
    nValue: @null unit;
}
```

以下是对应的 ets 代码

```typescript
export type NullableValue = undefined | string | int | null;
```

## 使用示例

### Taihe 声明

```rust
union NullableValue {
    uValue: @undefined unit;
    sValue: String;
    iValue: i32;
    nValue: @null unit;
}

function makeNullableValue(tag: i32): NullableValue;
```

### C++ 实现

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

### ets 侧使用

```typescript
let nvalue = makeNullableValue(0);
console.log("null: " + nvalue);
let svalue = makeNullableValue(1);
console.log("string: " + svalue);
let ivalue = makeNullableValue(2);
console.log("int: " + ivalue);
let uvalue = makeNullableValue(10);
console.log("undefined: " + uvalue);
```

Output：

```sh
null: null
string: hello
int: 123
undefined: undefined
```
