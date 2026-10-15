# updateSpatialActionEnableStatus（系统接口）

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## updateSpatialActionEnableStatus

```TypeScript
function updateSpatialActionEnableStatus(event: number): void
```

更新空间动作感知的启停状态。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.vehicle.MMA_SPATIALACTION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-carAwareness-function updateSpatialActionEnableStatus(event: number): void--><!--Device-carAwareness-function updateSpatialActionEnableStatus(event: number): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | number | 是 | 启停状态值。0：结束1：开始取值应为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-指定能力不支持) | Specific capability not supported. |
