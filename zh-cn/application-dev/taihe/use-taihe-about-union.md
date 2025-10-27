# 使用 Taihe 进行 union 相关开发

## 简介

使用 Taihe 进行联合类型相关开发时，可以使用 union，实现在同一内存位置存放不同类型的数据。

## 基本概念

Taihe 相关代码示例

```rust
union MessageData {
    textVal: String;
    numVal: i64;
}
```

以下是对应的 ets 代码

```typescript
export type MessageData = string | long;
```

## 使用示例

### Taihe 声明

```rust
union MessageData {
    textVal: String;
    numVal: i64;
}
function checkMessageDataType(data: MessageData): String;
```

### C++ 实现

```cpp
::taihe::string checkMessageDataType(MessageData const& data) {
  // 判断传入的 MessageData 对象是字符串类型还是数字类型
  switch (data.get_tag()) {
  case MessageData::tag_t::textVal:
    std::cout << "data: " << *data.get_textVal_ptr() << std::endl;
    return "text";
  case MessageData::tag_t::numVal:
    std::cout << "data: " << *data.get_numVal_ptr() << std::endl;
    return "number";
  }
}
```

### ets 侧使用

```typescript
let result1 = checkMessageDataType("hello");
let result2 = checkMessageDataType(5);
console.log("show checkMessageDataType value type: " + result1);
console.log("show checkMessageDataType value type: " + result2);
```

Output：

```sh
show checkMessageDataType value type: text
show checkMessageDataType value type: number
```

## Union C++ 使用方法

介绍 C++ 实现中的 union

- 创建 union

  用户可以使用 `{union}::make_{union_item}({val})` 来构造 union，其中 val 为对应类型的变量，以示例 union 为例：

  ```cpp
  auto data_text = MessageData::make_textVal("str");
  auto data_num = MessageData::make_numVal(5);
  ```

- 读取 union 值

  用户可以使用 `get_{union_item}_ptr`，如果当前对象是指定的 union 项，则返回指向其数据的指针；否则返回空指针，以本例 union 为例：

  ```cpp
  ::taihe::string* s = data_text.get_textVal_ptr();
  long* l = data_num.get_numVal_ptr();
  ```
