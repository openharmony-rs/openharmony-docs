# 使用Taihe进行String可选编码相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @k1ngqaquuu-->

## 简介

Taihe在C++侧默认将`String`类型投影为UTF-8编码的`taihe::string`和`taihe::string_view`。当C++侧需要明确使用UTF-16，或要接收上层语言原始编码的字符串，亦或是希望将可能为不同编码的字符串传递给上层时，可以在Taihe声明中通过`@encoding`类型注解指定字符串编码方式。

## 基本概念

`@encoding`只能标注在`String`类型上，可用于函数参数、返回值、数据结构成员和字段等。

| IDL中写法 | 对应编码 | C++侧持有类型 | C++侧临时借用类型 | 适用场景 |
| --- | --- | --- | --- | --- |
| `String`或`@encoding("utf-8") String` | `utf-8` | `taihe::string` | `taihe::string_view` | 默认场景 |
| `@encoding("utf-16") String` | `utf-16` | `taihe::u16string` | `taihe::u16string_view` | C++实现侧直接接收或返回UTF-16字符串 |
| `@encoding("common") String` | 不定 | `taihe::common_string` | `taihe::common_string_view` | 希望接收上层语言原始编码的字符串进行针对性处理，或希望将编码不定的字符串传递给上层 |

注解只影响传递到C++侧的字符串编码方式，而不会改变ETS侧的字符串类型，ETS侧始终对应`string`。

## 使用示例

下面的函数将字符串原样返回，分别演示默认UTF-8和UTF-16的声明方式，并展示常用的C++字符串操作。

### Taihe文件中声明

```rust
// 默认使用UTF-8
function echoUtf8(value: String): String;

// 明确使用UTF-16
function echoUtf16(value: @encoding("utf-16") String): @encoding("utf-16") String;
```

### C++侧实现

```cpp
#include <taihe/string.hpp>

taihe::string echoUtf8(taihe::string_view value)
{
    // UTF-8的size()返回字节数，而不是字符数
    std::size_t byteCount = value.size();
    std::cout << "UTF-8 byte count: " << byteCount << std::endl;
    std::cout << "UTF-8 bytes: ";
    for (char c : value) {
        std::cout << static_cast<int>(c) << ',';
    }
    std::cout << std::endl;
    return value;
}

taihe::u16string echoUtf16(taihe::u16string_view value)
{
    // UTF-16的size()返回char16_t代码单元数
    std::size_t codeUnitCount = value.size();
    std::cout << "UTF-16 code unit count: " << codeUnitCount << std::endl;
    std::cout << "UTF-16 code units: ";
    for (char16_t c : value) {
        std::cout << static_cast<int>(c) << ',';
    }
    std::cout << std::endl;
    return value;
}
```

对于UTF-8字符串，`size()`返回字节数；对于UTF-16字符串，`size()`返回`char16_t`代码单元数。此外，`taihe::string`和`taihe::u16string`（以及对应的view类型）也都提供`empty()`、`data()`、下标访问、`at()`和范围`for`遍历等操作。

### ETS侧使用

```typescript
let s: string = "Taihe 你好";
let utf8: string = string_example.echoUtf8(s);
let utf16: string = string_example.echoUtf16(s);

console.info("UTF-8 result:", utf8);
console.info("UTF-16 result:", utf16);
```

### 输出结果

```text
UTF-8 byte count: 12
UTF-8 bytes: 84,97,105,104,101,32,-28,-67,-96,-27,-91,-67,
UTF-16 code unit count: 8
UTF-16 code units: 84,97,105,104,101,32,20320,22909,
UTF-8 result: Taihe 你好
UTF-16 result: Taihe 你好
```

## 不定编码

使用`@encoding("common") String`表示字符串的编码不固定，可以是UTF-8或UTF-16。

### 判断和转换编码

`common_string`可用于接收上层语言原始编码的字符串，所以内部保存的字符串的具体编码是不确定的。需要在运行期通过`is_utf8()`、`is_utf16()`或`encoding()`动态判断编码类型，然后根据检查结果选择合适的处理方式。

在判断编码后，可以转换为特定编码的**临时借用类型**，以便在后续处理中使用。例如，确认字符串为UTF-8后，可以将其转换为`taihe::string_view`；确认字符串为UTF-16后，可以将其转换为`taihe::u16string_view`。转换为临时借用类型的操作不会真正转换字符串的内容，因此当编码不匹配时会直接抛出异常，所以使用者在转换前必须确保编码匹配。

```cpp
void handleCommonString(taihe::common_string_view value)
{
    if (value.is_utf8()) {
        taihe::string_view utf8(value);
        std::cout << "UTF-8 byte count: " << utf8.size() << std::endl;
    } else if (value.is_utf16()) {
        taihe::u16string_view utf16(value);
        std::cout << "UTF-16 code unit count: " << utf16.size() << std::endl;
    }
}
```

转换为特定编码的**持有类型**时，如果编码不匹配，会在运行时动态创建目标编码的字符串；因此可以用于需要统一编码的场景：

```cpp
taihe::u16string toUtf16(taihe::common_string_view value)
{
    // value为UTF-16时，会直接拷贝原始字符串
    // value为UTF-8时，会在运行期转换为UTF-16并返回新的字符串
    return taihe::u16string(value);
}
```

同理，使用`taihe::string(value)`可以将任意编码的字符串转换为UTF-8字符串。不过这种使用场景在实际开发中通常是没有必要的，如果确定最后需要某种特定编码的字符串，更建议的是直接在IDL中声明要接收对应编码的字符串类型。

## 返回不定编码的字符串

`taihe::string`，`taihe::u16string`以及它们各自的view类型都可以隐式转换为`taihe::common_string`或`taihe::common_string_view`。另外，`taihe::common_string`也可以直接通过`const char*`或`const char16_t*`构造。因此，当使用`@encoding("common") String`作为返回类型时，可以直接返回任意编码的字符串：

```cpp
enum class Language {
    English,
    Chinese,
};

taihe::common_string createCommonString(Language lang)
{
    switch (lang) {
        case Language::English:
            return "Hello";  // 返回UTF-8编码的字符串
        case Language::Chinese:
            return u"你好";  // 返回UTF-16编码的字符串
        default:
            return "";
    }
}
```
