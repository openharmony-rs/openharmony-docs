# AsyncCallback

The ResourceManager callback.

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [base:AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)

<!--Device-resourceManager-export interface AsyncCallback<T>--><!--Device-resourceManager-export interface AsyncCallback<T>-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## 导入模块

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
(err: Error, data: T): void
```

异步回调函数，携带错误参数和异步返回值。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [base:AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)

<!--Device-AsyncCallback-(err: Error, data: T): void--><!--Device-AsyncCallback-(err: Error, data: T): void-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | Error | 是 | 接口调用失败的错误信息。 |
| data | T | 是 | 接口调用时的回调信息。 |

