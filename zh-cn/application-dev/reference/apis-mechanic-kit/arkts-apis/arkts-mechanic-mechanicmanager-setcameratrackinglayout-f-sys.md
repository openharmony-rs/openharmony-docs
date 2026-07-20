# setCameraTrackingLayout（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="setcameratrackinglayout"></a>
## setCameraTrackingLayout

```TypeScript
function setCameraTrackingLayout(trackingLayout: CameraTrackingLayout): void
```

Sets the camera tracking layout for this mechanical device.

**起始版本：** 20

<!--Device-mechanicManager-function setCameraTrackingLayout(trackingLayout: CameraTrackingLayout): void--><!--Device-mechanicManager-function setCameraTrackingLayout(trackingLayout: CameraTrackingLayout): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| trackingLayout | [CameraTrackingLayout](arkts-mechanic-mechanicmanager-cameratrackinglayout-e.md) | 是 | Camera tracking layout. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |

**示例：**

```TypeScript
console.info('Set layout');
mechanicManager.setCameraTrackingLayout(mechanicManager.CameraTrackingLayout.LEFT);
console.info('Set layout successful');

```

