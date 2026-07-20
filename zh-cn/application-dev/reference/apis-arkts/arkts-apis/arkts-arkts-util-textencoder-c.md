# TextEncoder

提供将字符串编码为字节数组的 API。支持多种编码格式。使用 **TextEncoder** 进行编码时，每个字符所占用的字节数因编码格式而异。必须显式指定编码格式以获取所需的编码结果。

**起始版本：** 7

<!--Device-util-class TextEncoder--><!--Device-util-class TextEncoder-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

用于创建 **TextEncoder** 对象的构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextEncoder-constructor()--><!--Device-TextEncoder-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let textEncoder = new util.TextEncoder();

```

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(encoding?: string)
```

用于创建 **TextEncoder** 对象的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextEncoder-constructor(encoding?: string)--><!--Device-TextEncoder-constructor(encoding?: string)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 编码格式。默认格式为 **'utf-8'**。 |

**示例：**

```TypeScript
let textEncoder = new util.TextEncoder("utf-8");

```

<a id="create"></a>
## create

```TypeScript
static create(encoding?: string): TextEncoder
```

创建一个 **TextEncoder** 对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextEncoder-static create(encoding?: string): TextEncoder--><!--Device-TextEncoder-static create(encoding?: string): TextEncoder-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 编码格式。默认格式为 **'utf-8'**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextEncoder](arkts-arkts-util-textencoder-c.md) | **TextEncoder** 对象。 |

**示例：**

```TypeScript
let textEncoder = util.TextEncoder.create("utf-8");

```

<a id="encode"></a>
## encode

```TypeScript
encode(input?: string): Uint8Array
```

将输入内容编码为 Uint8Array 对象。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** encodeInto

<!--Device-TextEncoder-encode(input?: string): Uint8Array--><!--Device-TextEncoder-encode(input?: string): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | string | 否 | 要编码的字符串。默认值为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 获取到的 Uint8Array 对象。 |

**示例：**

```TypeScript
let textEncoder = new util.TextEncoder();
let result = textEncoder.encode("\uD800¥¥");
console.info("result = " + result);
// 输出结果: result = 237,160,128,194,165,194,165

```

<a id="encodeinto"></a>
## encodeInto

```TypeScript
encodeInto(input?: string): Uint8Array
```

将输入内容编码为 Uint8Array 对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextEncoder-encodeInto(input?: string): Uint8Array--><!--Device-TextEncoder-encodeInto(input?: string): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | string | 否 | 要编码的字符串。默认值为空字符串。如果输入参数为空字符串，则返回值为 undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 获取到的 Uint8Array 对象。 |

**示例：**

```TypeScript
let textEncoder = new util.TextEncoder();
let result = textEncoder.encodeInto("\uD800¥¥");
console.info("result = " + result);
// 输出结果: result = 237,160,128,194,165,194,165

```

<a id="encodeinto-1"></a>
## encodeInto

```TypeScript
encodeInto(input: string, dest: Uint8Array): { read: number; written: number }
```

将生成的 UTF-8 编码文本写入到数组中。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [encodeIntoUint8Array](arkts-arkts-util-textencoder-c.md#encodeintouint8array-1)

<!--Device-TextEncoder-encodeInto(input: string, dest: Uint8Array): { read: number; written: number }--><!--Device-TextEncoder-encodeInto(input: string, dest: Uint8Array): { read: number; written: number }-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | string | 是 | 要编码的字符串。 |
| dest | Uint8Array | 是 | 用于存储 UTF-8 编码文本的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| { read: number; written: number } | 获取到的对象。**read** 表示已编码的字符数，**written** 表示已编码字符所占用的字节数。 |

**示例：**

```TypeScript
let textEncoder = new util.TextEncoder();
let buffer = new ArrayBuffer(4);
let uint8 = new Uint8Array(buffer);
let result = textEncoder.encodeInto('abcd', uint8);
console.info("uint8 = " + uint8);
// 输出结果: uint8 = 97,98,99,100

```

<a id="encodeintouint8array"></a>
## encodeIntoUint8Array

```TypeScript
encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo
```

对输入内容进行编码，并将结果存储到 Uint8Array 对象中。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextEncoder-encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo--><!--Device-TextEncoder-encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | string | 是 | 要编码的字符串。 |
| dest | Uint8Array | 是 | 用于存储 UTF-8 编码文本的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| object | 返回该对象，其中 read 表示已编码的字符数，written 表示已编码字符所占用的字节数。<br>**适用版本：** 9 - 10 |
| [EncodeIntoUint8ArrayInfo](arkts-arkts-util-encodeintouint8arrayinfo-i.md) | 获取到的对象。**read** 表示已编码的字符数，**written** 表示已编码字符所占用的字节数。<br>**适用版本：** 11+ |

**示例：**

```TypeScript
let textEncoder = new util.TextEncoder();
let buffer = new ArrayBuffer(4);
let uint8 = new Uint8Array(buffer);
let result = textEncoder.encodeIntoUint8Array('abcd', uint8);
console.info("uint8 = " + uint8);
// 输出结果: uint8 = 97,98,99,100
console.info("result.read = " + result.read);
// 输出结果: result.read = 4
console.info("result.written = " + result.written);
// 输出结果: result.written = 4

```

## encoding

```TypeScript
readonly encoding = 'utf-8'
```

编码格式。<br>支持的格式包括：utf-8、gb2312、gb18030、ibm866、iso-8859-1、iso-8859-2、iso-8859-3、iso-8859-4、iso-8859-5、iso-8859-6、iso-8859-7、iso-8859-8、iso-8859-8-i、iso-8859-10、iso-8859-13、iso-8859-14、iso-8859-15、koi8-r、koi8-u、macintosh、windows-874、windows-1250、windows-1251、windows-1252、windows-1253、windows-1254、windows-1255、windows-1256、windows-1257、windows-1258、gbk、big5、euc-jp、iso-2022-jp、shift_jis、euc-kr、x-mac-cyrillic、utf-16be 和 utf-16le。<br>默认值为 **'utf-8'**。

**类型：** 'utf-8'

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextEncoder-readonly encoding = 'utf-8'--><!--Device-TextEncoder-readonly encoding = 'utf-8'-End-->

**系统能力：** SystemCapability.Utils.Lang

