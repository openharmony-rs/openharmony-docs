# getCameraTrackingEnabled

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## getCameraTrackingEnabled

```TypeScript
function getCameraTrackingEnabled(): boolean
```

获取相机跟踪状态

**起始版本：** 20

<!--Device-mechanicManager-function getCameraTrackingEnabled(): boolean--><!--Device-mechanicManager-function getCameraTrackingEnabled(): boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否启用摄像机跟踪 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例**

```TypeScript
// 判断当前设备是否支持对特定设备类型的机械体设备控制（isControlSupported()接口API起始版本：26.0.0）
let isSupported: boolean = mechanicManager.isControlSupported();
if (!isSupported) {
  console.info('The control function is not supported.');
  return;
}
console.info('Get tracking status');
// 调用getCameraTrackingEnabled方法获取当前摄像头跟踪是否启用
let enabled = mechanicManager.getCameraTrackingEnabled();
console.info(`'current tracking status:' ${enabled}`);
```
