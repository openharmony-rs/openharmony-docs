# @ohos.util

util模块提供常用工具函数， 如用于字符串编码和解码的TextEncoder和TextDecoder， 用于有理数运算的RationalNumber8+， 用于缓存管理的LRUCache9+， 用于范围判定的ScopeHelper9+， 用于Base64编码和解码的Base64Helper9+， 用于内置对象类型检查的types8+， 以及方法的替代实现。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare namespace util--><!--Device-unnamed-declare namespace util-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [callbackWrapper](arkts-na-util-callbackwrapper-f.md) | Takes an async function (or a function that returns a Promise) and returns a function following the error-first callback style. |
| [errnoToString](arkts-na-util-errnotostring-f.md) | Get the string name of the system errno. |
| [format](arkts-na-util-format-f.md) | %s: 用于转换除BigInt、Object和-0之外的所有值。BigInt值将以n表示，没有用户定义toString函数的对象使用util.inspect()检查， 选项为{ depth: 0, colors: false, compact: 3 }。 %d: 用于转换除BigInt和Symbol之外的所有值。 %i: 对除BigInt和Symbol之外的所有值使用parseInt(value, 10)。 %f: 对除BigInt和Symbol之外的所有值使用parseFloat(value)。 %j: JSON。如果参数包含循环引用，则替换为字符串'[Circular]'。 %o: Object。对象的通用JavaScript对象格式字符串表示。类似于 util.inspect()，选项为{ showHidden: true, showProxy: true}。这将显示完整对象，包括 不可枚举属性和代理。 %O: Object。对象的通用JavaScript对象格式字符串表示。 %O: Object。对象的通用JavaScript对象格式字符串表示。类似于 util.inspect()，没有选项。这将显示完整对象，不包括不可枚举属性和 代理。 %c: CSS。此说明符被忽略，将跳过传入的任何CSS。 %%: 单个百分号('%')。这不会消耗参数。返回：&lt;string&gt; 格式化的字符串。 |
| [generateRandomBinaryUUID](arkts-na-util-generaterandombinaryuuid-f.md) | Generate a random RFC 4122 version 4 binary UUID using a cryptographically secure random number generator. |
| [generateRandomUUID](arkts-na-util-generaterandomuuid-f.md) | 使用加密安全的随机数生成器生成随机的RFC 4122版本4 UUID。 |
| [getHash](arkts-na-util-gethash-f.md) | Get the hash code of an object. |
| [getMainThreadStackTrace](arkts-na-util-getmainthreadstacktrace-f.md) | Get stack trace of main thread. |
| [parseUUID](arkts-na-util-parseuuid-f.md) | Parse a UUID from the string standard representation as described in the RFC 4122 version 4. |
| [promisify](arkts-na-util-promisify-f.md) | Takes a function following the common error-first callback style, i.e taking an (err, value) => callback as the last argument, and return a function that returns promises. |

### 类

| 名称 | 说明 |
| --- | --- |
| [Base64Helper](arkts-na-util-base64helper-c.md) | 使用Base64编码方案将Base64编码的字符串或输入的u8数组解码为新分配的u8数组。 |
| [LRUCache](arkts-na-util-lrucache-c.md) | Provides APIs to discard the least recently used data to make rooms for new elements when the cache is full. This class uses the Least Recently Used (LRU) algorithm, which believes that the recently used data may be accessed again in the near future and the least accessed data is the least valuable data and should be removed from the cache. |
| [RationalNumber](arkts-na-util-rationalnumber-c.md) | The rational number is mainly to compare rational numbers and obtain the numerator and denominator. |
| [ScopeHelper](arkts-na-util-scopehelper-c.md) | Provides APIs to define the valid range of a field. The constructor of this class creates comparable objects with lower and upper limits. |
| [StringDecoder](arkts-na-util-stringdecoder-c.md) | Provide the ability to decode binary streams into strings. The supported encoding types include: utf-8, iso-8859-2, koi8-r, macintosh, windows-1250, windows-1251, gbk, gb18030, big5, utf-16be, utf-16 le, etc. |
| [TextDecoder](arkts-na-util-textdecoder-c.md) | The TextDecoder represents a text decoder that accepts a string as input, decodes it in UTF-8 format, and outputs UTF-8 byte stream. |
| [TextEncoder](arkts-na-util-textencoder-c.md) | The TextEncoder interface represents a text encoder. The encoder takes the byte stream as the input and outputs the String string. |
| [types](arkts-na-util-types-c.md) | Check the type of parameter. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DecodeToStringOptions](arkts-na-util-decodetostringoptions-i.md) | Defines the decode with stream related options parameters. |
| [EncodeIntoUint8ArrayInfo](arkts-na-util-encodeintouint8arrayinfo-i.md) | Return encoded text. |
| [ScopeComparable](arkts-na-util-scopecomparable-i.md) | The ScopeComparable contains comparison methods. |
| [TextDecoderOptions](arkts-na-util-textdecoderoptions-i.md) | Defines the TextDecoder related options parameters. |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Type](arkts-na-util-type-e.md) | Type表示base64的四种不同编码格式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [PromisifiedFunc](arkts-na-util-promisifiedfunc-t.md) | The type of promisify return function |
| [ScopeType](arkts-na-util-scopetype-t.md) | A type used to denote ScopeComparable or number. |

