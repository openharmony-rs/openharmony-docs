# 使用Taihe进行optional相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @k1ngqaquuu-->

## 简介

使用Taihe进行可选属性相关开发时，需要使用到`Optional<T>`类型及`@optional`注解。

## 基本概念

`Optional<T>`是一个模板类型，表示一个值可能存在（持有一个`T`类型的值），也可能不存在（持有空值）。它在C++侧对应`taihe::optional<T>`，在ArkTS侧则对应`T | undefined`。

`@optional`是一个注解，可用于修饰函数参数或结构体成员，表示在ArkTS中调用该函数或创建该结构体时，该参数或成员是可省略的（默认值为`undefined`），相当于ArkTS中的`a?: T`。

**_需要特别注意的是，在使用`@optional`注解时，务必要保证其修饰的参数或成员的类型是可为空的（即`Optional<T>`或有`@undefined unit`类型成员的联合体类型等）。_**这是因为`@optional`注解本身只影响ArkTS侧的调用签名，并不会改变C++侧接收的参数类型。如果一个参数或成员被`@optional`注解修饰，但其声明的类型却不可为空，那么当在ArkTS侧省略该参数或成员时，会传入一个C++侧无法接受的空值，从而导致运行时错误。

## 使用示例

### Taihe声明

```rust
function optionalIntToString(@optional a: Optional<i32>): Optional<String>;
// 对应.d.ts函数声明为
// function optionalIntToString(a?: number): string | undefined;
function optionalBooleanToString(a: Optional<bool>): Optional<String>;
// 对应.d.ts函数声明为
// function optionalBooleanToString(a: boolean | undefined): string | undefined;
```

### C++实现

```cpp
::taihe::optional<::taihe::string> optionalIntToString(::taihe::optional_view<::taihe::string> a) {
    if (a.has_value()) {
      return taihe::optional<::taihe::string>(std::in_place, taihe::to_string(*a));
    } else {
      return std::nullopt;
    }
}

::taihe::optional<::taihe::string> optionalBooleanToString(::taihe::optional_view<bool> a) {
    if (a.has_value()) {
        return taihe::optional<::taihe::string>(std::in_place, taihe::to_string(*a));
    } else {
        return std::nullopt;
    }
}
```

### ets侧使用

```typescript
let result1 = optionalIntToString(1);
let result2 = optionalIntToString();
let result3 = optionalBooleanToString(true);
let result4 = optionalBooleanToString(undefined);
console.info("optionalIntToString(1) = " + result1);
console.info("optionalIntToString() = " + result2);
console.info("optionalBooleanToString(true) = " + result3);
console.info("optionalBooleanToString(undefined) = " + result4);
```

### 输出结果

```sh
optionalIntToString(1) = 1
optionalIntToString() = undefined
optionalBooleanToString(true) = true
optionalBooleanToString(undefined) = undefined
```

## Optional C++使用方法

这里对C++实现中的optional进行介绍。

- 创建optional

  创建空optional的方法如下，其中T为对应类型。

  ```cpp
  ::taihe::optional<T> opt = std::nullopt;
  ```

  创建非空optional的方法如下，其中T为对应类型，val为对应类型的变量。

  ```cpp
  ::taihe::optional<T> opt(std::in_place, val);
  ```

- 判断optional是否有值

  判断`optional`是否有值，可以将`optional`对象转换为`bool`，或使用`has_value`函数。

  ```cpp
  bool tag = bool(opt);
  bool tag = opt.has_value();
  ```

- 获取optional的值

  获取optional的实际值可以直接从optional对象中取值，或通过value函数获取。

  ```cpp
  int32_t var0 = *opt;
  int32_t var1 = opt.value();
  ```
