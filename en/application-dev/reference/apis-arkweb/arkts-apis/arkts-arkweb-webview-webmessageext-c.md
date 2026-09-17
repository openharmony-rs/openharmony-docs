# WebMessageExt

Implements a **WebMessageExt** object that received and sent by the [WebMessagePort](arkts-arkweb-webview-webmessageport-i.md) API.

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

Obtains array-type data of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string &#124; number &#124; boolean&gt; | Data of the array type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getArrayBuffer

```TypeScript
getArrayBuffer(): ArrayBuffer
```

Obtains raw binary data of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Raw binary data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getBoolean

```TypeScript
getBoolean(): boolean
```

Obtains Boolean-type data of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Data of the Boolean type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getError

```TypeScript
getError(): Error
```

Obtains the error-object-type data of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Error | Data of the error object type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getNumber

```TypeScript
getNumber(): number
```

Obtains number-type data of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Data of the number type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getString

```TypeScript
getString(): string
```

Obtains string-type data of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Data of the string type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## getType

```TypeScript
getType(): WebMessageType
```

Obtains the type of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WebMessageType](arkts-arkweb-webview-webmessagetype-e.md) | Data types supported by the [webMessagePort](arkts-arkweb-webview-webmessageport-i.md) API. |

## setArray

```TypeScript
setArray(message: Array<string | number | boolean>): void
```

Sets the array-type data for the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | Array&lt;string &#124; number &#124; boolean&gt; | Yes | Data of the array type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## setArrayBuffer

```TypeScript
setArrayBuffer(message: ArrayBuffer): void
```

Sets the raw binary data for the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | ArrayBuffer | Yes | Raw binary data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## setBoolean

```TypeScript
setBoolean(message: boolean): void
```

Sets the Boolean-type data for the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | boolean | Yes | Data of the Boolean type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## setError

```TypeScript
setError(message: Error): void
```

Sets the error-object-type data for the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | Error | Yes | Data of the error object type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## setNumber

```TypeScript
setNumber(message: number): void
```

Sets the number-type data of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | number | Yes | Data of the number type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## setString

```TypeScript
setString(message: string): void
```

Sets the string-type data of the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes | String type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |

## setType

```TypeScript
setType(type: WebMessageType): void
```

Sets the type for the data object. For details about the sample code, see [onMessageEventExt](arkts-arkweb-webview-webmessageport-i.md#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [WebMessageType](arkts-arkweb-webview-webmessagetype-e.md) | Yes | Data types supported by the [webMessagePort](arkts-arkweb-webview-webmessageport-i.md) API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100014](../errorcode-webview.md#17100014-type-and-value-mismatch) | The type and value of the message do not match. |
