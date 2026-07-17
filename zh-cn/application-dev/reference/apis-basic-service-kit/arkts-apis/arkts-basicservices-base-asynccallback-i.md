# AsyncCallback

通用回调函数，携带错误参数和异步返回值，用于在异步操作完成时同时回传错误信息或成功数据。错误参数为[BusinessError](arkts-basicservices-base-businesserror-i.md)类型的信息。异步返回值的类型由开发者自定义，回调将返回对应类型。

**起始版本：** 6

<!--Device-unnamed-export interface AsyncCallback<T, E = void>--><!--Device-unnamed-export interface AsyncCallback<T, E = void>-End-->

**系统能力：** SystemCapability.Base

## 导入模块

```TypeScript
import { Callback, BusinessError, ErrorCallback, AsyncCallback } from '@kit.BasicServicesKit';
```

## constructor

```TypeScript
(err: BusinessError<E>, data: T): void
```

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-AsyncCallback-(err: BusinessError<E>, data: T): void--><!--Device-AsyncCallback-(err: BusinessError<E>, data: T): void-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | [BusinessError](arkts-basicservices-base-businesserror-i.md)<E> | 是 | 接口调用失败的公共错误信息。接口调用成功时，此参数返回null。 |
| data | T | 是 | 接口调用成功时的异步返回数据，类型由开发者自定义。接口调用失败时，此参数不返回。 |

