# Class (WebMessageExt)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=f18d113dd90e7361c74b830ab39cc318edd40714 translatedAt=2026-11-06T11:06:06.975Z pushedAt=2026-11-10T02:24:49.384Z nl=1 -->

WebMessageExt is an extended data object used for receiving and sending in the [WebMessagePort](./arkts-apis-webview-WebMessagePort.md) interface. It supports multiple data types: string (STRING), number (NUMBER), boolean (BOOLEAN), binary data (ARRAY_BUFFER), array (ARRAY), and error object (ERROR). This class provides a structured data carrier for cross-language message communication between the ArkTS side and the HTML5 side. It sets and gets the data type through setType/getType, and then reads and writes specific data through the corresponding setter/getter methods.

WebMessageExt is used together with WebMessagePort: WebMessagePort is responsible for establishing the message channel and sending and receiving messages, while WebMessageExt serves as the message payload transferred between different language runtimes. When using the extended interfaces [postMessageEventExt](./arkts-apis-webview-WebMessagePort.md#postmessageeventext10)/[onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10), the message carrier is the WebMessageExt object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 10.
>
> - The sample effect is subject to the actual device.

## getType<sup>10+</sup>

getType(): WebMessageType

Obtains the type of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description                                                     |
| --------------| --------------------------------------------------------- |
| [WebMessageType](./arkts-apis-webview-e.md#webmessagetype10) | Enumerates the data types supported by the [WebMessagePort](./arkts-apis-webview-WebMessagePort.md) API. |

## getString<sup>10+</sup>

getString(): string

Obtains string-type data of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| string | Data of the string type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getNumber<sup>10+</sup>

getNumber(): number

Obtains number-type data of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| number | Data of the number type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getBoolean<sup>10+</sup>

getBoolean(): boolean

Obtains Boolean-type data of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| boolean | Data of the Boolean type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getArrayBuffer<sup>10+</sup>

getArrayBuffer(): ArrayBuffer

Obtains raw binary data of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| ArrayBuffer | Raw binary data.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getArray<sup>10+</sup>

getArray(): Array\<string | number | boolean\>

Obtains array-type data of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| Array\<string \| number \| boolean\> | Data of the array type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## getError<sup>10+</sup>

getError(): Error

Obtains the error-object-type data of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type          | Description         |
| --------------| ------------- |
| Error | Data of the error object type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |

## setType<sup>10+</sup>

setType(type: WebMessageType): void

Sets the type for the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| type  | [WebMessageType](./arkts-apis-webview-e.md#webmessagetype10) | Yes   | Enumerates the data types supported by the [WebMessagePort](./arkts-apis-webview-WebMessagePort.md) API. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## setString<sup>10+</sup>

setString(message: string): void

Sets the string-type data of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | -------------------- |
| message  | string | Yes  | String type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## setNumber<sup>10+</sup>

setNumber(message: number): void

Sets the number-type data of the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | -------------------- |
| message  | number | Yes  | Data of the number type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## setBoolean<sup>10+</sup>

setBoolean(message: boolean): void

Sets the Boolean-type data for the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | -------------------- |
| message  | boolean | Yes  | Data of the Boolean type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## setArrayBuffer<sup>10+</sup>

setArrayBuffer(message: ArrayBuffer): void

Sets the raw binary data for the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | -------------------- |
| message  | ArrayBuffer | Yes  | Raw binary data.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## setArray<sup>10+</sup>

setArray(message: Array\<string | number | boolean\>): void

Sets the array-type data for the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | -------------------- |
| message  | Array\<string \| number \| boolean\> | Yes  | Data of the array type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## setError<sup>10+</sup>

setError(message: Error): void

Sets the error-object-type data for the data object. For details about the sample code, see [onMessageEventExt](./arkts-apis-webview-WebMessagePort.md#onmessageeventext10).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | -------------------- |
| message  | Error | Yes  | Data of the error object type.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 17100014 | The type and value of the message do not match. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |