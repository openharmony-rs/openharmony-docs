# offCarAwareness（系统接口）

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## offCarAwareness

```TypeScript
function offCarAwareness(capability: Capability, callback?: Callback<CarAwarenessInfo[]>, options?:
  CarAwarenessOptions): void
```

取消订阅汽车感知结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | Capability | 是 | 表示特定能力。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md)[]&gt; | 否 | Callback used to return the corresponding capability data. |
| options | [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | 否 | Indicates options to specific capability. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system capability. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
