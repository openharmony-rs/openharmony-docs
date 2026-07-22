# getState

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## getState

```TypeScript
function getState(): NearlinkState
```

获取星闪状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-manager-function getState(): NearlinkState--><!--Device-manager-function getState(): NearlinkState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md) | 返回NearLink状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

