# isControlSupported

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="iscontrolsupported"></a>
## isControlSupported

```TypeScript
function isControlSupported(mechDeviceType?: MechDeviceType): boolean
```

Checks whether the current device supports embodied control for a specific type of device.

**起始版本：** 26.0.0

<!--Device-mechanicManager-function isControlSupported(mechDeviceType?: MechDeviceType): boolean--><!--Device-mechanicManager-function isControlSupported(mechDeviceType?: MechDeviceType): boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechDeviceType | [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e.md) | 否 | Associated device type.<br>Default: If this parameter is not provided, it represents all device types. As long as one or more types are supported, the result returned will be supported. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns whether embodied control is supported. |

**示例：**

```TypeScript
console.info('Check whether control is supported');
// 调用isControlSupported方法，传入MechDeviceType.GIMBAL_DEVICE类型，判断是否支持云台设备控制
let isSupported = mechanicManager.isControlSupported(mechanicManager.MechDeviceType.GIMBAL_DEVICE);
console.info(`isSupported: ${isSupported}`);

```

