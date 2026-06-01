# @ohos.base (Public Callback Information)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Base-->
<!--Owner: @majiajun518-->
<!--Designer: @majiajun518-->
<!--Tester: @jiyong_sd-->
<!--Adviser: @fang-jinxu-->

The **Base** module defines the public callback types of ArkTS APIs, including the common and error callbacks.

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

**Atomic service API:** This API can be used in atomic services since API version 11. This API applies only to ArkTS-Dyn.

**System capability**: SystemCapability.Base

**ArkTS-Dyn start version**: 6

**ArkTS-Sta start version**: 23

| Name| Type| Mandatory| Description                      |
| ---- | ---- | ---- | -------------------------- |
| data | T    | Yes  | Common callback information.|

## ErrorCallback

ErrorCallback\<T extends Error = BusinessError> {

(err: T): void;

}

Defines a common callback that carries an error parameter.

The information returned by the callback is of the [BusinessError](#businesserror) type.

**Atomic service API:** This API can be used in atomic services since API version 11. This API applies only to ArkTS-Dyn.

**System capability**: SystemCapability.Base

**ArkTS-Dyn start version**: 6

**ArkTS-Sta start version**: 23

**Parameters**

| Name| Type| Mandatory| Description                        |
| ---- | ---- | ---- | ---------------------------- |
| err  | T    | Yes  | Common error information about the API invoking failure.|

## AsyncCallback

**ArkTS-Dyn:**  

AsyncCallback\<T, E = void> {

(err: BusinessError\<E>, data: T): void;

}

**ArkTS-Sta:**  

AsyncCallback\<T, E = void> = (err: BusinessError\<E> | null, data: T | undefined) => void

Defines a common callback that carries an error parameter and asynchronous return value.

The error parameter is of the [BusinessError](#businesserror) type.

The type of the asynchronous return value is defined by the developer.

**Atomic service API:** This API can be used in atomic services since API version 11. This API applies only to ArkTS-Dyn.

**System capability**: SystemCapability.Base

**ArkTS-Dyn start version**: 6

**ArkTS-Sta start version**: 23

| Name| Type                                                        | Mandatory| Description                        |
| ---- | ------------------------------------------------------------ | ---- | ---------------------------- |
| err  | [BusinessError](#businesserror) | Yes  | Common error information about the API invoking failure.|
| data | T                                                            | Yes  | Common callback information.  |

## BusinessError

**ArkTS-Dyn:**  
BusinessError\<T = void> extends Error {

code: number;

data?: T;

}

| Name| Type   | Read-Only| Optional| Description                                                      |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| code | number | No  | No | Common error information about the API invoking failure.   |
| data | T      | No  | Yes  | Common callback information. If this parameter is left empty, no related information is returned.|


**ArkTS-Sta:**  

BusinessError\<T = void> extends Error {

public data?: T;

}

| Name| Type   | Read-Only| Optional| Description                                                      |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| data | T      | No  | Yes  | Common callback information. If this parameter is left empty, no related information is returned.|

**Atomic service API:** This API can be used in atomic services since API version 11. This API applies only to ArkTS-Dyn.

**System capability**: SystemCapability.Base

**ArkTS-Dyn start version**: 6

**ArkTS-Sta start version**: 23

### constructor<sup>23+</sup>    

constructor()    

Defines a constructor used to create a **BusinessError** object. 

**System capability**: SystemCapability.Base 

**ArkTS mode**: This API applies only to ArkTS-Sta.

### constructor<sup>23+</sup>    

constructor(code: int, error: Error)    

Defines a constructor used to create a **BusinessError** object.

**System capability**: SystemCapability.Base 

**ArkTS mode**: This API applies only to ArkTS-Sta.

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| code | int | Yes  | Common error information about the API invoking failure.|
| error | Error | Yes  | Defines the error parameter.|

> **NOTE**
>
> Scheduled for deprecation You are advised to use constructor(code: int, message: string, data?: T) instead.


### constructor<sup>23+</sup>      

constructor(code: int, data: T, error: Error)          

Defines a constructor used to create a **BusinessError** object.   

**System capability**: SystemCapability.Base     

**ArkTS mode**: This API applies only to ArkTS-Sta.  

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| code | int | Yes  | Common error information about the API invoking failure.|
| data | T | Yes  | Common callback information.|
| error | Error | Yes  | Defines the error parameter.|

> **NOTE**
>
> Scheduled for deprecation You are advised to use constructor(code: int, message: string, data?: T) instead.


### constructor<sup>23+</sup>    

constructor(code: int, message: string, data?: T)   

Defines a constructor used to create a **BusinessError** object.

**System capability**: SystemCapability.Base   

**ArkTS mode**: This API applies only to ArkTS-Sta.

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| code | int | Yes  | Common error information about the API invoking failure.|
| message | string | Yes  | Error message returned when the API call fails.|
| data | T | No  | Common callback information.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

interface ErrorDataType {
    url: string;
}

const businessError = new BusinessError<ErrorDataType>(201, 'no permission', {
    url: 'http://'
});
```

## RecordData

RecordData = undefined \| null \| Object \| Record\<string, [RecordData](#recorddata)> \| Array\<[RecordData](#recorddata)>

**RecordData** is a union type used for object structures with uncertain levels and quantities at each level.

**System capability**: SystemCapability.Base

**ArkTS mode**: This API applies only to ArkTS-Sta.

**ArkTS-Sta start version**: 23
