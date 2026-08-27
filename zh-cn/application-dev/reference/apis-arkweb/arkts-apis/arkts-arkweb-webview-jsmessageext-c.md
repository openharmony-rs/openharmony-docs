# JsMessageExt

JsMessageExt是ArkWeb框架中用于封装 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 接口执行JavaScript脚本后返回结果的数据类。与常规的runJavaScript接口不同，runJavaScriptExt支持更丰富的返回值类型，JsMessageExt则为这些多样化的返回结果提供了类型安全的访问方式。开发 者通过JsMessageExt的getType方法先获取数据类型，再调用对应的get方法获取具体值。JsMessageExt支持多种JavaScript返回值类型的解析：字符串（getString）、数值（getNumber）、布尔值（getBoolean）、原始二进制数据（getArrayBuffer）、数组（getArray ）等。当获取的数据类型与实际存储类型不匹配时（例如对数值类型调用getString），会抛出错误码17100014。从API version 22开始，JsMessageExt还提供了getErrorDescription方法，用 于获取JavaScript执行过程中的异常信息，如果返回值为object类型则统一格式化为描述字符串。

**起始版本：** 10

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## getArray

```TypeScript
getArray(): Array<string | number | boolean>
```

获取数据对象的数组类型数据。完整示例代码参考 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string \ | number \| boolean & gt; | 返回runJavaScriptExt接口脚本执行后得到的数组类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getArrayBuffer

```TypeScript
getArrayBuffer(): ArrayBuffer
```

获取数据对象的原始二进制数据。完整示例代码参考 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 返回runJavaScriptExt接口脚本执行后得到的原始二进制数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getBoolean

```TypeScript
getBoolean(): boolean
```

获取数据对象的布尔类型数据。完整示例代码参考 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回runJavaScriptExt接口脚本执行后得到的布尔类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getErrorDescription

```TypeScript
getErrorDescription(): string | null
```

获取JavaScript执行的异常信息。完整示例代码参考 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string \| null | 若JavaScript脚本执行过程中发生异常，或返回值为object类型，系统会将异常信息或object对象格式化为"Not support type: & lt;{exception \ | object} & gt;"字符串返回，该字符串长度不超过2048个字符，超长部分将被截断；若object对象中包含callback类型的成员，则序列化时将自动忽略该成员；其余情况，接口均返回null。 |

## getNumber

```TypeScript
getNumber(): number
```

获取数据对象的数值类型数据。完整示例代码参考 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回runJavaScriptExt接口脚本执行后得到的数值类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getString

```TypeScript
getString(): string
```

获取数据对象的字符串类型数据。完整示例代码参考 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回runJavaScriptExt接口脚本执行后得到的字符串类型的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-类型和值不匹配) | The type and value of the message do not match. |

## getType

```TypeScript
getType(): JsMessageType
```

获取数据对象的类型。完整示例代码参考 [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) 。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [JsMessageType](arkts-arkweb-webview-jsmessagetype-e.md) | [runJavaScriptExt]{ |
