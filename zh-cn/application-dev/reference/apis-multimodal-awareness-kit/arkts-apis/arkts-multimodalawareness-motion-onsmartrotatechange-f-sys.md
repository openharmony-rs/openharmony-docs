# onSmartRotateChange（系统接口）

## onSmartRotateChange

```TypeScript
function onSmartRotateChange(callback: Callback<SmartRotateEvent>): void
```

订阅智能旋转传感器事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-motion-function onSmartRotateChange(callback: Callback<SmartRotateEvent>): void--><!--Device-motion-function onSmartRotateChange(callback: Callback<SmartRotateEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SmartRotateEvent](arkts-multimodalawareness-motion-smartrotateevent-i-sys.md)&gt; | 是 | 回调函数，返回智能旋转方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited &lt;br&gt; device capabilities. |
| [31500001](../../apis-multimodalawareness-kit/errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, &lt;br&gt; container-related exception; 2. N-API invocation exception, invalid N-API status. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

