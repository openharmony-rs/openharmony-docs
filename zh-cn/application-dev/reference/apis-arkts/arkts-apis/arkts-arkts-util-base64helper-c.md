# Base64Helper

提供 Base64 和 Base64URL 的编解码。Base64 编码表包含 64 个字符，分别为大写字母（A-Z）、小写字母（a-z）、数字（0-9）以及特殊字符加号（+）和斜杠（/）。编码时，原始数据按三个字节一组进行划分，每组包含一个 6 位的数字。然后使用 Base64编码表中对应的字符来表示这些数字。如果最后一组只包含一个或两个字节，则使用等号（=）进行填充。Base64URL 编码表包含64 个字符，分别为大写字母（A-Z）、小写字母（a-z）、数字（0-9）以及特殊字符加号（+）和斜杠（/）。Base64URL 编码结果不包含等号（=）。

**起始版本：** 9

<!--Device-util-class Base64Helper--><!--Device-util-class Base64Helper-End-->

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

用于创建 **Base64Helper** 实例的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Base64Helper-constructor()--><!--Device-Base64Helper-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

<a id="decode"></a>
## decode

```TypeScript
decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>
```

将输入内容解码为 Uint8Array 对象。该接口使用 promise 返回结果。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Base64Helper-decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>--><!--Device-Base64Helper-decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array \| string | 是 | 要解码的 Uint8Array 对象或字符串。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 解码格式。<br>可取值如下：<br>- **util.Type.BASIC**（默认）：Base64 解码。<br>-**util.Type.MIME**：Base64 解码。输入参数 **src** 包含回车符和换行符。<br>- **util.Type.BASIC_URL_SAFE**：Base64URL 解码。<br>- **util.Type.MIME_URL_SAFE**：Base64URL 解码。输入参数 **src** 包含回车符和换行符。<br>**起始版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 用于返回获取到的 Uint8Array 对象的 promise。 |

<a id="decodesync"></a>
## decodeSync

```TypeScript
decodeSync(src: Uint8Array | string, options?: Type): Uint8Array
```

将字符串解码为 Uint8Array 对象。该接口同步返回结果。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Base64Helper-decodeSync(src: Uint8Array | string, options?: Type): Uint8Array--><!--Device-Base64Helper-decodeSync(src: Uint8Array | string, options?: Type): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array \| string | 是 | 要解码的 Uint8Array 对象或字符串。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 解码格式。<br>可取值如下：<br>- **util.Type.BASIC**（默认）：Base64 解码。<br>-**util.Type.MIME**：Base64 解码。输入参数 **src** 包含回车符和换行符。<br>- **util.Type.BASIC_URL_SAFE**：Base64URL 解码。<br>- **util.Type.MIME_URL_SAFE**：Base64URL 解码。输入参数 **src** 包含回车符和换行符。<br>**起始版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 获取到的 Uint8Array 对象。 |

<a id="encode"></a>
## encode

```TypeScript
encode(src: Uint8Array, options?: Type): Promise<Uint8Array>
```

将输入内容编码为 Uint8Array 对象。该接口使用 promise 返回结果。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Base64Helper-encode(src: Uint8Array, options?: Type): Promise<Uint8Array>--><!--Device-Base64Helper-encode(src: Uint8Array, options?: Type): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 编码格式。<br>可取值如下：<br>- **util.Type.BASIC**（默认）：Base64 编码。<br>-**util.Type.BASIC_URL_SAFE**：Base64URL 编码。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 用于返回获取到的 Uint8Array 对象的 promise。 |

<a id="encodesync"></a>
## encodeSync

```TypeScript
encodeSync(src: Uint8Array, options?: Type): Uint8Array
```

将输入内容编码为 Uint8Array 对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Base64Helper-encodeSync(src: Uint8Array, options?: Type): Uint8Array--><!--Device-Base64Helper-encodeSync(src: Uint8Array, options?: Type): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 编码格式。<br>可取值如下：<br>- **util.Type.BASIC**（默认）：Base64 编码。<br>-**util.Type.BASIC_URL_SAFE**：Base64URL 编码。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 获取到的 Uint8Array 对象。 |

<a id="encodetostring"></a>
## encodeToString

```TypeScript
encodeToString(src: Uint8Array, options?: Type): Promise<string>
```

将输入内容编码为字符串。该接口使用 promise 返回结果。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Base64Helper-encodeToString(src: Uint8Array, options?: Type): Promise<string>--><!--Device-Base64Helper-encodeToString(src: Uint8Array, options?: Type): Promise<string>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 编码格式。<br>可取值如下：<br>- **util.Type.BASIC**（默认）：Base64 编码。返回值不包含回车符或换行符。<br>- **util.Type.MIME**：Base64 编码。返回值每行最多 76 个字符且以 '\r\n' 结尾。<br>-**util.Type.BASIC_URL_SAFE**：Base64URL 编码。返回值不包含回车符或换行符。<br>- **util.Type.MIME_URL_SAFE**：Base64URL 编码。返回值每行最多 76 个字符且以 '\r\n' 结尾。<br>**起始版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 用于返回获取到的字符串的 promise。 |

<a id="encodetostringsync"></a>
## encodeToStringSync

```TypeScript
encodeToStringSync(src: Uint8Array, options?: Type): string
```

对输入的 Uint8Array 字节数组进行 Base64 编码，并返回字符串。该方法支持多种编码格式，包括标准 Base64 编码、符合MIME 规范的 Base64 编码（带换行）以及 URL 安全的 Base64 编码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Base64Helper-encodeToStringSync(src: Uint8Array, options?: Type): string--><!--Device-Base64Helper-encodeToStringSync(src: Uint8Array, options?: Type): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |
| options | [Type](arkts-arkts-util-type-e.md) | 否 | 编码格式。<br>可取值如下：<br>- **util.Type.BASIC**（默认）：Base64 编码。返回值不包含回车符或换行符。<br>- **util.Type.MIME**：Base64 编码。如果返回值超过 76 个字符，则每 76 个字符插入一个换行，每行以 '\r\n' 结尾。如果返回值少于 76 个字符，则抛出异常。<br>- **util.Type.BASIC_URL_SAFE**：Base64URL 编码。返回值不包含回车符或换行符。<br>- **util.Type.MIME_URL_SAFE**：Base64URL 编码。返回值每行最多 76 个字符且以'\r\n' 结尾。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 获取到的字符串。 |

