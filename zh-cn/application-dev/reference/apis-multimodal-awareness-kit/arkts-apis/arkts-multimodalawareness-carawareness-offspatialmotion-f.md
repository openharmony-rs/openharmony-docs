# offSpatialMotion

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## offSpatialMotion

```TypeScript
function offSpatialMotion(callback?: Callback<SpatialMotionInfo>): void
```

关闭空间动作感知，订阅空间动作感知结果。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.vehicle.MMA_SPATIALACTION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SpatialMotionInfo](arkts-multimodalawareness-carawareness-spatialmotioninfo-i.md)&gt; | 否 | 获取对应能力数据的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
