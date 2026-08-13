# WebMessageExt

The message received or sent from web message port.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class WebMessageExt--><!--Device-webview-class WebMessageExt-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getArray

```TypeScript
getArray(): Array<string | double | long | boolean>
```

Get the array value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-getArray(): Array<string | double | long | boolean>--><!--Device-WebMessageExt-getArray(): Array<string | double | long | boolean>-End-->

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

Get the array buffer value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-getArrayBuffer(): ArrayBuffer--><!--Device-WebMessageExt-getArrayBuffer(): ArrayBuffer-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | Returns data of ArrayBuffer type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getBoolean

```TypeScript
getBoolean(): boolean
```

Get the boolean value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-getBoolean(): boolean--><!--Device-WebMessageExt-getBoolean(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns data of Boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getError

```TypeScript
getError(): Error
```

Get the error value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-getError(): Error--><!--Device-WebMessageExt-getError(): Error-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Error | Returns data of Error type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getNumber

```TypeScript
getNumber(): double | long
```

Get the number value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-getNumber(): double | long--><!--Device-WebMessageExt-getNumber(): double | long-End-->

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

Get the string value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-getString(): string--><!--Device-WebMessageExt-getString(): string-End-->

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
getType(): WebMessageType
```

Get the type of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-getType(): WebMessageType--><!--Device-WebMessageExt-getType(): WebMessageType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebMessageType](arkts-na-webview-webmessagetype-e.md) | Returns data of WebMessageType type |

## setArray

```TypeScript
setArray(message: Array<string | double | long | boolean>): void
```

Set the array value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-setArray(message: Array<string | double | long | boolean>): void--><!--Device-WebMessageExt-setArray(message: Array<string | double | long | boolean>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Array&lt;string \| double \| long \| boolean&gt; | 是 | set Array type data |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setArrayBuffer

```TypeScript
setArrayBuffer(message: ArrayBuffer): void
```

Set the array buffer value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-setArrayBuffer(message: ArrayBuffer): void--><!--Device-WebMessageExt-setArrayBuffer(message: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | ArrayBuffer | 是 | set ArrayBuffer type data |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setBoolean

```TypeScript
setBoolean(message: boolean): void
```

Set the boolean value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-setBoolean(message: boolean): void--><!--Device-WebMessageExt-setBoolean(message: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | boolean | 是 | set boolean type data |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setError

```TypeScript
setError(message: Error): void
```

Set the error value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-setError(message: Error): void--><!--Device-WebMessageExt-setError(message: Error): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Error | 是 | set Error type data |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setNumber

```TypeScript
setNumber(message: double): void
```

Set the number value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-setNumber(message: double): void--><!--Device-WebMessageExt-setNumber(message: double): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | double | 是 | set number type data |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setString

```TypeScript
setString(message: string): void
```

Set the string value of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-setString(message: string): void--><!--Device-WebMessageExt-setString(message: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 | set string type data |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setType

```TypeScript
setType(type: WebMessageType): void
```

Set the type of the web message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebMessageExt-setType(type: WebMessageType): void--><!--Device-WebMessageExt-setType(type: WebMessageType): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [WebMessageType](arkts-na-webview-webmessagetype-e.md) | 是 | set WebMessageType type data |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../../apis-arkweb/errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

