# ConsoleMessage

ConsoleMessage is an object that encapsulates JavaScript console output information in the **Web** component. When a web page outputs logs through methods such as `console.log()`, `console.warn()`, and `console.error()`, this object is provided to the app through the `onConsole` event callback for monitoring and inspecting web page debug output. For sample code, see [onConsole event](arkts-arkweb-web-comp-attribute.md#onconsole).

**Since:** 8

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)
```

Constructs a **ConsoleMessage** object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** constructor

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes | Log output information of **ConsoleMessage**. |
| sourceId | string | Yes | Path and name of the web page source file. |
| lineNumber | number | Yes | Line number of **ConsoleMessage**. |
| messageLevel | [MessageLevel](arkts-arkweb-messagelevel-e.md) | Yes | Log level of **ConsoleMessage**. |

## constructor

```TypeScript
constructor()
```

Constructs a **ConsoleMessage** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## getLineNumber

```TypeScript
getLineNumber(): number
```

Obtains the line number of the console output in the web source file.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [MessageLevel](arkts-arkweb-messagelevel-e.md) | Level of the console message. |

## getSource

```TypeScript
getSource() : ConsoleMessageSource
```

Obtains the log source of this console message.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ConsoleMessageSource](arkts-arkweb-consolemessagesource-e.md) | Log source of the console message. |

## getSourceId

```TypeScript
getSourceId(): string
```

Obtains the path and file name of the web source file.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Path and file name of the web source file. |
