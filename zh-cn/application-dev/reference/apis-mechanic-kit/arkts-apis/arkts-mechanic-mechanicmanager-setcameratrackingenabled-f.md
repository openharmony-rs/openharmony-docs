# setCameraTrackingEnabled

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## setCameraTrackingEnabled

```TypeScript
function setCameraTrackingEnabled(isEnabled: boolean): void
```

启用或禁用摄像机跟踪

**起始版本：** 20

<!--Device-mechanicManager-function setCameraTrackingEnabled(isEnabled: boolean): void--><!--Device-mechanicManager-function setCameraTrackingEnabled(isEnabled: boolean): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 是否启用摄像机跟踪 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |

**示例**

```TypeScript
// 判断当前设备是否支持对特定设备类型的机械体设备控制（isControlSupported()接口API起始版本：26.0.0）
let isSupported: boolean = mechanicManager.isControlSupported();
if (!isSupported) {
  console.info('The control function is not supported.');
  return;
}
console.info('Enable tracing');
// 调用setCameraTrackingEnabled方法，参数true表示启用摄像头跟踪
mechanicManager.setCameraTrackingEnabled(true);
console.info('Succeeded in enabling tracking.');
```
