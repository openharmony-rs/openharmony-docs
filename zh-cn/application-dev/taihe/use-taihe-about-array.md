# 使用Taihe进行Array相关开发

## 简介

`Array` 是定长数组，在 Taihe 中表示为 `Array<T>`。Taihe 在 C++ 实现侧提供了一些相关操作函数便于开发。

## 基本概念

| Taihe 类型 | C++ 侧类型        | C++ 侧类型（作为参数时） |
| ---------- | ----------------- | ------------------------ |
| `Array<T>` | `taihe::array<T>` | `taihe::array_view<T>`   |

`Array` 创建后大小不可改变，且为值语义，没有引用计数，拷贝时会复制内部所有元素。

`Array` 在 C++ 实现侧有 view 类型（视图类型）和非 view 类型（持有者类型），其中，view 类型的语义是不拥有所有权，只是对现有类型的引用，而非 view 类型则是拥有当前类型的所有权。

建议**只有**在**必须获取所有权**的情况下使用 `taihe::array<T>`，其他情况使用`taihe::array_view<T>`。

## 使用示例

接下来介绍使用 Taihe 进行 `Array` 开发的流程

示例代码功能：将 `Array<i32>` 转换为 `int`。

### Taihe 文件中声明

```rust
function convert2Int(a: Array<i32>): i32;
```

### C++ 侧实现

```cpp
int32_t convert2Int(taihe::array_view<int32_t> a) {
  // 可通过 size() 获取 array 长度
  int32_t input_size = a.size();
  int32_t num = 0;
  for (int32_t i = 0; i < input_size; i++) {
    // 可以通过下标访问数组
    num = num * 10 + a[i];
  }
  return num;
}
```

### 生成 `array.ets`

```typescript
native function _taihe_convert2Int_native(a: Array<int>): int;
export function convert2Int(a: Array<int>): int {
    return _taihe_convert2Int_native(a);
}
function _taihe_convert2Int_reverse(a: Array<int>): int {
    return convert2Int(a);
}
```

### ets 侧使用

```typescript
let arr: int[] = [1, 2, 3, 4, 5];
let num = array.convert2Int(arr);
console.log("num: " + num);
// 输出:
// num: 12345
```

## C++ 侧 taihe::array\<T\> 介绍

### 1. 创建数组

`taihe::array<T>` 可以通过指定大小或使用初始化列表创建，以下是一些示例：
```cpp
#include <taihe/array.hpp>

// 1. 创建指定大小的数组（元素默认初始化）
taihe::array<int> arr1(5);

// 2. 创建并用特定值填充
taihe::array<int> arr2(5, 42);  // 5个元素，都是42

// 3. 从初始化列表创建
taihe::array<int> arr3 = {1, 2, 3, 4, 5};

// 4. 从 std::vector 创建
std::vector<int> vec = {6, 7, 8};
taihe::array<int> arr4(taihe::copy_data, vec.begin(), vec.size());

// 5. 从 C 数组创建
int c_arr[] = {9, 10, 11};
taihe::array<int> arr5(taihe::copy_data, c_arr, 3);
```
对于 4 和 5 的创建方式，可以使用 `taihe::move_data` 代替 `taihe::copy_data` 作为第一个参数，表示从源容器中移动数据，而不是复制数据。

### 2. 访问和遍历

Taihe 的数组提供了多种访问和遍历方式，以下是一些常用操作：
```cpp
// 下标访问
int first = arr3[0];
int last = arr3[arr3.size() - 1];

// at()访问
int first = arr3.at(0);
int last = arr3.at(arr3.size() - 1);

// 安全访问（会检查边界）
try {
    int value = arr3.at(10);  // 抛出 std::out_of_range
} catch (const std::out_of_range& e) {
    // 处理越界
}

// 获取首尾元素
int front = arr3.front();
int back = arr3.back();

// 遍历数组
for (int value : arr3) {
    std::cout << value << " ";
}

// 使用迭代器便利
// 注意使用 begin()，end() 获取的是指针
for (auto it = arr3.begin(); it != arr3.end(); ++it) {
    std::cout << *it << " ";
}

// 使用迭代器反向遍历
// 注意使用 rbegin()，rend() 获取的是指针
for (auto it = arr3.rbegin(); it != arr3.rend(); ++it) {
    std::cout << *it << " ";
}

// 获取原始指针和数组大小
int* data = arr3.data();
size_t size = arr3.size();
```

### 3. 视图类型

`taihe::array_view<T>` 用于函数参数传递：

```cpp
void process_array(taihe::array_view<int> view) {
    for (int value : view) {
        // 处理元素
    }
}

// 可以传入 array、vector、C 数组等
taihe::array<int> arr = {1, 2, 3};
std::vector<int> vec = {4, 5, 6};
int c_arr[] = {7, 8, 9};

process_array(arr);
process_array(vec);
process_array(c_arr);
```
`taihe::array<T>` 拥有所有权，而 `taihe::array_view<T>` 不拥有
```cpp
// example
// taihe::array_view<T> -> taihe::array<T> 从“不拥有所有权”到“拥有所有权”会进行一次拷贝，而反方向则不会进行拷贝
taihe::array<int> func(taihe::array_view<int> input) {
    return input; // 拷贝！
}
```
