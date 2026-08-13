# onHoverHandChange（系统接口）

## onHoverHandChange

```TypeScript
function onHoverHandChange(detectionArea: HoverHandDetectionArea, callback: Callback<HoverHandAction>): void
```

订阅悬停手势事件，并立即开始5秒检测。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-motion-function onHoverHandChange(detectionArea: HoverHandDetectionArea, callback: Callback<HoverHandAction>): void--><!--Device-motion-function onHoverHandChange(detectionArea: HoverHandDetectionArea, callback: Callback<HoverHandAction>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detectionArea | [HoverHandDetectionArea](arkts-multimodalawareness-motion-hoverhanddetectionarea-i-sys.md) | 是 | 悬停手势矩形检测区域。 &lt;br&gt; 重复调用将覆盖之前设置的检测区域。 &lt;br&gt; 若检测区域超出屏幕边界，默认检测重叠区域。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[HoverHandAction](arkts-multimodalawareness-motion-hoverhandaction-e-sys.md)&gt; | 是 | 回调函数，返回悬停手势动作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited &lt;br&gt; device capabilities. |
| [31500001](../../apis-multimodalawareness-kit/errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, &lt;br&gt; container-related exception; 2. N-API invocation exception, invalid N-API status. |
| [31500002](../../apis-multimodalawareness-kit/errorcode-motion.md#31500002-订阅失败) | Subscription failed. Possible causes: 1. Callback registration failure; &lt;br&gt; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC &lt;br&gt; request exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |


## onHoverHandChange

```TypeScript
function onHoverHandChange(
    detectionArea: HoverHandDetectionArea, duration: int, callback: Callback<HoverHandAction>): void
```

订阅悬停手势事件，并立即开始检测。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-motion-function onHoverHandChange(    detectionArea: HoverHandDetectionArea, duration: int, callback: Callback<HoverHandAction>): void--><!--Device-motion-function onHoverHandChange(    detectionArea: HoverHandDetectionArea, duration: int, callback: Callback<HoverHandAction>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detectionArea | [HoverHandDetectionArea](arkts-multimodalawareness-motion-hoverhanddetectionarea-i-sys.md) | 是 | 悬停手势矩形检测区域。 &lt;br&gt; 重复调用将覆盖之前设置的检测区域。 &lt;br&gt; 若检测区域超出屏幕边界，默认检测重叠区域。 |
| duration | int | 是 | 检测时长。单位：秒，取值范围为[1,10]的整数。 &lt;br&gt; 时长到期后自动结束订阅，需重新调用以重启检测。 &lt;br&gt; 悬停手势事件为高功耗事件，建议开发者根据需要设置时长。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[HoverHandAction](arkts-multimodalawareness-motion-hoverhandaction-e-sys.md)&gt; | 是 | 回调函数，返回悬停手势动作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited &lt;br&gt; device capabilities. |
| [31500001](../../apis-multimodalawareness-kit/errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, &lt;br&gt; container-related exception; 2. N-API invocation exception, invalid N-API status. |
| [31500002](../../apis-multimodalawareness-kit/errorcode-motion.md#31500002-订阅失败) | Subscription failed. Possible causes: 1. Callback registration failure; &lt;br&gt; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC &lt;br&gt; request exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

