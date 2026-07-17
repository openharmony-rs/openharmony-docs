# @ohos.base

## 导入模块

```TypeScript
import { Callback, BusinessError, ErrorCallback, AsyncCallback } from '@kit.BasicServicesKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AsyncCallback](arkts-basicservices-base-asynccallback-i.md) | 通用回调函数，携带错误参数和异步返回值，用于在异步操作完成时同时回传错误信息或成功数据。错误参数为[BusinessError](arkts-basicservices-base-businesserror-i.md)类型的信息。异步返回值的类型由开发者自定义，回调将返回对应类型。 |
| [BusinessError](arkts-basicservices-base-businesserror-i.md) | 错误参数。 |
| [Callback](arkts-basicservices-base-callback-i.md) | 通用回调函数，用于在异步操作完成时回传处理结果。类型由开发者自定义。 |
| [ErrorCallback](arkts-basicservices-base-errorcallback-i.md) | 通用回调函数，携带错误参数，用于在接口调用失败时回传错误信息。回调返回的信息为[BusinessError](arkts-basicservices-base-businesserror-i.md)类型的错误参数。 |

