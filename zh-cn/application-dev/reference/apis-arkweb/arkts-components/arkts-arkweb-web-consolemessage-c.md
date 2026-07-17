# ConsoleMessage

Encompassed message information as parameters to {@link onConsole} method.

**起始版本：** 8

<!--Device-unnamed-declare class ConsoleMessage--><!--Device-unnamed-declare class ConsoleMessage-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)
```

Constructor.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

<!--Device-ConsoleMessage-constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)--><!--Device-ConsoleMessage-constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 | ConsoleMessage的日志输出信息。 |
| sourceId | string | 是 | 网页源文件的路径和文件名。 |
| lineNumber | number | 是 | ConsoleMessage的行号。 |
| messageLevel | [MessageLevel](arkts-arkweb-web-messagelevel-e.md) | 是 | ConsoleMessage的日志级别。 |

## constructor

```TypeScript
constructor()
```

ConsoleMessage的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConsoleMessage-constructor()--><!--Device-ConsoleMessage-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getLineNumber

```TypeScript
getLineNumber(): number
```

获取ConsoleMessage的行数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConsoleMessage-getLineNumber(): number--><!--Device-ConsoleMessage-getLineNumber(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回ConsoleMessage的行数。 |

## getMessage

```TypeScript
getMessage(): string
```

获取ConsoleMessage的日志信息。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConsoleMessage-getMessage(): string--><!--Device-ConsoleMessage-getMessage(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回ConsoleMessage的日志信息。 |

## getMessageLevel

```TypeScript
getMessageLevel(): MessageLevel
```

获取ConsoleMessage的信息级别。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConsoleMessage-getMessageLevel(): MessageLevel--><!--Device-ConsoleMessage-getMessageLevel(): MessageLevel-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MessageLevel](arkts-arkweb-web-messagelevel-e.md) | 返回ConsoleMessage的信息级别。 |

## getSource

```TypeScript
getSource() : ConsoleMessageSource
```

获取ConsoleMessage的日志来源。

**起始版本：** 23

<!--Device-ConsoleMessage-getSource() : ConsoleMessageSource--><!--Device-ConsoleMessage-getSource() : ConsoleMessageSource-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ConsoleMessageSource](arkts-arkweb-web-consolemessagesource-e.md) | 返回ConsoleMessage的日志来源。 |

## getSourceId

```TypeScript
getSourceId(): string
```

获取网页源文件路径和文件名。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConsoleMessage-getSourceId(): string--><!--Device-ConsoleMessage-getSourceId(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回网页源文件路径和文件名。 |

