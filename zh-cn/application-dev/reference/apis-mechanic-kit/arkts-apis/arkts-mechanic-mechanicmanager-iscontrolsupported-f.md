# isControlSupported

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## isControlSupported

```TypeScript
function isControlSupported(mechDeviceType?: MechDeviceType): boolean
```

判断当前设备是否支持某类设备的具身控制

**起始版本：** 26.0.0

<!--Device-mechanicManager-function isControlSupported(mechDeviceType?: MechDeviceType): boolean--><!--Device-mechanicManager-function isControlSupported(mechDeviceType?: MechDeviceType): boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechDeviceType | [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e.md) | 否 | 关联的设备类型<br>默认值:如果未提供该参数，则代表所有类型设备，只要支持其中一种以上则返回支持 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns whether control is supported. |

**示例：**

```TypeScript
console.info('Check whether control is supported');
// 调用isControlSupported方法，传入MechDeviceType.GIMBAL_DEVICE类型，判断是否支持云台设备控制
let isSupported = mechanicManager.isControlSupported(mechanicManager.MechDeviceType.GIMBAL_DEVICE);
console.info(`isSupported: ${isSupported}`);

```

