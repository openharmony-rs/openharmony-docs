# @ohos.base (Public Callback Information)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Base-->
<!--Owner: @majiajun518-->
<!--Designer: @majiajun518-->
<!--Tester: @jiyong_sd-->
<!--Adviser: @fang-jinxu-->

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

Defines a common callback.

You can set **data** to customize the data type of the information returned by the callback.

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

Defines a common callback that carries an error parameter.

The information returned by the callback is of the [BusinessError](#businesserror) type.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Base

**Parameters**

| Name| Type| Mandatory| Description                        |
| ---- | ---- | ---- | ---------------------------- |
| err  | T    | Yes  | Common error message returned when the API fails to be called.|

## AsyncCallback

AsyncCallback\<T, E = void> {

(err: BusinessError\<E>, data: T): void;

}

Defines a common callback that carries an error parameter and asynchronous return value.

The error parameter is of the [BusinessError](#businesserror) type.

The type of the asynchronous return value is defined by the developer.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Base

**Parameters**

| Name| Type                                                        | Mandatory| Description                        |
| ---- | ------------------------------------------------------------ | ---- | ---------------------------- |
| err  | [BusinessError](#businesserror) | Yes  | Common error message returned when the API fails to be called.|
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
| data | T      | No| Yes  | Error message returned when the API fails to be called. If this parameter is left empty, the error object does not contain additional data.|
