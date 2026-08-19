# JsMessageExt

The message for indicating the of result of JavaScript code execution.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-class JsMessageExt--><!--Device-webview-class JsMessageExt-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## getArray

```TypeScript
getArray(): Array<string | double | long | boolean>
```

Get the array value of the the JavaScript code execution result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-JsMessageExt-getArray(): Array<string | double | long | boolean>--><!--Device-JsMessageExt-getArray(): Array<string | double | long | boolean>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string \| double \| long \| boolean&gt; | Returns data of Array type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getArrayBuffer

```TypeScript
getArrayBuffer(): ArrayBuffer
```

Get the array buffer value of the JavaScript code execution result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-JsMessageExt-getArrayBuffer(): ArrayBuffer--><!--Device-JsMessageExt-getArrayBuffer(): ArrayBuffer-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | Returns data of ArrayBuffer |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getBoolean

```TypeScript
getBoolean(): boolean
```

Get the boolean value of the JavaScript code execution result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-JsMessageExt-getBoolean(): boolean--><!--Device-JsMessageExt-getBoolean(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns data of Boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getErrorDescription

```TypeScript
getErrorDescription(): string | null
```

Get the exception or object of the the JavaScript code execution result and serialize it into a string.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-JsMessageExt-getErrorDescription(): string | null--><!--Device-JsMessageExt-getErrorDescription(): string | null-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | if an exception occurs, or the returned type is object, return the serialized string in the format of "Not support type: &lt;{exception\|object}&gt;", Parts exceeding a length of 2048 will be truncated; otherwise, return null. |

## getNumber

```TypeScript
getNumber(): double | long
```

Get the number value of the JavaScript code execution result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-JsMessageExt-getNumber(): double | long--><!--Device-JsMessageExt-getNumber(): double | long-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | Returns data of number type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getString

```TypeScript
getString(): string
```

Get the string value of the JavaScript code execution result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-JsMessageExt-getString(): string--><!--Device-JsMessageExt-getString(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns data of string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getType

```TypeScript
getType(): JsMessageType
```

Get the type of the JavaScript code execution result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-JsMessageExt-getType(): JsMessageType--><!--Device-JsMessageExt-getType(): JsMessageType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [JsMessageType](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-jsmessagetype-e.md) | Returns data of JsMessageType type |

