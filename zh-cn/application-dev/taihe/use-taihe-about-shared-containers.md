# 使用Taihe进行共享容器相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @k1ngqaquuu-->

## 简介

共享容器用于把ArkTS侧已有的容器以共享的方式传给C++侧直接使用。C++侧对共享容器进行修改后，ArkTS侧持有的原始容器也会同步反映这些修改。

普通的`Vector`、`Map`、`Set`和`Array`会将上层容器中的所有数据拷贝传给C++侧，所以对C++侧的修改不会反映到ArkTS侧，这适用于只需要在C++侧读取数据的场景；而需要C++和ArkTS共同操作同一个容器时，可以使用`SharedVector`、`SharedMap`、`SharedSet`或`SharedArray`。

> **注意：**
>
> 共享容器只能用于将ArkTS侧已有容器传入C++。不能在C++侧新建共享容器后作为结果返回给ArkTS侧。

## 基本概念

| Taihe类型 | ArkTS侧类型 | C++侧持有类型 | C++侧临时借用类型 |
| --- | --- | --- | --- |
| `SharedVector<T>` | `Array<T>` | `taihe::shared_vector<T>` | `taihe::shared_vector_view<T>` |
| `SharedMap<K, V>` | `Map<K, V>` | `taihe::shared_map<K, V>` | `taihe::shared_map_view<K, V>` |
| `@record SharedMap<K, V>` | `Record<K, V>` | `taihe::shared_map<K, V>` | `taihe::shared_map_view<K, V>` |
| `SharedSet<T>` | `Set<T>` | `taihe::shared_set<T>` | `taihe::shared_set_view<T>` |
| `@arraybuffer SharedArray<T>` | `ArrayBuffer` | `taihe::shared_array<T>` | `taihe::shared_array_view<T>` |
| `@typedarray SharedArray<T>` | 对应的TypedArray | `taihe::shared_array<T>` | `taihe::shared_array_view<T>` |

`SharedArray<T>`的元素必须是标量类型。使用`@arraybuffer`时，`T`只能是`i8`或`u8`；使用`@typedarray`时，`T`必须是整数或浮点类型。

`*_view`是共享容器的临时借用类型。它适合作为函数参数，仅在函数执行期间访问容器；需要长期保存容器时，必须保存为不带`_view`的持有类型。

## SharedVector

`SharedVector<T>`对应ArkTS侧的`Array<T>`，可以按下标读取、修改、插入和删除元素。

**Taihe声明**

```rust
function insertAfterFirst(names: SharedVector<String>, name: String): String;
```

**C++侧实现**

```cpp
#include <taihe/error.hpp>
#include <taihe/expected.hpp>
#include <taihe/shared_vector.hpp>
#include <taihe/string.hpp>

taihe::expected<taihe::string, taihe::error> insertAfterFirst(
    taihe::shared_vector_view<taihe::string> names,
    taihe::string_view name)
{
    // get()的返回值不是直接的字符串，需要先检查操作是否成功
    taihe::expected<taihe::string, taihe::error> firstResult = names.get(0);
    if (!firstResult.has_value()) {  // 判断获取操作是否失败
        return taihe::unexpected(std::move(firstResult.error()));
    }
    taihe::string firstName = std::move(*firstResult);

    // 同理，插入操作也需要通过返回值检查调用是否成功
    taihe::expected<void, taihe::error> insertResult = names.insert(1, name);
    if (!insertResult.has_value()) {  // 判断插入操作是否失败
        return taihe::unexpected(std::move(insertResult.error()));
    }

    return firstName;
}
```

该示例先读取第一个字符串，再在其后插入新字符串。调用成功时，函数会返回读取的第一个字符串。

在共享容器上的方法返回值均为`taihe::expected`类型，关于`taihe::expected`的使用细节可参考[使用Taihe进行异常相关开发](use-taihe-about-exception.md)，调用后必须检查返回结果是否成功，并在失败时进行相应处理。例如，在上面的例子里，如果原始数组为空，则`get(0)`就会返回访问越界错误，这里将错误直接继续传递给了ArkTS，所以在ArkTS会表现为抛出访问越界异常。同理，调用`insert()`后也必须根据返回结果检查调用是否成功。

当函数只需要继续传递错误时，可以使用`TH_TRY`宏来简化上面的写法：

```cpp
taihe::expected<taihe::string, taihe::error> insertAfterFirst(
    taihe::shared_vector_view<taihe::string> names,
    taihe::string_view name)
{
    // TH_TRY宏会自动完成错误检查，并在成功时返回解包后的值，失败时自动将错误继续传递到上层调用方
    taihe::string firstName = TH_TRY(names.get(0));
    TH_TRY(names.insert(1, name));
    return firstName;
}
```

`SharedVector<T>`提供的方法包括`getSize()`、`get()`、`set()`、`insert()`、`insertLast()`、`remove()`和`clear()`。此外，需要一次读取所有元素时，可调用`getItems()`取得`Array<T>`类型的快照，快照创建后不会随共享数组的后续修改自动更新。需要逐项处理时，可调用`forEachItem()`遍历所有元素。

**ArkTS侧使用**

```typescript
let names: Array<string> = ["Alice", "Bob"];
let firstName: string = shared_container_example.insertAfterFirst(names, "Carol");

console.info(firstName);
console.info(names);

let emptyNames: Array<string> = [];
try {
    shared_container_example.insertAfterFirst(emptyNames, "Carol");
} catch (e) {
    console.info(e);
}
```

**输出结果**

```text
Alice
Alice,Carol,Bob
Error: Out of bounds
```

## SharedMap

`SharedMap<K, V>`对应ArkTS侧的`Map<K, V>`。使用`@record SharedMap<K, V>`时，则对应ArkTS侧的`Record<K, V>`。

**Taihe声明**

```rust
function increaseExistingScore(scores: @record SharedMap<String, i32>, name: String, increment: i32): Optional<i32>;
```

**C++侧实现**

```cpp
#include <taihe/error.hpp>
#include <taihe/expected.hpp>
#include <taihe/shared_map.hpp>
#include <taihe/string.hpp>

taihe::expected<taihe::optional<int32_t>, taihe::error> increaseExistingScore(
    taihe::shared_map_view<taihe::string, int32_t> scores,
    taihe::string_view name,
    int32_t increment)
{
    // 调用tryGet()后，需要依次检查查询操作是否发生错误，以及是否取到了对应的值
    taihe::expected<taihe::optional<int32_t>, taihe::error> result = scores.tryGet(name);
    if (!result.has_value()) {  // 查询出错
        return taihe::unexpected(std::move(result.error()));
    }
    taihe::optional<int32_t> maybeOldScore = std::move(*result);
    if (!maybeOldScore.has_value()) {  // 查询成功，但查询的键不存在
        return taihe::optional<int32_t>();
    }

    int32_t oldScore = *maybeOldScore;
    int32_t newScore = oldScore + increment;
    taihe::expected<void, taihe::error> updateResult = scores.upsert(name, newScore);
    if (!updateResult.has_value()) {
        return taihe::unexpected(std::move(updateResult.error()));
    }
    return taihe::optional<int32_t>::make(newScore);
}
```

该示例的行为是，先在传入的映射中查找已经存在的用户积分，当且仅当用户已经存在时更新其积分并返回新积分，否则返回空值。

其中，需要注意`tryGet()`调用的返回值可能有三种情况：
- 查询操作出错时，`result.has_value()`为`false`；
- 查询成功但键不存在时，`result.has_value()`为`true`，但`*result`的值为空；
- 查询成功且键存在时，`**result`即为查询到的值。

仅需要继续传递错误时，也可使用`TH_TRY`简化错误处理：

```cpp
taihe::expected<taihe::optional<int32_t>, taihe::error> increaseExistingScoreSimplified(
    taihe::shared_map_view<taihe::string, int32_t> scores,
    taihe::string_view name,
    int32_t increment)
{
    // TH_TRY自动处理查询出错的情况，并将错误继续传递给上层调用方，因此只需要处理查询成功的两种情况即可
    taihe::optional<int32_t> maybeOldScore = TH_TRY(scores.tryGet(name));
    if (!maybeOldScore.has_value()) {
        return taihe::optional<int32_t>();
    }

    int32_t oldScore = *maybeOldScore;
    int32_t newScore = oldScore + increment;
    TH_TRY(scores.upsert(name, newScore));
    return taihe::optional<int32_t>(std::in_place, newScore);
}
```

`SharedMap<K, V>`提供的方法包括`getSize()`、`has()`、`tryGet()`、`upsert()`、`remove()`和`clear()`。`getKeys()`、`getValues()`和`getEntries()`分别返回键、值和键值对的普通数组快照，快照创建后不会随共享映射的后续修改自动更新。`forEachKey()`、`forEachValue()`和`forEachEntry()`可分别用于遍历键、值或键值对。

**ArkTS侧使用**

```typescript
let scores: Record<string, int> = { "Alice": 90 };
let aliceScore: int | undefined = shared_container_example.increaseExistingScore(scores, "Alice", 5);
let unknownScore: int | undefined = shared_container_example.increaseExistingScore(scores, "Bob", 5);

console.info("Alice score:", aliceScore);
console.info("Unknown score:", unknownScore);
console.info("scores:", scores);
```

**输出结果**

```text
Alice score: 95
Unknown score: undefined
scores: Alice,95
```

## SharedSet

`SharedSet<T>`对应ArkTS侧的`Set<T>`，用于保存不重复的元素。

**Taihe声明**

```rust
function insertTwo(tags: SharedSet<String>, first: String, second: String): i32;
```

**C++侧实现**

```cpp
#include <taihe/error.hpp>
#include <taihe/expected.hpp>
#include <taihe/shared_set.hpp>
#include <taihe/string.hpp>

taihe::expected<int32_t, taihe::error> insertTwo(
    taihe::shared_set_view<taihe::string> tags,
    taihe::string_view first,
    taihe::string_view second)
{
    int32_t count = 0;
    taihe::expected<bool, taihe::error> firstResult = tags.checkedInsert(first);
    if (!firstResult.has_value()) {
        return taihe::unexpected(std::move(firstResult.error()));
    }
    bool firstInserted = *firstResult;
    if (firstInserted) {
        ++count;
    }
    taihe::expected<bool, taihe::error> secondResult = tags.checkedInsert(second);
    if (!secondResult.has_value()) {
        return taihe::unexpected(std::move(secondResult.error()));
    }
    bool secondInserted = *secondResult;
    if (secondInserted) {
        ++count;
    }
    return count;
}
```

该示例使用`checkedInsert()`判断集合是否实际改变：成功调用后，返回`true`表示本次新增了元素，返回`false`表示元素原本已存在；调用失败将接收到的错误传递给ArkTS。

需要知道元素是否实际删除时，可使用`checkedRemove()`，返回`true`表示本次实际删除了元素，返回`false`表示元素原本不存在；调用失败时会接收到错误。

该示例同样可以使用`TH_TRY`宏简化错误处理。

```cpp
taihe::expected<int32_t, taihe::error> insertTwo(
    taihe::shared_set_view<taihe::string> tags,
    taihe::string_view first,
    taihe::string_view second)
{
    int32_t count = 0;
    bool firstInserted = TH_TRY(tags.checkedInsert(first));
    if (firstInserted) {
        ++count;
    }
    bool secondInserted = TH_TRY(tags.checkedInsert(second));
    if (secondInserted) {
        ++count;
    }
    return count;
}
```

`SharedSet<T>`提供的方法包括`getSize()`、`has()`、`insert()`、`checkedInsert()`、`remove()`、`checkedRemove()`和`clear()`。`getKeys()`返回集合元素的普通数组快照，快照创建后不会随共享集合的后续修改自动更新。`forEachKey()`可用于遍历集合所有元素。

**ArkTS侧使用**

```typescript
let tags: Set<string> = new Set<string>();
let firstAdded: int = shared_container_example.insertTwo(tags, "a", "b");
let secondAdded: int = shared_container_example.insertTwo(tags, "a", "c");

console.info("firstAdded:", firstAdded);
console.info("secondAdded:", secondAdded);
console.info("tags:", tags);
```

**输出结果**

```text
firstAdded: 2
secondAdded: 1
tags: Set[a,b,c]
```

## SharedArray

`SharedArray<T>`用于访问`ArrayBuffer`或TypedArray的连续数据。与其他共享容器不同，它提供了一些直接访问原始连续内存的底层接口，可直接使用下标、`data()`和范围`for`访问元素。

### 投影成ArrayBuffer

`@arraybuffer SharedArray<T>`在ArkTS侧投影为`ArrayBuffer`，其中`T`只能为`i8`或`u8`。需要使用其他数值类型时，应改用`@typedarray`。

**Taihe声明**

```rust
function setBytes(values: @arraybuffer SharedArray<u8>, value: u8);
```

**C++侧实现**

```cpp
#include <taihe/shared_array.hpp>

void setBytes(taihe::shared_array_view<uint8_t> values, uint8_t value)
{
    for (uint8_t &v : values) {
        v = value;
    }
}
```

**ArkTS侧使用**

```typescript
let values: ArrayBuffer = new ArrayBuffer(4);
shared_container_example.setBytes(values, 1);

// values现在为[1, 1, 1, 1]
console.info(values);
```

**输出结果**

```text
std.core.ArrayBuffer {data: [1, 1, 1, 1], byteLength: 4}
```


### 投影成TypedArray

`@typedarray SharedArray<T>`在ArkTS侧投影对应关系如下：

| Taihe元素类型 | ArkTS侧TypedArray |
| --- | --- |
| `i8` | `Int8Array` |
| `u8` | `Uint8Array` |
| `i16` | `Int16Array` |
| `u16` | `Uint16Array` |
| `i32` | `Int32Array` |
| `u32` | `Uint32Array` |
| `i64` | `BigInt64Array` |
| `u64` | `BigUint64Array` |
| `f32` | `Float32Array` |
| `f64` | `Float64Array` |

以下示例把`Int32Array`中的每个元素加一。

**Taihe声明**

```rust
function increment(values: @typedarray SharedArray<i32>);
```

**C++侧实现**

```cpp
#include <taihe/shared_array.hpp>

void increment(taihe::shared_array_view<int32_t> values)
{
    for (int32_t &value : values) {
        ++value;
    }
}
```

**ArkTS侧使用**

```typescript
let values: Int32Array = new Int32Array([1, 2, 3]);
shared_container_example.increment(values);

console.info(values);
```

**输出结果**

```text
2,3,4
```
