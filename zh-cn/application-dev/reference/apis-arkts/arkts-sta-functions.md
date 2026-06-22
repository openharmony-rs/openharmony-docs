# Functions
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供URI编码和解码相关的全局函数。推荐优先使用`encodeURI`、`decodeURI`、`encodeURIComponent`和`decodeURIComponent`；`escape`和`unescape`仅用于兼容旧代码。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## decodeURI

export function decodeURI(uri: string): string

解码由`encodeURI`或兼容方式编码的完整URI。URI保留字符会保持转义形式。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| uri | string | 是 | 待解码的URI字符串。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 解码后的URI字符串。 |

**错误信息：**

| 错误信息 | 说明 |
| :--- | :--- |
| URIError | 传入的URI包含非法转义序列时抛出。<br>可能原因：输入字符串不是由`encodeURI`生成的，或已被篡改导致转义序列不合法。<br>处理步骤：检查输入字符串中的`%`转义序列是否合法，确保每个`%`后跟随两个有效的十六进制字符，且多字节转义序列构成有效的UTF-8编码。 |

**示例：**

```ts
const encoded = "https://example.test/search?q=ArkTS%20%E6%96%87%E6%A1%A3";
console.info(decodeURI(encoded)); // "https://example.test/search?q=ArkTS 文档"

try {
  decodeURI("%"); // 非法转义序列，抛出URIError
} catch (e) {
  console.info(e instanceof URIError); // true
}
```

## encodeURI

export function encodeURI(uri: string): string

编码完整URI。该函数会保留URI语法字符，例如`:`、`/`、`?`和`#`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| uri | string | 是 | 待编码的URI字符串。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 编码后的URI字符串。 |

**示例：**

```ts
const raw = "https://example.test/search?q=ArkTS 文档";
console.info(encodeURI(raw)); // "https://example.test/search?q=ArkTS%20%E6%96%87%E6%A1%A3"
```

## decodeURIComponent

export function decodeURIComponent(uriComponent: string): string

解码由`encodeURIComponent`编码的URI组件。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| uriComponent | string | 是 | 待解码的URI组件字符串。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 解码后的URI组件字符串。 |

**错误信息：**

| 错误信息 | 说明 |
| :--- | :--- |
| URIError | 传入的URI组件包含非法转义序列时抛出。<br>可能原因：输入字符串不是由`encodeURIComponent`生成的，或已被篡改导致转义序列不合法。<br>处理步骤：检查输入字符串中的`%`转义序列是否合法，确保每个`%`后跟随两个有效的十六进制字符，且多字节转义序列构成有效的UTF-8编码。 |

**示例：**

```ts
const encoded = "ArkTS%20%E6%96%87%E6%A1%A3";
console.info(decodeURIComponent(encoded)); // "ArkTS 文档"

try {
  decodeURIComponent("%ZZ"); // 非法转义序列，抛出URIError
} catch (e) {
  console.info(e instanceof URIError); // true
}
```

## encodeURIComponent

export function encodeURIComponent(uriComponent: String | Number | Boolean): string

编码URI组件。该函数会编码更多URI语法字符，适合处理路径片段、查询参数值或片段内容。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| uriComponent | String \| Number \| Boolean | 是 | 待编码为URI组件的值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 编码后的URI组件字符串。 |

**示例：**

```ts
const query = "ArkTS 文档";
console.info(encodeURIComponent(query)); // "ArkTS%20%E6%96%87%E6%A1%A3"

// 传入Number和Boolean时，先转为字符串再编码
console.info(encodeURIComponent(100));  // "100"
console.info(encodeURIComponent(true)); // "true"
```

## escape

export function escape(str: string): string

按旧式规则转义字符串。对ASCII字符中不属于`@*_+-./`的字符进行`%XX`编码，对非ASCII字符进行`%uXXXX`（Unicode码点）编码。该函数不支持UTF-8编码，也不处理代理对（surrogate pairs），新代码应优先使用`encodeURI`或`encodeURIComponent`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| str | string | 是 | 待转义的字符串。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 转义后的字符串。 |

**示例：**

```ts
const escaped = escape("https://example.test/search?q=ArkTS 文档");
// 其中%u6587和%u6863为汉字"文档"的Unicode码点转义，与encodeURIComponent的UTF-8字节编码%E6%96%87%E6%A1%A3不同
console.info(escaped); // "https%3A//example.test/search%3Fq%3DArkTS%20%u6587%u6863"
```

## unescape

export function unescape(str: string): string

按旧式规则还原`escape`生成的字符串。支持识别`%XX`和`%uXXXX`格式的转义序列。该函数不处理UTF-8编码，新代码应优先使用`decodeURI`或`decodeURIComponent`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| str | string | 是 | 待还原的字符串。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 还原后的字符串。 |

**示例：**

```ts
const encoded = "https%3A//example.test/search%3Fq%3DArkTS%20%u6587%u6863"
console.info(unescape(encoded)); // "https://example.test/search?q=ArkTS 文档"
```
