# offPickupChange（系统接口）

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## offPickupChange

```TypeScript
function offPickupChange(callback?: Callback<PickupEvent>): void
```

取消订阅拾取传感器事件。需先调用onPickupChange订阅后才能取消，若未订阅则不生效。当应用不再需要监听拾取事件时使用如页面销毁、应用进入后台或暂停相关功能时，应调用此接口取消订阅以释放系统资源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-motion-function offPickupChange(callback?: Callback<PickupEvent>): void--><!--Device-motion-function offPickupChange(callback?: Callback<PickupEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PickupEvent](arkts-multimodalawareness-motion-pickupevent-e-sys.md)&gt; | 否 | 要注销的回调函数。若不填，则取消该拾起事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [31500001](../errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, <br> container-related exception; 2. N-API invocation exception, invalid N-API status. |
