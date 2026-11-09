# Base64Helper

```TypeScript
class Base64Helper
```

提供 Base64 和 Base64URL 的编解码。Base64 编码表包含 64 个字符，分别为大写字母（A-Z）、小写字母（a-z）、数字（0-9）以及特殊字符加号（+）和斜杠（/）。编码时，原始数据按三个字节一组进行划分，每组转换为多个 6 位数字。然后使用 Base64编码表中对应的字符来表示这些数字。如果最后一组只包含一个或两个字节，则使用等号（=）进行填充。Base64URL 编码表包含64 个字符，分别为大写字母（A-Z）、小写字母（a-z）、数字（0-9）以及特殊字符连字符（-）和下划线（_）。Base64URL 编码结果不包含等号（=）。

**起始版本：** 9

<!--Device-util-class Base64Helper--><!--Device-util-class Base64Helper-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

Base64Helper的构造函数，创建一个用于Base64编解码的Base64Helper实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Base64Helper-constructor()--><!--Device-Base64Helper-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
let base64 = new util.Base64Helper();
```

## decode

```TypeScript
decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>
```

将输入参数异步解码后输出对应Uint8Array对象。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Base64Helper-decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>--><!--Device-Base64Helper-decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array &#124; string | 是 | 异步解码输入Uint8Array对象或者字符串。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 从API version 10开始支持该参数，表示对应的解码格式。<br>此参数可选，可选值为：util.Type.BASIC，util.Type.MIME，util.Type.BASIC_URL_SAFE和util.Type.MIME_URL_SAFE，默认值为：util.Type.BASIC。<br>- 当参数取值为util.Type.BASIC时，表示Base64解码。<br>- 当参数取值为util.Type.MIME时，表示Base64解码，src入参包含回车符、换行符。<br>- 当参数取值为util.Type.BASIC_URL_SAFE，表示Base64URL解码。<br>- 当参数取值为util.Type.MIME_URL_SAFE，表示Base64URL解码，src入参包含回车符、换行符。<br>**适用版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 返回异步解码后新分配的Uint8Array对象。 |

**示例**

```TypeScript
let base64Helper = new util.Base64Helper();
let array = 'TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz\r\naW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl\r\naGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=\r\n';
base64Helper.decode(array, util.Type.MIME).then((val) => {
  console.info(val.toString());
  /*
  输出结果：77,97,110,105,115,100,105,115,116,105,110,103,117,105,115,104,101,100,110,111,116,111,110,108,121,98,121,104,105,115,114,101,97,115,111,110,98,117,116,98,121,116,104,105,115,115,105,110,103,117,108,97,114,112,97,115,115,105,111,110,102,114,111,109,111,116,104,101,114,97,110,105,109,97,108,115,119,104,105,99,104,105,115,97,108,117,115,116,111,102,116,104,101,109,105,110,100,101,120,99,101,101,100,115,116,104,101,115,104,111,114,116,118,101,104,101,109,101,110,99,101,111,102,97,110,121,99,97,114,110,97,108,112,108,101,97,115,117,114,101
   */
})
```

## decodeSync

```TypeScript
decodeSync(src: Uint8Array | string, options?: Type): Uint8Array
```

将输入参数解码后输出对应Uint8Array对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Base64Helper-decodeSync(src: Uint8Array | string, options?: Type): Uint8Array--><!--Device-Base64Helper-decodeSync(src: Uint8Array | string, options?: Type): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array &#124; string | 是 | 待解码的Uint8Array对象或者字符串。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 从API version 10开始支持该参数，表示对应的解码格式。<br>此参数可选，可选值为：util.Type.BASIC，util.Type.MIME，util.Type.BASIC_URL_SAFE和util.Type.MIME_URL_SAFE，默认值为：util.Type.BASIC。<br>- 当参数取值为util.Type.BASIC，表示Base64解码。<br>- 当参数取值为util.Type.MIME，表示Base64解码，src入参包含回车符、换行符。<br>- 当参数取值为util.Type.BASIC_URL_SAFE，表示Base64URL解码。<br>- 当参数取值为util.Type.MIME_URL_SAFE，表示Base64URL解码，src入参包含回车符、换行符。<br>**适用版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回解码后新分配的Uint8Array对象。 |

**示例**

```TypeScript
let base64Helper = new util.Base64Helper();
let buff = 'TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz\r\naW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl\r\naGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=\r\n';
let result = base64Helper.decodeSync(buff, util.Type.MIME);
console.info("result = " + result);
/*
输出结果：result = 77,97,110,105,115,100,105,115,116,105,110,103,117,105,115,104,101,100,110,111,116,111,110,108,121,98,121,104,105,115,114,101,97,115,111,110,98,117,116,98,121,116,104,105,115,115,105,110,103,117,108,97,114,112,97,115,115,105,111,110,102,114,111,109,111,116,104,101,114,97,110,105,109,97,108,115,119,104,105,99,104,105,115,97,108,117,115,116,111,102,116,104,101,109,105,110,100,101,120,99,101,101,100,115,116,104,101,115,104,111,114,116,118,101,104,101,109,101,110,99,101,111,102,97,110,121,99,97,114,110,97,108,112,108,101,97,115,117,114,101
 */
```

## encode

```TypeScript
encode(src: Uint8Array, options?: Type): Promise<Uint8Array>
```

将输入参数异步编码后输出对应Uint8Array对象。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Base64Helper-encode(src: Uint8Array, options?: Type): Promise<Uint8Array>--><!--Device-Base64Helper-encode(src: Uint8Array, options?: Type): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 待编码Uint8Array对象。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 从API version 12开始支持该参数，表示对应的编码格式。<br>此参数可选，可选值为：util.Type.BASIC和util.Type.BASIC_URL_SAFE，默认值为：util.Type.BASIC。<br>util.Type.BASIC表示Base64编码。<br>util.Type.BASIC_URL_SAFE表示Base64URL编码。<br>**适用版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象。编码成功时resolve为新分配的Uint8Array对象，编码失败时reject为错误对象。 |

**示例**

```TypeScript
let base64Helper = new util.Base64Helper();
let array = new Uint8Array([115,49,51]);
base64Helper.encode(array).then((val) => {
  console.info(val.toString());
  // 输出结果：99,122,69,122
})
```

## encodeSync

```TypeScript
encodeSync(src: Uint8Array, options?: Type): Uint8Array
```

通过输入参数编码后输出Uint8Array对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Base64Helper-encodeSync(src: Uint8Array, options?: Type): Uint8Array--><!--Device-Base64Helper-encodeSync(src: Uint8Array, options?: Type): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 待编码的Uint8Array对象。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 从API version 12开始支持该参数，表示对应的编码格式。<br>此参数可选，可选值为：util.Type.BASIC和util.Type.BASIC_URL_SAFE，默认值为：util.Type.BASIC。<br>util.Type.BASIC表示Base64编码。<br>util.Type.BASIC_URL_SAFE表示Base64URL编码。<br>**适用版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回编码后的Uint8Array对象。 |

**示例**

```TypeScript
let base64Helper = new util.Base64Helper();
let array = new Uint8Array([115,49,51]);
let result = base64Helper.encodeSync(array);
console.info("result = " + result);
// 输出结果：result = 99,122,69,122
```

## encodeToString

```TypeScript
encodeToString(src: Uint8Array | collections.Uint8Array, options?: Type): Promise<string>
```

将输入参数异步编码后输出对应文本。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Base64Helper-encodeToString(src: Uint8Array | collections.Uint8Array, options?: Type): Promise<string>--><!--Device-Base64Helper-encodeToString(src: Uint8Array | collections.Uint8Array, options?: Type): Promise<string>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array &#124; [collections.Uint8Array](arkts-arkts-collections-uint8array-c.md) | 是 | 异步编码输入的Uint8Array对象。<br>**说明：** 从API version 26.1.0开始，支持传入collections.Uint8Array（Sendable字节数组），可直接编码跨并发实例（TaskPool/Worker）传递的字节数据，无需先拷贝为普通Uint8Array。<br>**适用版本：** 26.1.0 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 从API version 10开始支持该参数，表示对应的编码格式。<br>此参数可选，可选值为：util.Type.BASIC，util.Type.MIME，util.Type.BASIC_URL_SAFE和util.Type.MIME_URL_SAFE，默认值为：util.Type.BASIC。<br>- 当参数取值为util.Type.BASIC，表示Base64编码，返回值没有回车符、换行符。<br>- 当参数取值为util.Type.MIME，表示Base64编码，返回值每一行不超过76个字符，而且每行以'\r\n'符结束。<br>- 当参数取值为util.Type.BASIC_URL_SAFE，表示Base64URL编码，返回值没有回车符、换行符。<br>- 当参数取值为util.Type.MIME_URL_SAFE，表示Base64URL编码，返回值每一行不超过76个字符，而且每行以'\r\n'符结束。<br>**适用版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。编码成功时resolve为Base64编码后的字符串，编码失败时reject为错误对象。 |

**示例**

```TypeScript
import { util, collections } from '@kit.ArkTS';
let base64Helper = new util.Base64Helper();
let array = new Uint8Array([77,97,110,105,115,100,105,115,116,105,110,103,117,105,115,104,101,100,110,111,116,111,110,108,121,98,121,104,105,115,114,101,97,115,111,110,98,117,116,98,121,116,104,105,115,115,105,110,103,117,108,97,114,112,97,115,115,105,111,110,102,114,111,109,111,116,104,101,114,97,110,105,109,97,108,115,119,104,105,99,104,105,115,97,108,117,115,116,111,102,116,104,101,109,105,110,100,101,120,99,101,101,100,115,116,104,101,115,104,111,114,116,118,101,104,101,109,101,110,99,101,111,102,97,110,121,99,97,114,110,97,108,112,108,101,97,115,117,114,101]);
base64Helper.encodeToString(array, util.Type.MIME).then((val) => {
  console.info(val);
  /*
  输出结果：TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz
  aW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl
  aGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=
   */

})

// 从API version 26.1.0开始，支持传入collections.Uint8Array（Sendable字节数组）
let base64Helper = new util.Base64Helper();
let sendableArray = new collections.Uint8Array([77, 97, 110]);
base64Helper.encodeToString(sendableArray, util.Type.BASIC).then((val) => {
  console.info(val);
  /*
  输出结果：TWFu
   */
});
```

## encodeToStringSync

```TypeScript
encodeToStringSync(src: Uint8Array | collections.Uint8Array, options?: Type): string
```

将输入的Uint8Array字节数组进行Base64编码，返回一个字符串结果。该方法支持多种编码格式，包括标准Base64编码、MIME格式的Base64编码（带有换行符）、URL安全格式的Base64编码等。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Base64Helper-encodeToStringSync(src: Uint8Array | collections.Uint8Array, options?: Type): string--><!--Device-Base64Helper-encodeToStringSync(src: Uint8Array | collections.Uint8Array, options?: Type): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array &#124; [collections.Uint8Array](arkts-arkts-collections-uint8array-c.md) | 是 | 待编码的Uint8Array对象。<br>**说明：** 从API version 26.1.0开始，支持传入collections.Uint8Array（Sendable字节数组），可直接编码跨并发实例（TaskPool/Worker）传递的字节数据，无需先拷贝为普通Uint8Array。<br>**适用版本：** 26.1.0 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 从API version 10开始支持该参数，表示对应的编码格式。<br>此参数可选，可选值为：util.Type.BASIC，util.Type.MIME，util.Type.BASIC_URL_SAFE 和util.Type.MIME_URL_SAFE，默认值为：util.Type.BASIC。<br>- 当参数取值为util.Type.BASIC，表示Base64编码，返回值没有回车符、换行符。<br>- 当参数取值为util.Type.MIME，表示使用Base64编码。如果返回值超过76个字符，则会在每76个字符处进行换行，并以'\r\n'结束每行。如果返回值少于76个字符，则会抛出异常。<br>- 当参数取值为util.Type.BASIC_URL_SAFE，表示Base64URL编码，返回值没有回车符、换行符。<br>- 当参数取值为util.Type.MIME_URL_SAFE，表示Base64URL编码，返回值每一行不超过76个字符，而且每行以'\r\n'符结束。<br>**适用版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回编码后的字符串。 |

**示例**

```TypeScript
import { util, collections } from '@kit.ArkTS';
// MIME编码
let base64Helper = new util.Base64Helper();
let array =
  new Uint8Array([77, 97, 110, 105, 115, 100, 105, 115, 116, 105, 110, 103, 117, 105, 115, 104, 101, 100, 110, 111, 116,
    111, 110, 108, 121, 98, 121, 104, 105, 115, 114, 101, 97, 115, 111, 110, 98, 117, 116, 98, 121, 116, 104, 105, 115,
    115, 105, 110, 103, 117, 108, 97, 114, 112, 97, 115, 115, 105, 111, 110, 102, 114, 111, 109, 111, 116, 104, 101,
    114, 97, 110, 105, 109, 97, 108, 115, 119, 104, 105, 99, 104, 105, 115, 97, 108, 117, 115, 116, 111, 102, 116, 104,
    101, 109, 105, 110, 100, 101, 120, 99, 101, 101, 100, 115, 116, 104, 101, 115, 104, 111, 114, 116, 118, 101, 104,
    101, 109, 101, 110, 99, 101, 111, 102, 97, 110, 121, 99, 97, 114, 110, 97, 108, 112, 108, 101, 97, 115, 117, 114,
    101]);
let result = base64Helper.encodeToStringSync(array, util.Type.MIME);
console.info("result = " + result);
/*
输出结果：result = TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz
aW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl
aGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=
 */

// BASIC编码
let base64Helper = new util.Base64Helper();
let array =
  new Uint8Array([77, 97, 110, 105, 115, 100, 105, 115, 116, 105, 110, 103, 117, 105, 115, 104, 101, 100, 110, 111, 116,
    111, 110, 108, 121, 98, 121, 104, 105, 115, 114, 101, 97, 115, 111, 110, 98, 117, 116, 98, 121, 116, 104, 105, 115,
    115, 105, 110, 103, 117, 108, 97, 114, 112, 97, 115, 115, 105, 111, 110, 102, 114, 111, 109, 111, 116, 104, 101,
    114, 97, 110, 105, 109, 97, 108, 115, 119, 104, 105, 99, 104, 105, 115, 97, 108, 117, 115, 116, 111, 102, 116, 104,
    101, 109, 105, 110, 100, 101, 120, 99, 101, 101, 100, 115, 116, 104, 101, 115, 104, 111, 114, 116, 118, 101, 104,
    101, 109, 101, 110, 99, 101, 111, 102, 97, 110, 121, 99, 97, 114, 110, 97, 108, 112, 108, 101, 97, 115, 117, 114,
    101]);
let result = base64Helper.encodeToStringSync(array, util.Type.BASIC);
console.info("result = " + result);
/*
输出结果：result = TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNzaW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZlaGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU=
 */

// BASIC_URL_SAFE编码
let base64Helper = new util.Base64Helper();
let array =
  new Uint8Array([77, 97, 110, 105, 115, 100, 105, 115, 116, 105, 110, 103, 117, 105, 115, 104, 101, 100, 110, 111, 116,
    111, 110, 108, 121, 98, 121, 104, 105, 115, 114, 101, 97, 115, 111, 110, 98, 117, 116, 98, 121, 116, 104, 105, 115,
    115, 105, 110, 103, 117, 108, 97, 114, 112, 97, 115, 115, 105, 111, 110, 102, 114, 111, 109, 111, 116, 104, 101,
    114, 97, 110, 105, 109, 97, 108, 115, 119, 104, 105, 99, 104, 105, 115, 97, 108, 117, 115, 116, 111, 102, 116, 104,
    101, 109, 105, 110, 100, 101, 120, 99, 101, 101, 100, 115, 116, 104, 101, 115, 104, 111, 114, 116, 118, 101, 104,
    101, 109, 101, 110, 99, 101, 111, 102, 97, 110, 121, 99, 97, 114, 110, 97, 108, 112, 108, 101, 97, 115, 117, 114,
    101]);
let result = base64Helper.encodeToStringSync(array, util.Type.BASIC_URL_SAFE);
console.info("result = " + result);
/*
输出结果：result = TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNzaW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZlaGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU
 */
// MIME_URL_SAFE编码
let base64Helper = new util.Base64Helper();
let array =
  new Uint8Array([77, 97, 110, 105, 115, 100, 105, 115, 116, 105, 110, 103, 117, 105, 115, 104, 101, 100, 110, 111, 116,
    111, 110, 108, 121, 98, 121, 104, 105, 115, 114, 101, 97, 115, 111, 110, 98, 117, 116, 98, 121, 116, 104, 105, 115,
    115, 105, 110, 103, 117, 108, 97, 114, 112, 97, 115, 115, 105, 111, 110, 102, 114, 111, 109, 111, 116, 104, 101,
    114, 97, 110, 105, 109, 97, 108, 115, 119, 104, 105, 99, 104, 105, 115, 97, 108, 117, 115, 116, 111, 102, 116, 104,
    101, 109, 105, 110, 100, 101, 120, 99, 101, 101, 100, 115, 116, 104, 101, 115, 104, 111, 114, 116, 118, 101, 104,
    101, 109, 101, 110, 99, 101, 111, 102, 97, 110, 121, 99, 97, 114, 110, 97, 108, 112, 108, 101, 97, 115, 117, 114,
    101]);
let result = base64Helper.encodeToStringSync(array, util.Type.MIME_URL_SAFE);
console.info("result = " + result);
/*
输出结果：result = TWFuaXNkaXN0aW5ndWlzaGVkbm90b25seWJ5aGlzcmVhc29uYnV0Ynl0aGlzc2luZ3VsYXJwYXNz
aW9uZnJvbW90aGVyYW5pbWFsc3doaWNoaXNhbHVzdG9mdGhlbWluZGV4Y2VlZHN0aGVzaG9ydHZl
aGVtZW5jZW9mYW55Y2FybmFscGxlYXN1cmU
 */

// 从API version 26.1.0开始，支持传入collections.Uint8Array（Sendable字节数组）
let base64Helper = new util.Base64Helper();
let sendableArray = new collections.Uint8Array([77, 97, 110]);
let result = base64Helper.encodeToStringSync(sendableArray, util.Type.BASIC);
console.info("result = " + result);
/*
输出结果：result = TWFu
 */
```
