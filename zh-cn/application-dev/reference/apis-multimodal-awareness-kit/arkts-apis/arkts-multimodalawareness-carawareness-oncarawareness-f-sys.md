# onCarAwareness（系统接口）

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## onCarAwareness

```TypeScript
function onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?:
  CarAwarenessOptions): void
```

订阅车辆感知结果。设备不支持该能力时抛出34000002错误码，可调用getAllCapabilityList查询设备可用能力。通过callback异步返回数据。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-carAwareness-function onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?:  CarAwarenessOptions): void--><!--Device-carAwareness-function onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?:  CarAwarenessOptions): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | [Capability](arkts-multimodalawareness-carawareness-capability-e.md) | 是 | 指定订阅的感知能力类型。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md)[]&gt; | 是 | 回调函数，用于返回感知结果数据数组。 |
| options | [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | 否 | 感知能力的可选配置项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-指定能力不支持) | Specific capability not supported. |
