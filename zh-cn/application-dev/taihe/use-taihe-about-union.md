# 使用Taihe进行union相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

使用Taihe进行联合类型相关开发时，可以使用union，实现在同一内存位置存放不同类型的数据。

## 基本概念

Taihe相关代码示例

```rust
union MessageData {
    textVal: String;
    numVal: i64;
}
```

以下是对应的ets代码

```typescript
export type MessageData = string | long;
```

## 使用示例

### Taihe声明

```rust
union MessageData {
    textVal: String;
    numVal: i64;
}
function checkMessageDataType(data: MessageData): String;
```

### C++实现

```cpp
::taihe::string checkMessageDataType(MessageData const& data) {
  // 判断传入的MessageData对象是字符串类型还是数字类型
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

### ets侧使用

```typescript
let result1 = checkMessageDataType("hello");
let result2 = checkMessageDataType(5);
console.info("show checkMessageDataType value type: " + result1);
console.info("show checkMessageDataType value type: " + result2);
```

Output：

```sh
show checkMessageDataType value type: text
show checkMessageDataType value type: number
```

## Union C++使用方法

介绍C++实现中的union

- 创建union

  用户可以使用`{union}::make_{union_item}({val})`来构造union，其中val为对应类型的变量，以示例union为例：

  ```cpp
  auto data_text = MessageData::make_textVal("str");
  auto data_num = MessageData::make_numVal(5);
  ```

- 读取union值

  用户可以使用`get_{union_item}_ptr`，如果当前对象是指定的union项，则返回指向其数据的指针；否则返回空指针，以本例union为例：

  ```cpp
  ::taihe::string* s = data_text.get_textVal_ptr();
  long* l = data_num.get_numVal_ptr();
  ```
