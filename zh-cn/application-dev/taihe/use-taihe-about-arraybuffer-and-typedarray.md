# 使用Taihe进行ArrayBuffer和TypedArray相关开发

## 简介

`ArrayBuffer` 是一段通用的、固定长度的原始二进制数据缓冲区。在 ets 侧，`ArrayBuffer` 中的内容不能直接操作，而是需要包装成 `TypedArray` 对象来读写。

## 基本概念

| Taihe 类型 | C++ 侧类型           | C++ 侧类型（作为参数时）  |
| ------------- | -------------------- | ------------------------- |
| `@arraybuffer Array<u8>`    | `taihe::array<uint8_t>` | `taihe::array_view<uint8_t>` |
| `@typedarray Array<T>` | `taihe::array<T>` | `taihe::array_view<T>` |

`TypedArray` 是一组类型化数组的统称，其子类有 `Uint8Array`、`Int8Array`、`Int16Array`、`Int32Array` 等。它们都是视图（View），在 ets 侧用来读写 `ArrayBuffer` 中的数据，并且按固定的数值类型和字节大小解析。

在 Taihe 中，`ArrayBuffer` 使用 `@arraybuffer Array<u8>` 表示，`TypedArray` 使用 `@typedarray Array<T>` 表示。

`ArrayBuffer` 和 `TypedArray` 的 C++ 实现侧与 `Array` 几乎一致，但 `ArrayBuffer` 对应的模板实参必须为 `uint8_t`， `TypedArray` 则没有限制。可移步 [`Array` 相关文档](./use-taihe-about-array.md)查看 C++ 侧 `taihe::array<T>` 相关介绍。

## 使用示例

### `ArrayBuffer` 示例

接下来介绍使用 Taihe 进行 `ArrayBuffer` 开发的流程

示例代码功能：将连续的 `byte` 数据转换为 `int` 类型。

**1. 在 Taihe 文件中声明**

```rust
function convert2Int(a: @arraybuffer Array<u8>): i32;
```

**2. C++ 侧 实现声明的接口**

```cpp
// 将一段连续的 byte 转换成 int 类型
int32_t convert2Int(taihe::array_view<uint8_t> a) {
    int32_t num = 0;
    if (a.size() >= 4) { 
        num = *(int32_t*)a.begin();
    } else {
        set_business_error(1, "ArrayBuffer len < 4");
    }
    return num;
}
```

**3. 生成 `arraybuffer.ets`**

```typescript
native function _taihe_convert2Int_native(a: ArrayBuffer): int;
export function convert2Int(a: ArrayBuffer): int {
    return _taihe_convert2Int_native(a);
}
function _taihe_convert2Int_reverse(a: ArrayBuffer): int {
    return convert2Int(a);
}
```

**4. ets 侧使用**

`main.ets`

```typescript
let numbersU8: byte[] = [1, 1, 0, 0, 0];
let arrbuf1: ArrayBuffer = new ArrayBuffer(numbersU8.length);
for (let i = 0; i < numbersU8.length; i++) {
    arrbuf1.set(i, numbersU8[i]);
}
let num1 = other_type.convert2Int(arrbuf1);
console.log("num1: " + num1);
// 输出：
// num1: 257

// 以下代码示例会触发 C++ 侧 Error
let arrbuf2: ArrayBuffer = new ArrayBuffer(3);
for (let i = 0; i < 3; i++) {
    arrbuf2.set(i, numbersU8[i]);
}
let num2 = arraybuffer.convert2Int(arrbuf2);
console.log("num2: " + num2);
// [TID xxx] E/runtime: Error: ArrayBuffer len < 4
```

### `TypedArray` 示例

接下来介绍使用 Taihe 进行 `TypedArray` 开发的流程。

示例代码功能：为 `ArrayBuffer` 创建 `Uint16Array` 并打印

**1. 在 Taihe 文件中声明**

```rust
function createUint16Array(): @typedarray Array<u16>;
function printUint16Array(arr: @typedarray Array<u16>): void;
```

**2. C++ 侧 实现声明的接口**

```cpp
taihe::array<uint16_t> createUint16Array() {
    return {1, 3, 5, 6, 9};
}

void printUint16Array(taihe::array_view<uint16_t> arr) {
    size_t i = 0;
    for (uint16_t val : arr) {
        std::cout << "Index: " << i++ << " Value: " << val << std::endl;
    }
}
```

**3. 生成 `typedarray.ets`**

```typescript
native function _taihe_createUint16Array_native(): Uint16Array;
native function _taihe_printUint16Array_native(arr: Uint16Array): void;
export function createUint16Array(): Uint16Array {
    return _taihe_createUint16Array_native();
}
export function printUint16Array(arr: Uint16Array): void {
    return _taihe_printUint16Array_native(arr);
}
function _taihe_createUint16Array_reverse(): Uint16Array {
    return createUint16Array();
}
function _taihe_printUint16Array_reverse(arr: Uint16Array): void {
    return printUint16Array(arr);
}
```

**4. ets 侧使用**

`main.ets`
```typescript
// ets 侧创建 TypedArray 对象，C++ 侧 print
let arrbuf = new ArrayBuffer(8);
arrbuf.set(0, 0xff as byte);
arrbuf.set(1, 0xff as byte);
arrbuf.set(2, 0x01 as byte);
arrbuf.set(3, 0x00 as byte);
let ets_uarr = new Uint16Array(arrbuf, 0, 2);
typearr.printUint16Array(ets_uarr);
// 输出:
// Index: 0 Value: 65535
// Index: 1 Value: 1
// 注：上述输出在小端字节序的情况下得到

// C++ 侧创建 TypedArray 对象，ets 侧 print
let c_uarr = typearr.createUint16Array();
console.log(c_uarr);
// 输出:
// 1,3,5,6,9
```
