# getCameraTrackingEnabled

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="getcameratrackingenabled"></a>
## getCameraTrackingEnabled

```TypeScript
function getCameraTrackingEnabled(): boolean
```

Checks whether camera tracking is enabled for this mechanical device.

**起始版本：** 20

<!--Device-mechanicManager-function getCameraTrackingEnabled(): boolean--><!--Device-mechanicManager-function getCameraTrackingEnabled(): boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Enabled status. The value true means that camera tracking is enabled, and false means the opposite. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Get tracking status');
// 调用getCameraTrackingEnabled方法获取当前摄像头跟踪是否启用
let enabled = mechanicManager.getCameraTrackingEnabled();
console.info(`'current tracking status:' ${enabled}`);

```

