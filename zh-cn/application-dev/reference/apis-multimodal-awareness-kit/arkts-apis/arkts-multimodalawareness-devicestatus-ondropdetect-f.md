# onDropDetect

## 导入模块

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## onDropDetect

```TypeScript
function onDropDetect(callback: Callback<DropDetectionStatus>): void
```

订阅跌落检测事件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceStatus-function onDropDetect(callback: Callback<DropDetectionStatus>): void--><!--Device-deviceStatus-function onDropDetect(callback: Callback<DropDetectionStatus>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DropDetectionStatus](arkts-multimodalawareness-devicestatus-dropdetectionstatus-e.md)&gt; | 是 | 用于接收设备跌落事件的回调。同一回调重复订阅时抛出错误32500002。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Failed due to limited device capabilities. |
| [32500001](../errorcode-deviceStatus.md#32500001-服务异常) | Service exception. |
| [32500002](../errorcode-deviceStatus.md#32500002-订阅失败) | Subscription failed. |
