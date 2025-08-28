# 使用 Taihe 进行 Record 相关开发

## 简介

`Record` 是一种结构化数据类型，用来表示一个固定属性集合的对象类型，在 Taihe 中使用 `@record Map<K, V>` 表示。

## 基本概念

| Taihe 类型      | C++ 侧类型       | C++ 侧类型（作为参数时） |
| ------------------- | ------------------ | ------------------------ |
| `@record Map<K, V>` | `taihe::map<K, V>` | `taihe::map_view<K, V>`  |

在 ets 侧，`Record` 可用于将一种类型的属性映射到另一种类型。`Record` 对应 Taihe C++ 实现侧的 `taihe::map<K, V>`。

`map` 在 Taihe C++ 实现侧有 view 类型（视图类型）和非 view 类型（持有者类型），其中，view 类型的语义是不拥有所有权，只是对现有类型的引用，而非 view 类型则是拥有当前类型的所有权，用户可以根据使用场景来进行使用。

建议**只有**在**必须获取所有权**的情况下使用 `taihe::map<K, V>`，其他情况使用`taihe::map_view<K, V>`。

## 使用示例

接下来介绍使用 Taihe 进行 `Record` 开发的流程

示例代码功能：使用 `Record` 存储用户设置并获取某些设置项

### 在 Taihe 文件中声明

```rust
function getUserSetting(settings: @record Map<String, String>, key: String): String;
```

### C++ 侧 实现声明的接口

```cpp
taihe::string getUserSetting(taihe::map_view<taihe::string, taihe::string> settings, taihe::string_view key) {
  auto iter = settings.find_item(key);
  if (iter == nullptr) {
    return "undefined";  // Return "undefined" if the key is not found
  }
  return iter->second;
}
```

### 生成 `record.ets` 

```typescript
native function _taihe_getUserSetting_native(settings: Record<string, string>, key: string): string;
export function getUserSetting(settings: Record<string, string>, key: string): string {
    return _taihe_getUserSetting_native(settings, key);
}
function _taihe_getUserSetting_reverse(settings: Record<string, string>, key: string): string {
    return getUserSetting(settings, key);
}
```

### ets 侧使用

```typescript
// 初始化 Record
let Settings: Record<string, string> = {
    "theme": "dark",
    "fontSize": "14px",
    "language": "en-US",
};
// 查找设置
let setting1 = record.getUserSetting(Settings, "theme");
let setting2 = record.getUserSetting(Settings, "autosave");
console.log("theme: " + setting1);
console.log("autosave: " + setting2);

// 输出：
// theme: dark
// autosave: undefined
```

## C++ 侧 taihe::map<K, V> 介绍

`taihe::map<K, V>` 用于表示键值对映射集合，通过引用计数管理。它基于哈希表实现，故键值对的顺序并不保证。以下是 Taihe 在 C++ 实现侧提供的 `taihe::map<K, V>` 相关操作。

### 1. 创建

```cpp
#include <taihe/map.hpp>

// 创建空 map
taihe::map<taihe::string, int> map1;

map1.reserve(10);  // 支持预分配空间，避免频繁重新分配

size_t capacity = map1.capacity();  // 获取当前容量
```

### 2. 插入、查找与删除

```cpp
// 插入键值对
auto [it1, success1] = map1.emplace("apple", 5);
auto [it2, success2] = map1.emplace("banana", 3);

// 如果键已存在，emplace 不会覆盖
auto [it3, success3] = map1.emplace("apple", 10);  // success3 为 false

// 使用 emplace<true> 强制覆盖
auto [it4, success4] = map1.emplace<true>("apple", 10);  // 覆盖原值

// 查找键值对
auto it = map1.find_item("banana");
if (it != map1.end()) {
    std::cout << it->first << ": " << it->second << std::endl;
}

// 删除键值对
bool erased = map1.erase("apple");
```

***⚠️ 特别注意：当前请不要使用 `map` 对象的 `find` 方法，该方法返回 `V*` 而不是迭代器。这将在未来的版本中被修正，届时将导致之前使用 `find` 处产生不兼容，请使用 `find_item` 方法。***

### 3. 获取大小、遍历和清空

```cpp
// 获取大小
size_t size = map1.size();

// 遍历 map
for (auto it = map1.begin(); it != map1.end(); ++it) {
    const auto& [key, value] = *it;
    std::cout << key << " => " << value << std::endl;
}

for (const auto& [key, value] : map1) {
    std::cout << key << " => " << value << std::endl;
}

// 清空所有元素
map1.clear();

// 判断是否为空
bool is_empty = map1.empty();
```
