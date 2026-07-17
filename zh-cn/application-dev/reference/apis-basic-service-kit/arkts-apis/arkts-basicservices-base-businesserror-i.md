# BusinessError

错误参数。

**继承/实现关系：** BusinessError extends [Error](Error)

**起始版本：** 6

<!--Device-unnamed-export interface BusinessError<T = void> extends Error--><!--Device-unnamed-export interface BusinessError<T = void> extends Error-End-->

**系统能力：** SystemCapability.Base

## 导入模块

```TypeScript
import { Callback, BusinessError, ErrorCallback, AsyncCallback } from '@kit.BasicServicesKit';
```

## code

```TypeScript
code: number
```

接口调用失败返回的错误码信息。

**类型：** number

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BusinessError-code: number--><!--Device-BusinessError-code: number-End-->

**系统能力：** SystemCapability.Base

## data

```TypeScript
data?: T
```

接口调用失败时返回的附加错误信息。如果不填，则错误对象不包含附加数据。

**类型：** T

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BusinessError-data?: T--><!--Device-BusinessError-data?: T-End-->

**系统能力：** SystemCapability.Base

