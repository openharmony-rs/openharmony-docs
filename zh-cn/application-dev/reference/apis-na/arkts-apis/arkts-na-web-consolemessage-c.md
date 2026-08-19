# ConsoleMessage

Encompassed message information as parameters to onConsole method.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ConsoleMessage--><!--Device-unnamed-export declare class ConsoleMessage-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ConsoleMessage-constructor()--><!--Device-ConsoleMessage-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getLineNumber

```TypeScript
getLineNumber(): int
```

Gets the line number of a console message.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ConsoleMessage-getLineNumber(): int--><!--Device-ConsoleMessage-getLineNumber(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return the line number of a console message. |

## getMessage

```TypeScript
getMessage(): string
```

Gets the message of a console message.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ConsoleMessage-getMessage(): string--><!--Device-ConsoleMessage-getMessage(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the message of a console message. |

## getMessageLevel

```TypeScript
getMessageLevel(): MessageLevel
```

Gets the message level of a console message.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ConsoleMessage-getMessageLevel(): MessageLevel--><!--Device-ConsoleMessage-getMessageLevel(): MessageLevel-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MessageLevel](arkts-na-web-messagelevel-e.md) | Return the message level of a console message, which can be { |

## getSource

```TypeScript
getSource(): ConsoleMessageSource
```

Gets the source of a console message.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ConsoleMessage-getSource(): ConsoleMessageSource--><!--Device-ConsoleMessage-getSource(): ConsoleMessageSource-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ConsoleMessageSource](arkts-na-web-consolemessagesource-e.md) | Return the source of a console message. |

## getSourceId

```TypeScript
getSourceId(): string
```

Gets the Web source file's path and name of a console message.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ConsoleMessage-getSourceId(): string--><!--Device-ConsoleMessage-getSourceId(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the Web source file's path and name of a console message. |

