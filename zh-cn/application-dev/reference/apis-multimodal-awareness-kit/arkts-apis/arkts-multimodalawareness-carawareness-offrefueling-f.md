# offRefueling

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## offRefueling

```TypeScript
function offRefueling(callback?: Callback<RefuelingInfo>): void
```

禁用加油感知。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.vehicle.MMA_ENERGYREFILL

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RefuelingInfo](arkts-multimodalawareness-carawareness-refuelinginfo-i.md)&gt; | 否 | 获取对应能力数据的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
