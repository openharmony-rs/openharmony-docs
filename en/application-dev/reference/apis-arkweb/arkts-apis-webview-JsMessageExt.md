# Class (JsMessageExt)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=c3549f5fc26f86afdb3e7a215c50ff6d6d5cab0c translatedAt=2026-08-07T04:44:27.860Z pushedAt=2026-08-07T08:11:04.359Z -->

JsMessageExt is a data class in the ArkWeb framework used to encapsulate the result returned after executing a JavaScript script through the [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10) API. Unlike the conventional runJavaScript API, runJavaScriptExt supports richer return value types, and JsMessageExt provides a type-safe way to access these diverse return results. Developers first obtain the data type through the getType method of JsMessageExt, and then call the corresponding get method to retrieve the specific value.

JsMessageExt supports parsing of multiple JavaScript return value types: string (getString), number (getNumber), boolean (getBoolean), raw binary data (getArrayBuffer), array (getArray), and more. When the obtained data type does not match the actual stored type (for example, calling getString on a numeric type), error code 17100014 is thrown. Starting from API version 22, JsMessageExt also provides the getErrorDescription method for obtaining exception information during JavaScript execution. If the return value is of the object type, it is uniformly formatted into a description string.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 10.
>
> - The sample effect is subject to the actual device.

## getType<sup>10+</sup>

getType(): JsMessageType

Obtains the type of the data object. For details about the sample code, see [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description                                                     |
| --------------| --------------------------------------------------------- |
| [JsMessageType](./arkts-apis-webview-e.md#jsmessagetype10) | Data type of the result returned after the [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10) API is executed.|

## getString<sup>10+</sup>

getString(): string

Obtains string-type data of the data object. For details about the sample code, see [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| string | String-type data obtained after the script of the runJavaScriptExt API is executed. |

**Error codes**

For details about the error codes, see [Webview Error Codes](./errorcode-webview.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getNumber<sup>10+</sup>

getNumber(): number

Obtains number-type data of the data object. For details about the sample code, see [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| number | Numeric data obtained after the script of the runJavaScriptExt API is executed. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getBoolean<sup>10+</sup>

getBoolean(): boolean

Obtains Boolean-type data of the data object. For details about the sample code, see [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| boolean | Boolean data obtained after the script of the runJavaScriptExt API is executed. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getArrayBuffer<sup>10+</sup>

getArrayBuffer(): ArrayBuffer

Obtains raw binary data of the data object. For details about the sample code, see [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| ArrayBuffer | Raw binary data obtained after the execution of the runJavaScriptExt interface script. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getArray<sup>10+</sup>

getArray(): Array\<string | number | boolean\>

Obtains array-type data of the data object. For details about the sample code, see [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| Array\<string \| number \| boolean\> | Array data obtained after the script of the runJavaScriptExt API is executed. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getErrorDescription<sup>22+</sup>

getErrorDescription(): string \| null

Obtains the error information about the JavaScript execution. For details about the sample code, see [runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description                                                     |
| --------------| --------------------------------------------------------- |
| string \| null | If an exception occurs during JavaScript script execution, or the return value is of the object type, the system formats the exception information or object into the string "Not support type: <{exception \| object}>". The string length does not exceed 2048 characters, and the excess part will be truncated. If the object contains members of the callback type, they will be automatically ignored during serialization. In all other cases, the interface returns null. |