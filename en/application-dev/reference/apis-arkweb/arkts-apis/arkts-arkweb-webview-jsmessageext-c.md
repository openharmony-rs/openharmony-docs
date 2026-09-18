# JsMessageExt

JsMessageExt is a data class in the ArkWeb framework used to encapsulate the result returned after executing a JavaScript script through the [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) API. Unlike the conventional runJavaScript API, runJavaScriptExt supports richer return value types, and JsMessageExt provides a type-safe way to access these diverse return results. Developers first obtain the data type through the getType method of JsMessageExt, and then call the corresponding get method to retrieve the specific value.

JsMessageExt supports parsing of multiple JavaScript return value types: string (getString), number (getNumber), boolean (getBoolean), raw binary data (getArrayBuffer), array (getArray), and more. When the obtained data type does not match the actual stored type (for example, calling getString on a numeric type), error code 17100014 is thrown. Starting from API version 22, JsMessageExt also provides the getErrorDescription method for obtaining exception information during JavaScript execution. If the return value is of the object type, it is uniformly formatted into a description string.

**Since:** 10

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getArray

```TypeScript
getArray(): Array<string | number | boolean>
```

Obtains array-type data of the data object. For details about the sample code, see [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string &#124; number &#124; boolean&gt; | Array data obtained after the script of the runJavaScriptExt API is executed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getArrayBuffer

```TypeScript
getArrayBuffer(): ArrayBuffer
```

Obtains raw binary data of the data object. For details about the sample code, see [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Raw binary data obtained after the execution of the runJavaScriptExt interface script. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getBoolean

```TypeScript
getBoolean(): boolean
```

Obtains Boolean-type data of the data object. For details about the sample code, see [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean data obtained after the script of the runJavaScriptExt API is executed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getErrorDescription

```TypeScript
getErrorDescription(): string | null
```

Obtains the error information about the JavaScript execution. For details about the sample code, see [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext).

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | If an exception occurs during JavaScript script execution, or the return value is of the object type, the system formats the exception information or object into the string "Not support type: &lt;{exception &#124; object}&gt;". The string length does not exceed 2048 characters, and the excess part will be truncated. If the object contains members of the callback type, they will be automatically ignored during serialization. In all other cases, the interface returns null. |

## getNumber

```TypeScript
getNumber(): number
```

Obtains number-type data of the data object. For details about the sample code, see [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Numeric data obtained after the script of the runJavaScriptExt API is executed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getString

```TypeScript
getString(): string
```

Obtains string-type data of the data object. For details about the sample code, see [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | String-type data obtained after the script of the runJavaScriptExt API is executed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getType

```TypeScript
getType(): JsMessageType
```

Obtains the type of the data object. For details about the sample code, see [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [JsMessageType](arkts-arkweb-webview-jsmessagetype-e.md) | Data type of the result returned after the [runJavaScriptExt](arkts-arkweb-webview-webviewcontroller-c.md#runjavascriptext) API is executed. |
