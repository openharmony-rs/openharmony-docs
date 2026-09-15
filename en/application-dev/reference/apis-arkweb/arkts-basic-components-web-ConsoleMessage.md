# Class (ConsoleMessage)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:50:41.977Z pushedAt=2026-08-07T08:11:56.982Z -->

ConsoleMessage is an object that encapsulates JavaScript console output information in the **Web** component. When a web page outputs logs through methods such as `console.log()`, `console.warn()`, and `console.error()`, this object is provided to the app through the `onConsole` event callback for monitoring and inspecting web page debug output. For sample code, see [onConsole event](./arkts-basic-components-web-events.md#onconsole).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 8.
>
> - The sample effect is subject to the actual device.

## constructor<sup>(deprecated)</sup>

constructor(message: string, sourceId: string, lineNumber: number, messageLevel: MessageLevel)

Constructs a **ConsoleMessage** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [constructor](#constructor9) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| message | string | Yes  | Log output information of **ConsoleMessage**.|
| sourceId | string | Yes  | Path and name of the web page source file.|
| lineNumber | number | Yes  | Line number of **ConsoleMessage**.|
| messageLevel | [MessageLevel](./arkts-basic-components-web-e.md#messagelevel) | Yes  | Log level of **ConsoleMessage**.|

## constructor<sup>9+</sup>

constructor()

Constructs a **ConsoleMessage** object.

**System capability**: SystemCapability.Web.Webview.Core

## getLineNumber

getLineNumber(): number

Obtains the line number of the console output in the web source file.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                  |
| ------ | -------------------- |
| number | Line number of the console output in the web source file. |

## getMessage

getMessage(): string

Obtains the log message of the console output.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                    |
| ------ | ---------------------- |
| string | Log information output to the console. |

## getMessageLevel

getMessageLevel(): MessageLevel

Obtains the level of this console message.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                               | Description                    |
| --------------------------------- | ---------------------- |
| [MessageLevel](./arkts-basic-components-web-e.md#messagelevel) | Level of the console message.|

## getSourceId

getSourceId(): string

Obtains the path and file name of the web source file.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| string | Path and file name of the web source file. |

## getSource<sup>23+</sup>

getSource(): ConsoleMessageSource

Obtains the log source of this console message.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| [ConsoleMessageSource](./arkts-basic-components-web-e.md#consolemessagesource23) | Log source of the console message.|