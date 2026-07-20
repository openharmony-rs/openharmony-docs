# JsMessageExt

该消息用于指示JavaScript代码执行结果的状态。

**起始版本：** 10

<!--Device-webview-class JsMessageExt--><!--Device-webview-class JsMessageExt-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

<a id="getarray"></a>
## getArray

```TypeScript
getArray(): Array<string | number | boolean>
```

获取JavaScript代码执行结果的数组类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsMessageExt-getArray(): Array<string | number | boolean>--><!--Device-JsMessageExt-getArray(): Array<string | number | boolean>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string \| number \| boolean&gt; | - Returns data of Array type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

<a id="getarraybuffer"></a>
## getArrayBuffer

```TypeScript
getArrayBuffer(): ArrayBuffer
```

获取JavaScript代码执行结果的原始二进制数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsMessageExt-getArrayBuffer(): ArrayBuffer--><!--Device-JsMessageExt-getArrayBuffer(): ArrayBuffer-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | - 返回原始二进制数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

<a id="getboolean"></a>
## getBoolean

```TypeScript
getBoolean(): boolean
```

获取JavaScript代码执行结果的布尔类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsMessageExt-getBoolean(): boolean--><!--Device-JsMessageExt-getBoolean(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 返回布尔类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

<a id="geterrordescription"></a>
## getErrorDescription

```TypeScript
getErrorDescription(): string | null
```

获取JS执行的异常信息，并将其序列化为字符串。

**起始版本：** 22

<!--Device-JsMessageExt-getErrorDescription(): string | null--><!--Device-JsMessageExt-getErrorDescription(): string | null-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - If an exception occurs, or the returned type is object, return the serialized string in the format of "Not support type: <{exception\|object}>", Parts exceeding a length of2048 will be truncated; otherwise, return null. |

<a id="getnumber"></a>
## getNumber

```TypeScript
getNumber(): number
```

获取JavaScript代码执行结果的数值类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsMessageExt-getNumber(): number--><!--Device-JsMessageExt-getNumber(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - 返回数值类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

<a id="getstring"></a>
## getString

```TypeScript
getString(): string
```

获取JavaScript代码执行结果的字符串类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsMessageExt-getString(): string--><!--Device-JsMessageExt-getString(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 返回字符串类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

<a id="gettype"></a>
## getType

```TypeScript
getType(): JsMessageType
```

获取数据对象的类型。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsMessageExt-getType(): JsMessageType--><!--Device-JsMessageExt-getType(): JsMessageType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [JsMessageType](arkts-arkweb-webview-jsmessagetype-e.md) | - runJavaScriptExt接口脚本执行后返回的结果的类型。 |

