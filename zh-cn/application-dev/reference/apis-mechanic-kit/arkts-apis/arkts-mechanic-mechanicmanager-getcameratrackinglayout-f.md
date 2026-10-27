# getCameraTrackingLayout

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## getCameraTrackingLayout

```TypeScript
function getCameraTrackingLayout(): CameraTrackingLayout
```

获取当前摄像头跟踪布局

**起始版本：** 20

<!--Device-mechanicManager-function getCameraTrackingLayout(): CameraTrackingLayout--><!--Device-mechanicManager-function getCameraTrackingLayout(): CameraTrackingLayout-End-->

**系统能力：** SystemCapability.Mechanic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraTrackingLayout](arkts-mechanic-mechanicmanager-cameratrackinglayout-e.md) | 返回当前布局 |

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
console.info('Query layout');
// 调用getCameraTrackingLayout方法获取当前摄像头跟踪布局
let layout = mechanicManager.getCameraTrackingLayout();
console.info(`'Succeeded in querying layout, current layout:' ${layout}`);
```
