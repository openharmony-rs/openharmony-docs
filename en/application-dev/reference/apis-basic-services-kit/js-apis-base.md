# @ohos.base (Public Callback Information)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Base-->
<!--Owner: @majiajun518-->
<!--Designer: @majiajun518-->
<!--Tester: @jiyong_sd-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a6c31d94a76001ec2569481af36de5e521d8dabb translatedAt=2026-10-09T12:10:20.878Z pushedAt=2026-10-10T05:59:03.369Z -->

The **Base** module defines the public callback types of ArkTS APIs, including the common and error callbacks. These callbacks provide a unified asynchronous processing mechanism for processing asynchronous operation results and error messages. They can help developers simplify the asynchronous programming model and improve code readability and maintainability.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> - Since API version 12, the APIs of this module are supported in ArkTS widgets.

## Modules to Import

ArkTS example: 
```typescript
import { AsyncCallback, BusinessError, Callback, ErrorCallback } from '@kit.BasicServicesKit';
```
JS example:

```typescript
import base from '@ohos.base';
```

## Callback

Callback\<T> {

(data: T): void;

}

Defines a common callback used to return the processing result when an asynchronous operation is successful. You need to define the callback type.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Base

**Parameters**

| Name| Type| Mandatory| Description                      |
| ---- | ---- | ---- | -------------------------- |
| data | T    | Yes  | Common callback information. The type is defined by the developer. The callback is used to return data of the corresponding type.|

## ErrorCallback

ErrorCallback\<T extends Error = BusinessError> {

(err: T): void;

}

Defines a common callback that carries an error parameter. It is used to return error information when an asynchronous operation fails. The specific error code is defined by each API. For details, please refer to the error code description of the corresponding API.

The information returned by the callback is an error parameter of the [BusinessError](#businesserror) type.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Base

**Parameters**

| Name| Type| Mandatory| Description                        |
| ---- | ---- | ---- | ---------------------------- |
| err  | T    | Yes   | Common error message of a failed API call. The type defaults to BusinessError, which contains the error code and optional additional data. |

## AsyncCallback

AsyncCallback\<T, E = void> {

(err: BusinessError\<E>, data: T): void;

}

Defines a common callback that carries an error parameter and asynchronous return value. It is used to return error information or success data when an asynchronous operation is complete.

The error parameter is of the [BusinessError](#businesserror) type.

The type of the asynchronous return value is defined by the developer.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Base

**Parameters**

| Name| Type                                                        | Mandatory| Description                        |
| ---- | ------------------------------------------------------------ | ---- | ---------------------------- |
| err  | [BusinessError](#businesserror) | Yes   | Common error message of a failed API call. This parameter returns null when the API call is successful. |
| data | T                                                            | Yes  | Data returned asynchronously when the API is successfully called. The data type is defined by the developer. This parameter is unavailable when the API fails to be called.  |

## BusinessError

BusinessError\<T = void> extends Error { code: number; data?: T; }

Defines the error parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Base

| Name| Type  | Read-Only| Optional| Description                                                      |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| code | number | No| No  | Error code returned when the API fails to be called.                            |
| data<sup>9+</sup> | T      | No | Yes   | Additional error information returned when the API call fails. If this parameter is left empty, the error object does not contain additional data. |