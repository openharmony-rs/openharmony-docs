# WebMessageExt

The message received or sent from web message port.

**起始版本：** 10

<!--Device-webview-class WebMessageExt--><!--Device-webview-class WebMessageExt-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getArray

```TypeScript
getArray(): Array<string | number | boolean>
```

获取数据对象的数组类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-getArray(): Array<string | number | boolean>--><!--Device-WebMessageExt-getArray(): Array<string | number | boolean>-End-->

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

获取数据对象的原始二进制数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-getArrayBuffer(): ArrayBuffer--><!--Device-WebMessageExt-getArrayBuffer(): ArrayBuffer-End-->

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

获取数据对象的布尔类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-getBoolean(): boolean--><!--Device-WebMessageExt-getBoolean(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 返回布尔类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getError

```TypeScript
getError(): Error
```

获取数据对象的错误类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-getError(): Error--><!--Device-WebMessageExt-getError(): Error-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Error | - 返回错误对象类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getNumber

```TypeScript
getNumber(): number
```

获取数据对象的数值类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-getNumber(): number--><!--Device-WebMessageExt-getNumber(): number-End-->

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

获取数据对象的字符串类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-getString(): string--><!--Device-WebMessageExt-getString(): string-End-->

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
getType(): WebMessageType
```

获取数据对象的类型。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-getType(): WebMessageType--><!--Device-WebMessageExt-getType(): WebMessageType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebMessageType](arkts-arkweb-webview-webmessagetype-e.md) | - 返回类型为 WebMessageType 的数据。 |

## setArray

```TypeScript
setArray(message: Array<string | number | boolean>): void
```

设置数据对象的数组类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-setArray(message: Array<string | number | boolean>): void--><!--Device-WebMessageExt-setArray(message: Array<string | number | boolean>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Array&lt;string \| number \| boolean&gt; | 是 | 数组类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setArrayBuffer

```TypeScript
setArrayBuffer(message: ArrayBuffer): void
```

设置数据对象的原始二进制数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-setArrayBuffer(message: ArrayBuffer): void--><!--Device-WebMessageExt-setArrayBuffer(message: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | ArrayBuffer | 是 | 原始二进制类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setBoolean

```TypeScript
setBoolean(message: boolean): void
```

设置数据对象的布尔类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-setBoolean(message: boolean): void--><!--Device-WebMessageExt-setBoolean(message: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | boolean | 是 | 布尔类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setError

```TypeScript
setError(message: Error): void
```

设置数据对象的错误对象类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-setError(message: Error): void--><!--Device-WebMessageExt-setError(message: Error): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Error | 是 | 错误对象类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setNumber

```TypeScript
setNumber(message: number): void
```

设置数据对象的数值类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-setNumber(message: number): void--><!--Device-WebMessageExt-setNumber(message: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | number | 是 | 数值类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setString

```TypeScript
setString(message: string): void
```

设置数据对象的字符串类型数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-setString(message: string): void--><!--Device-WebMessageExt-setString(message: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 | 字符串类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## setType

```TypeScript
setType(type: WebMessageType): void
```

设置数据对象的类型。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessageExt-setType(type: WebMessageType): void--><!--Device-WebMessageExt-setType(type: WebMessageType): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [WebMessageType](arkts-arkweb-webview-webmessagetype-e.md) | 是 | 设置 WebMessageType 类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

