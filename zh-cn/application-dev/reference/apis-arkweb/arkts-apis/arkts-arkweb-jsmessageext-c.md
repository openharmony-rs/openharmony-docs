# JsMessageExt

该消息用于指示JavaScript代码执行结果的状态。

**起始版本：** 10

**系统能力：** SystemCapability.Web.Webview.Core

## getArray

```TypeScript
getArray(): Array<string | number | boolean>
```

获取JavaScript代码执行结果的数组类型数据。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string \| number \| boolean&gt; | - Returns data of Array type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getArrayBuffer

```TypeScript
getArrayBuffer(): ArrayBuffer
```

获取JavaScript代码执行结果的原始二进制数据。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | - 返回原始二进制数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getBoolean

```TypeScript
getBoolean(): boolean
```

获取JavaScript代码执行结果的布尔类型数据。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 返回布尔类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getErrorDescription

```TypeScript
getErrorDescription(): string | null
```

获取JS执行的异常信息，并将其序列化为字符串。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - If an exception occurs, or the returned type is object, return theserialized string in the format of "Not support type: &lt;{exception\|object}&gt;", Parts exceeding a length of2048 will be truncated; otherwise, return null. |

## getNumber

```TypeScript
getNumber(): number
```

获取JavaScript代码执行结果的数值类型数据。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - 返回数值类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getString

```TypeScript
getString(): string
```

获取JavaScript代码执行结果的字符串类型数据。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 返回字符串类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getType

```TypeScript
getType(): JsMessageType
```

获取数据对象的类型。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| JsMessageType | - runJavaScriptExt接口脚本执行后返回的结果的类型。 |

