# onRefueling

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## onRefueling

```TypeScript
function onRefueling(callback: Callback<RefuelingInfo>): void
```

订阅补能状态感知结果。设备不支持该能力时抛出34000002错误码，可调用 getAllCapabilityList查询设备可用能力。通过callback异步返回数据。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.vehicle.MMA_ENERGYREFILL

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-carAwareness-function onRefueling(callback: Callback<RefuelingInfo>): void--><!--Device-carAwareness-function onRefueling(callback: Callback<RefuelingInfo>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RefuelingInfo](arkts-multimodalawareness-carawareness-refuelinginfo-i.md)&gt; | 是 | 回调函数，用于返回补能识别数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-指定能力不支持) | Specific capability not supported. |
