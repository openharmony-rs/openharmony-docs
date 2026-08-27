# @ohos.base(公共回调信息)

本模块定义了OpenHarmony ArkTS接口的公共回调类型，包括接口调用时出现的公共回调和公共错误信息。
 这些回调类型为开发者提供了统一的异步处理机制，适用于需要处理异步操作结果、错误信息回传等场景，可以帮助开发者简化异步编程模型，提高代码的可读性和可维护性。
 > **说明：**
 >
 > - 本模块首批接口从API version 6 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
 > - 从API version 12开始，本模块接口支持在ArkTS卡片中使用。


## 导入模块

```TypeScript
import { AsyncCallback, BusinessError, Callback, ErrorCallback } from '@kit.BasicServicesKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AsyncCallback(公共回调信息)](arkts-basicservices-base-asynccallback-i.md) | 通用回调函数，携带错误参数和异步返回值，用于在异步操作完成时同时回传错误信息或成功数据。错误参数为[BusinessError](arkts-basicservices-base-businesserror-i.md)类型。异步返回值的类型由开发者自定义，回调将返回对应类型的信息。 |
| [BusinessError(公共回调信息)](arkts-basicservices-base-businesserror-i.md) | 错误参数，继承自Error类，用于在接口调用失败时传递标准化的错误信息，包含错误码和可选的附加信息。 |
| [Callback(公共回调信息)](arkts-basicservices-base-callback-i.md) | 通用回调函数，用于在异步操作成功完成时回传处理结果。类型由开发者自定义。 |
| [ErrorCallback(公共回调信息)](arkts-basicservices-base-errorcallback-i.md) | 通用回调函数，携带错误参数，用于在异步操作失败时回传错误信息。具体错误码值由各接口定义，请参考对应接口的错误码说明。回调返回的信息为[BusinessError](arkts-basicservices-base-businesserror-i.md)类型的错误参数。 |
