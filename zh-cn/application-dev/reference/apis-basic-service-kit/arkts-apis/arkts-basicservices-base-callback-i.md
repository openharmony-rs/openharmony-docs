# Callback

通用回调函数，用于在异步操作完成时回传处理结果。类型由开发者自定义。

**起始版本：** 6

<!--Device-unnamed-export interface Callback<T>--><!--Device-unnamed-export interface Callback<T>-End-->

**系统能力：** SystemCapability.Base

## 导入模块

```TypeScript
import { Callback, BusinessError, ErrorCallback, AsyncCallback } from '@kit.BasicServicesKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
(data: T): void
```

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Callback-(data: T): void--><!--Device-Callback-(data: T): void-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | T | 是 | 接口调用时的公共回调信息。类型由开发者自定义，回调成功时将返回对应类型的数据。失败则不返回数据。 |

