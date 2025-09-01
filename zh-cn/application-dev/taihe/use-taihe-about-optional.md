# 使用 Taihe 进行 optional 相关开发

## 简介

使用 Taihe 进行可选属性相关开发时，可以使用 Optional<T> 或 @optional 注解。

## 基本概念

Taihe 相关代码示例

```rust
Optional\<T\>
```

以下是对应的 ets 代码

```typescript
T | undefined;
```

例如 `Optional\<String\>` 对应 `string | undefined`。

Taihe 相关代码示例

```rust
@optional item: Optional\<T\>
```

以下是对应的 ets 代码

```typescript
item ?: T
```

例如 `@optional item: Optional\<String\>` 对应 `item ?: String`。

## 使用示例

### Taihe 声明

```rust
function showOptionalString(@optional a: Optional<String>): Optional<String>;
// 对应 .d.ts 函数声明为
// function showOptionalString(a?: string): string | undefined;
function showOptionalBool(a: Optional<bool>): Optional<bool>;
// 对应 .d.ts 函数声明为
// function showOptionalBool(a: boolean | undefined): boolean | undefined;
```

### C++ 实现

```cpp
::taihe::optional<::taihe::string> showOptionalString(::taihe::optional_view<::taihe::string> a) {
    if (a.has_value()) {
      return a;
    } else {
      return ::taihe::optional<::taihe::string>{std::nullopt};
    }
}

::taihe::optional<bool> showOptionalBool(::taihe::optional_view<bool> a) {
    if (a.has_value()) {
        return a;
    } else {
        return ::taihe::optional<bool>{std::nullopt};
    }
}
```

### ets 侧使用

```typescript
let result1 = showOptionalString("my_opt_str");
let result2 = showOptionalString();
let result3 = showOptionalBool(undefined);
console.log("show my optional string value: " + result1);
console.log("show my optional string undefined: " + result2);
console.log("show my optional string param undefined: " + result3);
```

Output：

```sh
show my optional string value: my_opt_str
show my optional string undefined: undefined
show my optional string param undefined: undefined
```

## Optional C++ 使用方法

这里对 C++ 实现中的 optional 进行介绍

- 创建 optional

  创建空 optional 的方法如下，其中 T 为对应类型

  ```cpp
  ::taihe::optional<T> opt = std::nullopt;
  ```

  创建非空 optional 的方法如下，其中 T 为对应类型，val 为对应类型的变量

  ```cpp
  ::taihe::optional<T> opt(std::in_place, val);
  ```

- 判断 optional 是否有值

  判断 `optional` 是否有值，可以将 `optional` 对象转换为 `bool`，或使用 `has_value` 函数。

  ```cpp
  bool tag = bool(opt);
  bool tag = opt.has_value();
  ```

- 获取 optional 的值

  获取 optional 的实际值可以直接从 optional 对象中取值，或通过 value 函数获取

  ```cpp
  int32_t var0 = *opt;
  int32_t var1 = opt.value();
  ```
