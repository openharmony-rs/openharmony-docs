# onSmartRotateChange（系统接口）

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## onSmartRotateChange

```TypeScript
function onSmartRotateChange(callback: Callback<SmartRotateEvent>): void
```

订阅智能旋转传感器事件。当设备物理方向变化或智能算法调整逻辑方向时触发该事件并回调，当需要实现智能屏幕旋转等场景时使用。需与offSmartRotateChange配对使用，使用完毕后应调用offSmartRotateChange取消订阅以释放系统资源。

与onRotateChange相比，onSmartRotateChange不仅返回重力传感器检测的物理方向，还提供智能算法调整后的逻辑方向

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-motion-function onSmartRotateChange(callback: Callback<SmartRotateEvent>): void--><!--Device-motion-function onSmartRotateChange(callback: Callback<SmartRotateEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SmartRotateEvent](arkts-multimodalawareness-motion-smartrotateevent-i-sys.md)&gt; | 是 | 回调函数，返回智能旋转方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br> 1. The hardware does not support the capability; <br> 2. The chip does not support the capability; <br> 3. A dependent service feature is not supported. |
| [31500001](../errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, <br> container-related exception; 2. N-API invocation exception, invalid N-API status. |
