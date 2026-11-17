# onHoverHandChange（系统接口）

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## onHoverHandChange

```TypeScript
function onHoverHandChange(detectionArea: HoverHandDetectionArea, callback: Callback<HoverHandAction>): void
```

订阅悬浮手事件，并立即开启悬浮手事件检测，检测时长为五秒。需与offHoverHandChange配对使用，使用完毕后应调用offHoverHandChange取消订阅以释放系统资源。

> **说明：** 
> 
> 检测时长到期后，悬浮手事件检测将自动终止，不再上报悬浮手事件，需要开发者再次调用订阅此接口以重新开启检测。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-motion-function onHoverHandChange(detectionArea: HoverHandDetectionArea, callback: Callback<HoverHandAction>): void--><!--Device-motion-function onHoverHandChange(detectionArea: HoverHandDetectionArea, callback: Callback<HoverHandAction>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detectionArea | [HoverHandDetectionArea](arkts-multimodalawareness-motion-hoverhanddetectionarea-i-sys.md) | 是 | 悬停手势矩形检测区域。<br> 重复调用将覆盖之前设置的检测区域。<br> 若检测区域超出屏幕边界，默认检测重叠区域。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HoverHandAction](arkts-multimodalawareness-motion-hoverhandaction-e-sys.md)&gt; | 是 | 回调函数，返回悬停手势动作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br> 1. The hardware does not support the capability; <br> 2. The chip does not support the capability; <br> 3. A dependent service feature is not supported. |
| [31500001](../errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, <br> container-related exception; 2. N-API invocation exception, invalid N-API status. |
| [31500002](../errorcode-motion.md#31500002-订阅失败) | Subscription failed. Possible causes: 1. Callback registration failure; <br> 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC <br> request exception. |


## onHoverHandChange

```TypeScript
function onHoverHandChange(
    detectionArea: HoverHandDetectionArea, duration: number, callback: Callback<HoverHandAction>): void
```

订阅悬浮手事件，并立即开启悬浮手事件检测，支持指定检测时长。需与offHoverHandChange配对使用，使用完毕后应调用offHoverHandChange取消订阅以释放系统资源。

> **说明：** 
> 
> 检测时长到期后，悬浮手事件检测将自动终止，不再上报悬浮手事件，需要开发者再次调用订阅此接口以重新开启检测。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-motion-function onHoverHandChange(    detectionArea: HoverHandDetectionArea, duration: int, callback: Callback<HoverHandAction>): void--><!--Device-motion-function onHoverHandChange(    detectionArea: HoverHandDetectionArea, duration: int, callback: Callback<HoverHandAction>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detectionArea | [HoverHandDetectionArea](arkts-multimodalawareness-motion-hoverhanddetectionarea-i-sys.md) | 是 | 悬停手势矩形检测区域。<br> 重复调用将覆盖之前设置的检测区域。<br> 若检测区域超出屏幕边界，默认检测重叠区域。 |
| duration | number | 是 | 检测时长。单位：秒，取值范围为[1,10]的整数。<br> 时长到期后自动结束订阅，需重新调用以重启检测。<br> 悬停手势事件为高功耗事件，建议开发者根据需要设置时长。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HoverHandAction](arkts-multimodalawareness-motion-hoverhandaction-e-sys.md)&gt; | 是 | 回调函数，返回悬停手势动作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br> 1. The hardware does not support the capability; <br> 2. The chip does not support the capability; <br> 3. A dependent service feature is not supported. |
| [31500001](../errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, <br> container-related exception; 2. N-API invocation exception, invalid N-API status. |
| [31500002](../errorcode-motion.md#31500002-订阅失败) | Subscription failed. Possible causes: 1. Callback registration failure; <br> 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC <br> request exception. |
