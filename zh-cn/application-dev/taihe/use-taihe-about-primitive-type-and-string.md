# 使用Taihe进行primitive type和string相关开发

## 简介

Taihe 提供基础类型和字符串类型。

## 基本概念

**基础类型映射表**

| taihe 类型 | C++ 侧投影类型  | C++ 侧投影（作为参数时） | ets 侧投影 |
| ---------- | --------------- | ------------------------ | ---------- |
| `i8`       | `int8_t`        | `int8_t`                 | `byte`     |
| `i16`      | `int16_t`       | `int16_t`                | `short`    |
| `i32`      | `int32_t`       | `int32_t`                | `int`      |
| `i64`      | `int64_t`       | `int64_t`                | `long`     |
| `u8`       | `uint8_t`       | `uint8_t`                | 不支持     |
| `u16`      | `uint16_t`      | `uint16_t`               | 不支持     |
| `u32`      | `uint32_t`      | `uint32_t`               | 不支持     |
| `u64`      | `uint64_t`      | `uint64_t`               | 不支持     |
| `f32`      | `float`         | `float`                  | `float`    |
| `f64`      | `double`        | `double`                 | `double`   |
| `bool`     | `bool`          | `bool`                   | `boolean`  |
| `String`   | `taihe::string` | `taihe::string_view`     | `string`   |

注意，目前Taihe支持unsigned类型，但ets并不支持，如果进行ets相关开发，请避免直接使用`u8`、`u16`、`u32`、`u64`。`Array<u8>`，`Array<u64>`等特例，后续会在[bigint](./use-taihe-about-bigint.md)，[arraybuffer](./use-taihe-about-arraybuffer-and-typedarray.md)章节介绍。

作为参数时，string 类型有 view 类型和非 view 类型，其中，view 类型的语义是不拥有所有权，只是对现有类型的引用，而非 view 类型则是拥有当前类型的所有权，用户可以根据使用场景来进行使用。

## 使用示例

### Taihe 声明

```rust
function baseCFunc(testBoolean : i32): bool;
// 对应 .d.ts 函数声明为
// function baseCFunc(testBoolean: int): boolean;
function baseDFunc(testBoolean : String): bool;
// 对应 .d.ts 函数声明为
// function baseDFunc(testBoolean: string): boolean;
```

### C++ 实现

```cpp
int testInt_add10_{10};

bool baseCFunc(int32_t testBoolean) {
  if (testBoolean == testInt_add10_) {
    return true;
  } else {
    return false;
  }
}

bool baseDFunc(string_view testBoolean) {
  if (testBoolean == "test123") {
    return true;
  } else {
    return false;
  }
}
```

### ets 侧使用

```typescript
// 显示设置
let res1 = baseCFunc(10);
console.log("BaseCFunc pass:", res1);
let res2 = baseCFunc(5);
console.log("BaseCFunc fail", res2);

let res3 = baseDFunc("test123");
console.log("BaseDFunc pass:", res3);
let res4 = baseDFunc("test1231");
console.log("BaseDFunc fail:", res4);
```

Output：

```sh
BaseCFunc pass: true
BaseCFunc fail false
BaseDFunc pass: true
BaseDFunc fail: false
```

## String C++ 使用方法

介绍 C++ 实现中的 String

- 创建 string

  ```cpp
  // 从 C 字符串创建
  taihe::string str1 = "Hello, Taihe!";

  // 从 std::string 创建
  std::string std_str = "Hello";
  taihe::string str2 = std_str;

  // 从 std::string_view 创建
  std::string_view std_sv = "World";
  taihe::string str3 = std_sv;

  // 指定长度创建
  taihe::string str4("Hello", 5);
  ```

- 输出 string

  ```cpp
  // taihe::string 可以使用 << 输出
  std::cout << "str1: " << str1 << "\n";

  // 使用已有字符串为 string_view 进行 0 拷贝的初始化
  string_view sv1 = str1;

  // string_view 可以使用 << 输出
  std::cout << "sv1: " << sv1 << "\n";
  ```

- 操作 string

  ```cpp
  // 访问字符串首字符和尾字符
  std::cout << "str1 front: " << str1.front() << "\n";
  std::cout << "str1 back: " << str1.back() << "\n";

  // 连接字符串
  string str5 = str1 + str2;
  std::cout << "str1 + str2: " << str5 << "\n";

  // 截取子字符串
  string str6 = str5.substr(0, 5); // arg0: inputStr, arg1: begin position, arg2: len
  std::cout << "Substring of str5 (first 5 chars): " << str6 << "\n";

  // 比较字符串
  std::cout << "str1 == str2: " << (str1 == str2) << "\n";

  // 转换整数到 string
  string numStr = to_string(12345);
  std::cout << "to_string(12345): " << numStr << "\n";

  // 转换浮点数到 string
  string floatStr = to_string(3.1415);
  std::cout << "to_string(3.1415): " << floatStr << "\n";

  // 转换布尔值到 string
  string boolTrueStr = to_string(true);
  string boolFalseStr = to_string(false);
  std::cout << "to_string(true): " << boolTrueStr << "\n";
  std::cout << "to_string(false): " << boolFalseStr << "\n";
  ```

- 字符串分为 string 和 string_view，string 拥有字符串的所有权，而 string_view 不拥有字符串的所有权

  ```cpp
  // string_view -> string 从不拥有所有权到拥有所有权会拷贝一次字符串，而反方向则不会进行拷贝
  string fun(string_view input) {
      return input; // 拷贝！
  }
  // 如果用户希望获得更好的性能，在不需要拷贝的场景则不使用 string 类型
  ```
