# @ohos.base (公共回调信息)

本模块定义了OpenHarmony ArkTS接口的公共回调类型，包括接口调用时出现的公共回调和公共错误信息。

> **说明：**
> 
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从 API version 6 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> - 本模块ArkTS-Dyn接口从API version 12开始支持在ArkTS卡片中使用。

## 导入模块

```
import { AsyncCallback, BusinessError, Callback, ErrorCallback, RecordData } from '@kit.BasicServicesKit';
```

## Callback

```
Callback<T> {

(data: T): void;

}
```

通用回调函数。

开发者在使用时，可自定义data的类型，回调将返回对应类型的信息。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Base

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 20

| 名称 | 类型 | 必填 | 说明                       |	
| ---- | ---- | ---- | -------------------------- |	
| data | T    | 是   | 接口调用时的公共回调信息。 |

## ErrorCallback

```
ErrorCallback<T extends Error = BusinessError> {

(err: T): void;

}
```

通用回调函数，携带错误参数。

回调返回的信息为[BusinessError](#businesserror)类型的信息。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Base

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 20

**参数：**

| 名称 | 类型 | 必填 | 说明                         |	
| ---- | ---- | ---- | ---------------------------- |	
| err  | T    | 是   | 接口调用失败的公共错误信息。 |

## AsyncCallback

**ArkTS-Dyn：**   

```
AsyncCallback<T, E = void> {

(err: BusinessError<E> , data: T): void;

}
```

**ArkTS-Sta：**   

```
AsyncCallback<T, E = void> = (err: BusinessError<E> | null, data: T | undefined)=> void
```

通用回调函数，携带错误参数和异步返回值。

错误参数为[BusinessError](#businesserror)类型的信息。

异步返回值的类型由开发者自定义，回调将返回对应类型的信息。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Base

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 20

| 名称 | 类型                                                          | 必填 | 说明                         |
| ---- | ------------------------------------------------------------ | ---- | ---------------------------- |
| err  | ArkTS-Dyn: [BusinessError\<E>](#businesserror) </br> ArkTS-Sta:    [BusinessError\<E>](#businesserror) \| null | 是   | 接口调用失败的公共错误信息。 |
| data | ArkTS-Dyn: T </br> ArkTS-Sta: T \| undefined                                                            | 是   | 接口调用时的公共回调信息。   |

## BusinessError  

**ArkTS-Dyn：**   

BusinessError\<T = void> extends Error {

code: number;

data?: T;
}

| 名称 | 类型    | 只读 | 可选 | 说明                                                       |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| code | number | 否   | 否  | 接口调用失败返回的错误码信息。   
| data | T      | 否   | 是   | 接口调用时的公共回调信息。如果不填，则回调不返回相关信息。 |


**ArkTS-Sta：**   

BusinessError\<T = void> extends Error {

public data?: T;
}

| 名称 | 类型    | 只读 | 可选 | 说明                                                       |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| data | T      | 否   | 是   | 接口调用时的公共回调信息。如果不填，则回调不返回相关信息。 |


**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Base   

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 20

### constructor<sup>20+</sup>    

constructor()    

BusinessError的构造函数。  

**系统能力：** SystemCapability.Base  

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

### constructor<sup>20+</sup>    

constructor(code: int, error: Error)    

BusinessError的构造函数。

**系统能力：** SystemCapability.Base  

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**参数：**

| 参数名    | 类型                                      | 必填 | 说明                               |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| code | int | 是   | 接口调用失败返回的错误码信息。 |
| error | Error | 是   | 错误参数。 |

> **说明：**
>
> 后续将废弃。建议使用 constructor(code: int, message: string, data?: T) 代替。


### constructor<sup>20+</sup>      

constructor(code: int, data: T, error: Error)          

BusinessError的构造函数。    

**系统能力：** SystemCapability.Base      

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。   

**参数：**

| 参数名    | 类型                                      | 必填 | 说明                               |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| code | int | 是   | 接口调用失败返回的错误码信息。 |
| data | T | 是   | 接口调用时的公共回调信息。 |
| error | Error | 是   | 错误参数。 |

> **说明：**
>
> 后续将废弃。建议使用 constructor(code: int, message: string, data?: T) 代替。


### constructor<sup>20+</sup>    

constructor(code: int, message: string, data?: T)   

BusinessError的构造函数。

**系统能力：** SystemCapability.Base    

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**参数：**

| 参数名    | 类型                                      | 必填 | 说明                               |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| code | int | 是   | 接口调用失败返回的错误码信息。 |
| message | string | 是   | 接口调用失败返回的错误信息描述。 |
| data | T | 否   | 接口调用时的公共回调信息。 |

**示例：**

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

RecordData = undefined \| null \| Object \| Record\<string, [RecordData](#RecordData)> \| Array\<[RecordData](#RecordData)>

RecordData 是一个联合类型，用于层级和每层数量都不确定的对象结构。

**系统能力：** SystemCapability.Base

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 20