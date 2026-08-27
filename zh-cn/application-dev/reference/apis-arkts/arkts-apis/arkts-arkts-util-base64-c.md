# Base64

将包含 Base64 数据的字符串或 Uint8Array 解码为重新分配的 Uint8Array。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Base64Helper](arkts-arkts-util-base64helper-c.md)

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

用于创建 **Base64** 对象的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [constructor](arkts-arkts-util-base64helper-c.md#constructor)

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
let textDecoder = new util.TextDecoder();
let retStr = textDecoder.encoding;
console.info('retStr = ' + retStr);
// 输出结果：retStr = utf-8
```

```TypeScript
let textEncoder = new util.TextEncoder();
```

```TypeScript
let rationalNumber = new util.RationalNumber();
```

```TypeScript
let base64 = new util.Base64Helper();
```

```TypeScript
let type = new util.types();
```

```TypeScript
let base64 = new  util.Base64();
```

## decode

```TypeScript
decode(src: Uint8Array | string): Promise<Uint8Array>
```

将输入内容解码为 Uint8Array 对象。该接口使用 promise 返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [decode](arkts-arkts-util-base64helper-c.md#decode)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array \| string | 是 | 要解码的 Uint8Array 对象或字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Uint8Array & gt; | 用于返回获取到的 Uint8Array 对象的 promise。 |

**示例**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([99,122,69,122]);
base64.decode(array).then((val) => {
  console.info(val.toString());
  // 输出结果：115,49,51
})
```

## decodeSync

```TypeScript
decodeSync(src: Uint8Array | string): Uint8Array
```

将输入内容解码为 Uint8Array 对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [decodeSync](arkts-arkts-util-base64helper-c.md#decodesync)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array \| string | 是 | 要解码的 Uint8Array 对象或字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 获取到的 Uint8Array 对象。 |

**示例**

```TypeScript
let base64 = new util.Base64();
let buff = 'czEz';
let result = base64.decodeSync(buff);
console.info("result = " + result);
// 输出结果：result = 115,49,51
```

## encode

```TypeScript
encode(src: Uint8Array): Promise<Uint8Array>
```

将输入内容编码为 Uint8Array 对象。该接口使用 promise 返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [encode](arkts-arkts-util-base64helper-c.md#encode)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Uint8Array & gt; | 用于返回获取到的 Uint8Array 对象的 promise。 |

**示例**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([115,49,51]);
base64.encode(array).then((val) => {
  console.info(val.toString());
  // 输出结果：99,122,69,122
})
```

## encodeSync

```TypeScript
encodeSync(src: Uint8Array): Uint8Array
```

对输入的 Uint8Array 字节数组进行 Base64 编码，并返回编码后的 Uint8Array。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [encodeSync](arkts-arkts-util-base64helper-c.md#encodesync)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 获取到的 Uint8Array 对象。 |

**示例**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([115,49,51]);
let result = base64.encodeSync(array);
console.info("result = " + result);
// 输出结果：result = 99,122,69,122
```

## encodeToString

```TypeScript
encodeToString(src: Uint8Array): Promise<string>
```

将输入内容编码为字符串。该接口使用 promise 返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [encodeToString](arkts-arkts-util-base64helper-c.md#encodetostring)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | 用于返回获取到的字符串的 promise。 |

**示例**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([115,49,51]);
base64.encodeToString(array).then((val) => {
    console.info(val);
    // 输出结果：czEz
})
```

## encodeToStringSync

```TypeScript
encodeToStringSync(src: Uint8Array): string
```

对输入的 Uint8Array 字节数组进行 Base64 编码，并返回编码后的字符串。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [encodeToStringSync](arkts-arkts-util-base64helper-c.md#encodetostringsync)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 获取到的字符串。 |

**示例**

```TypeScript
let base64 = new util.Base64();
let array = new Uint8Array([115,49,51]);
let result = base64.encodeToStringSync(array);
console.info("result = " + result);
// 输出结果：result = czEz
```
