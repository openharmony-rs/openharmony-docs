# 使用 Taihe 进行 BigInt 相关开发

## 简介

`BigInt` 用于表示任意精度的整数，在 Taihe 中使用 `@bigint Array<u64>` 表示。在 Taihe C++ 实现侧，其使用方法与 `Array` 一致。

## 基本概念

| Taihe 类型           | C++ 侧类型               | C++ 侧类型（作为参数时）      |
| -------------------- | ------------------------ | ----------------------------- |
| `@bigint Array<u64>` | `taihe::array<uint64_t>` | `taihe::array_view<uint64_t>` |

`BigInt` 的 C++ 实现侧与 `Array` 几乎一致，但模板实参必须为 `uint64_t` 类型。可移步 [`Array` 相关文档](./use-taihe-about-array.md)查看 C++ 侧 `taihe::array<T>` 的相关介绍。

Taihe 中 `BigInt` 表示为二进制补码，在 Taihe C++ 实现侧以 `taihe::array<uint64_t>` 的形式存在。Taihe 提供了一些实用函数，便于在 C++ 侧对 `BigInt` 进行操作，文末将进行详细介绍。


## 使用示例

接下来介绍使用 Taihe 进行 `BigInt` 开发的流程

示例代码功能：将输入的 `bigint` 左移 64 位，并将原输入以 `uint64_t` 输出

### 在 Taihe 文件中声明

```rust
function processBigInt(a: @bigint Array<u64>): @bigint Array<u64>;
```

### C++ 侧 实现声明的接口

```cpp
taihe::array<uint64_t> processBigInt(taihe::array_view<uint64_t> a) {
	taihe::array<uint64_t> res(a.size() + 1);
	res[0] = 0;
	for (std::size_t i = 0; i < a.size(); i++) {
		res[i + 1] = a[i];
		// 将原输入以 `uint64_t` 输出
		std::cerr << "arr[" << i << "] = " << a[i] << std::endl; 
	}
	return res;
}
```

### 生成 `bigint.ets`

```typescript
native function _taihe_processBigInt_native(a: BigInt): BigInt;
export function processBigInt(a: BigInt): BigInt {
    return _taihe_processBigInt_native(a);
}
function _taihe_processBigInt_reverse(a: BigInt): BigInt {
    return processBigInt(a);
}
```

### ets 侧使用

```typescript
let num1: BigInt = bigint.processBigInt(18446744073709551616n)
console.log(num1)
let num2: BigInt = bigint.processBigInt(-65535n)
console.log(num2);
// 输出：
// arr[0] = 0
// arr[1] = 1
// 340282366920938463463374607431768211456
// arr[0] = 18446744073709486081
// -1208907372870555465154560
```

## C++ 侧 BigInt 实用函数介绍

Taihe 中 `BigInt` 用二进制补码表示，在 C++ 实现侧，符号位是 `taihe::array<T>` 最后一个元素的最高有效位。数字为负数时，符号位为 1；为非负数时，符号位为 0。

```cpp
// 从整数类型中获取最高有效位或符号位
template<typename T, std::enable_if_t<std::is_integral_v<T>, int> = 0>
bool get_msb(T dig) {
  return dig >> (sizeof(T) * 8 - 1) != 0;
}
```

```cpp
// 从以 array 表示的二进制补码 bigint 中获取符号
//
// 例如:
//   get_sign([0x7f]) => false        (+127)
//   get_sign([0x80]) => true         (-128)
//   get_sign([0x80, 0x00]) => false  (+128)
//   get_sign([0x00, 0xff]) => true   (-256)
//   get_sign([0x00]) => false        (   0)
template<typename T, std::enable_if_t<std::is_integral_v<T>, int> = 0>
bool get_sign(taihe::array_view<T> num) {
  return get_msb(num[num.size() - 1]);
}
```

```cpp
// 从以 array 表示的二进制补码 bigint 中获取 符号 和 绝对值（没有额外的符号位）
//
// For example:
//   get_sign_and_abs([0x7f]) => {false, [0x7f]}             (+127)
//   get_sign_and_abs([0x80]) => {true, [0x80]}              (-128)
//   get_sign_and_abs([0x80, 0x00]) => {false, [0x80]}       (+128)
//   get_sign_and_abs([0x00, 0xff]) => {true, [0x00, 0x01]}  (-256)
//   get_sign_and_abs([0x00]) => {false, []}                 (   0)
template<typename T, std::enable_if_t<std::is_integral_v<T>, int> = 0>
std::pair<bool, taihe::array<T>> get_sign_and_abs(taihe::array_view<T> num) {
  T *buf = reinterpret_cast<T *>(malloc(num.size() * sizeof(T)));
  bool sign = get_msb(num[num.size() - 1]);  // 获取符号位
  if (sign) {
    // 获取负数绝对值
    bool carry = true;
    for (std::size_t i = 0; i < num.size(); i++) {
      buf[i] = ~num[i] + carry;
      carry = carry && (buf[i] == 0);
    }
  } else {
    // 获取非负数绝对值
    for (std::size_t i = 0; i < num.size(); i++) {
      buf[i] = num[i];
    }
  }
  // 删除多余的高位
  std::size_t size = num.size();
  while (size > 0 && buf[size - 1] == 0) {
    size--;
  }
  return {sign, taihe::array<T>(buf, size)};
}
```

```cpp
// 给定一个二进制补码 bigint 的符号和绝对值，创建其对应的 array
//
// For example:
//   get_num(false, [0x7f]) => [0x7f, 0x00]       (+127)
//   get_num(true, [0x80]) => [0x80, 0x00]        (-128)
//   get_num(false, [0x80]) => [0x80, 0x00]       (+128)
//   get_num(true, [0x00, 0x01]) => [0x00, 0xff]  (-256)
//   get_num(false, []) => [0x00]                 (   0)
template<typename T, std::enable_if_t<std::is_integral_v<T>, int> = 0>
taihe::array<T> build_num(bool sign, taihe::array_view<T> abs) {
  T *buf = reinterpret_cast<T *>(malloc((abs.size() + 1) * sizeof(T)));
  if (sign) {
    // 为负数创建 array
    bool carry = true;
    for (std::size_t i = 0; i < abs.size(); i++) {
      buf[i] = ~abs[i] + carry;
      carry = carry && (buf[i] == 0);
    }
    buf[abs.size()] = carry - 1;
  } else {
    // 为非负数创建 array
    for (std::size_t i = 0; i < abs.size(); i++) {
      buf[i] = abs[i];
    }
    buf[abs.size()] = 0;
  }
  // 删除多余的高位
  std::size_t size = abs.size() + 1;
  while (size >= 2 && ((buf[size - 1] == 0 && get_msb(buf[size - 2]) == 0) ||
                       (buf[size - 1] == -1 && get_msb(buf[size - 2]) == 1))) {
    size--;
  }
  return taihe::array<T>(buf, size);
}
```
