# ConsoleMessage

```TypeScript
declare class ConsoleMessage
```

ConsoleMessage is an object that encapsulates JavaScript console output information in the **Web** component. When a web page outputs logs through methods such as `console.log()`, `console.warn()`, and `console.error()`, this object is provided to the app through the `onConsole` event callback for monitoring and inspecting web page debug output. For sample code, see [onConsole event](arkts-arkweb-web-comp-attribute.md#onconsole).

**Since:** 8

<!--Device-unnamed-declare class ConsoleMessage--><!--Device-unnamed-declare class ConsoleMessage-End-->

**System capability:** SystemCapability.Web.Webview.Core

<a id="constructor2"></a>

## constructor

```TypeScript
constructor()
```

Constructs a **ConsoleMessage** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConsoleMessage-constructor()--><!--Device-ConsoleMessage-constructor()-End-->

**System capability:** SystemCapability.Web.Webview.Core

<a id="constructor1"></a>

## constructor

```TypeScript
constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)
```

Constructs a **ConsoleMessage** object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** constructor

<!--Device-ConsoleMessage-constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)--><!--Device-ConsoleMessage-constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes | Log output information of **ConsoleMessage**. |
| sourceId | string | Yes | Path and name of the web page source file. |
| lineNumber | number | Yes | Line number of **ConsoleMessage**. |
| messageLevel | [MessageLevel](arkts-arkweb-web-comp-messagelevel-e.md) | Yes | Log level of **ConsoleMessage**. |

## getLineNumber

```TypeScript
getLineNumber(): number
```

Obtains the line number of the console output in the web source file.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConsoleMessage-getLineNumber(): number--><!--Device-ConsoleMessage-getLineNumber(): number-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Line number of the console output in the web source file. |

## getMessage

```TypeScript
getMessage(): string
```

Obtains the log message of the console output.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConsoleMessage-getMessage(): string--><!--Device-ConsoleMessage-getMessage(): string-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Log information output to the console. |

## getMessageLevel

```TypeScript
getMessageLevel(): MessageLevel
```

Obtains the level of this console message.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConsoleMessage-getMessageLevel(): MessageLevel--><!--Device-ConsoleMessage-getMessageLevel(): MessageLevel-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [MessageLevel](arkts-arkweb-web-comp-messagelevel-e.md) | Level of the console message. |

## getSource

```TypeScript
getSource() : ConsoleMessageSource
```

Obtains the log source of this console message.

**Since:** 23

<!--Device-ConsoleMessage-getSource() : ConsoleMessageSource--><!--Device-ConsoleMessage-getSource() : ConsoleMessageSource-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ConsoleMessageSource](arkts-arkweb-web-comp-consolemessagesource-e.md) | Log source of the console message. |

## getSourceId

```TypeScript
getSourceId(): string
```

Obtains the path and file name of the web source file.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ConsoleMessage-getSourceId(): string--><!--Device-ConsoleMessage-getSourceId(): string-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Path and file name of the web source file. |
