# TextDecoder

提供将字节数组解码为字符串的 API。支持多种格式，包括 UTF-8、UTF-16LE、UTF-16BE、ISO-8859 和 Windows-1251。

**起始版本：** 7

<!--Device-util-class TextDecoder--><!--Device-util-class TextDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

用于创建 **TextDecoder** 对象的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoder-constructor()--><!--Device-TextDecoder-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let textDecoder = new util.TextDecoder();
let retStr = textDecoder.encoding;
console.info('retStr = ' + retStr);
// 输出结果：retStr = utf-8

```

## constructor

```TypeScript
constructor(encoding?: string, options?: { fatal?: boolean; ignoreBOM?: boolean })
```

用于创建 **TextDecoder** 对象的构造函数。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [create](arkts-arkts-util-textdecoder-c.md#create)

<!--Device-TextDecoder-constructor(encoding?: string, options?: { fatal?: boolean; ignoreBOM?: boolean })--><!--Device-TextDecoder-constructor(encoding?: string, options?: { fatal?: boolean; ignoreBOM?: boolean })-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 编码格式。默认格式为 **'utf-8'**。 |
| options | { fatal?: boolean; ignoreBOM?: boolean } | 否 | 解码相关的选项，包含 **fatal** 和 **ignoreBOM**。 |

**示例：**

```TypeScript
let textDecoder = new util.TextDecoder("utf-8",{ignoreBOM: true});

```

## create

```TypeScript
static create(encoding?: string, options?: TextDecoderOptions): TextDecoder
```

创建一个 **TextDecoder** 对象。提供与已弃用的带参构造函数相同的功能。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoder-static create(encoding?: string, options?: TextDecoderOptions): TextDecoder--><!--Device-TextDecoder-static create(encoding?: string, options?: TextDecoderOptions): TextDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | 编码格式。默认格式为 **'utf-8'**。<br>**起始版本：** 11 |
| options | [TextDecoderOptions](arkts-arkts-util-textdecoderoptions-i.md) | 否 | 解码相关的选项，包含 **fatal** 和 **ignoreBOM**。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextDecoder](arkts-arkts-util-textdecoder-c.md) | 创建的 **TextDecoder** 对象。 |

**示例：**

```TypeScript
let textDecoderOptions: util.TextDecoderOptions = {
  fatal: false,
  ignoreBOM : true
}
let textDecoder = util.TextDecoder.create('utf-8', textDecoderOptions);
let retStr = textDecoder.encoding;
console.info('retStr = ' + retStr);
// 输出结果：retStr = utf-8

```

## decode

```TypeScript
decode(input: Uint8Array, options?: { stream?: false }): string
```

将输入内容解码为字符串。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [decodeToString](arkts-arkts-util-textdecoder-c.md#decodetostring)

<!--Device-TextDecoder-decode(input: Uint8Array, options?: { stream?: false }): string--><!--Device-TextDecoder-decode(input: Uint8Array, options?: { stream?: false }): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | Uint8Array | 是 | 要解码的 Uint8Array 对象。 |
| options | { stream?: false } | 否 | 解码相关的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 获取到的字符串。 |

**示例：**

```TypeScript
let textDecoder = new util.TextDecoder("utf-8",{ignoreBOM: true});
let uint8 = new Uint8Array(6);
uint8[0] = 0xEF;
uint8[1] = 0xBB;
uint8[2] = 0xBF;
uint8[3] = 0x61;
uint8[4] = 0x62;
uint8[5] = 0x63;
console.info("input num:");
let retStr = textDecoder.decode(uint8, {stream: false});
console.info("retStr = " + retStr);
// 输出结果：retStr = abc

```

## decodeToString

```TypeScript
decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string
```

将输入内容解码为字符串。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoder-decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string--><!--Device-TextDecoder-decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | Uint8Array | 是 | 要解码的 Uint8Array 对象。 |
| options | [DecodeToStringOptions](arkts-arkts-util-decodetostringoptions-i.md) | 否 | 解码相关的选项。默认值为 **undefined**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 获取到的字符串。 |

**示例：**

```TypeScript
// 当解析不含有\0的字节的示例代码
let textDecoderOptions: util.TextDecoderOptions = {
  fatal: false,
  ignoreBOM : true
}
let decodeToStringOptions: util.DecodeToStringOptions = {
  stream: false
}
let textDecoder = util.TextDecoder.create('utf-8', textDecoderOptions);
let uint8 = new Uint8Array([0xEF, 0xBB, 0xBF, 0x61, 0x62, 0x63]);
let retStr = textDecoder.decodeToString(uint8, decodeToStringOptions);
console.info("retStr = " + retStr);
// 输出结果：retStr = abc

```

```TypeScript
// 当解析含有\0的字节的示例代码
let textDecoderOptions: util.TextDecoderOptions = {
  fatal: false,
  ignoreBOM : true
}
let decodeToStringOptions: util.DecodeToStringOptions = {
  stream: false
}
let textDecoder = util.TextDecoder.create('utf-8', textDecoderOptions);
let uint8 = new Uint8Array([97, 98, 0, 99]);
let retStr = textDecoder.decodeToString(uint8, decodeToStringOptions);
console.info("retStr = " + retStr);
// 输出结果：retStr = abc
let retJson = JSON.stringify(retStr)
console.info("retJson = " + retJson);
// 输出结果：retJson = ab/u0000c

```

## decodeWithStream

```TypeScript
decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string
```

将输入内容解码为字符串。如果 **input** 是空数组，则返回 **undefined**。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [decodeToString](arkts-arkts-util-textdecoder-c.md#decodetostring)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoder-decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string--><!--Device-TextDecoder-decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | Uint8Array | 是 | 要解码的 Uint8Array 对象。 |
| options | [DecodeWithStreamOptions](arkts-arkts-util-decodewithstreamoptions-i.md) | 否 | 解码相关的选项。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 获取到的字符串。 |

**示例：**

```TypeScript
let textDecoderOptions: util.TextDecoderOptions = {
  fatal: false,
  ignoreBOM : true
}
let decodeWithStreamOptions: util.DecodeWithStreamOptions = {
  stream: false
}
let textDecoder = util.TextDecoder.create('utf-8', textDecoderOptions);
let uint8 = new Uint8Array(6);
uint8[0] = 0xEF;
uint8[1] = 0xBB;
uint8[2] = 0xBF;
uint8[3] = 0x61;
uint8[4] = 0x62;
uint8[5] = 0x63;
console.info("input num:");
let retStr = textDecoder.decodeWithStream(uint8, decodeWithStreamOptions);
console.info("retStr = " + retStr);
// 输出结果：retStr = abc

```

## encoding

```TypeScript
readonly encoding: string
```

编码格式。<br>支持的格式包括：utf-8、ibm866、iso-8859-2、iso-8859-3、iso-8859-4、iso-8859-5、iso-8859-6、iso-8859-7、iso-8859-8、iso-8859-8-i、iso-8859-10、iso-8859-13、iso-8859-14、iso-8859-15、koi8-r、koi8-u、macintosh、windows-874、windows-1250、windows-1251、windows-1252、windows-1253、windows-1254、windows-1255、windows-1256、windows-1257、windows-1258、x-mac-cyrillic、gbk、gb18030、big5、euc-jp、iso-2022-jp、shift_jis、euc-kr、utf-16be、utf-16le、gb2312 和 iso-8859-1。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoder-readonly encoding: string--><!--Device-TextDecoder-readonly encoding: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## fatal

```TypeScript
readonly fatal: boolean
```

是否显示致命错误。值为 **true** 表示显示致命错误，值为 **false** 表示相反的情况。

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoder-readonly fatal: boolean--><!--Device-TextDecoder-readonly fatal: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreBOM

```TypeScript
readonly ignoreBOM = false
```

是否忽略字节顺序标记（BOM）。默认值为 **false**，表示结果中包含 BOM。

**类型：** false

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoder-readonly ignoreBOM = false--><!--Device-TextDecoder-readonly ignoreBOM = false-End-->

**系统能力：** SystemCapability.Utils.Lang

