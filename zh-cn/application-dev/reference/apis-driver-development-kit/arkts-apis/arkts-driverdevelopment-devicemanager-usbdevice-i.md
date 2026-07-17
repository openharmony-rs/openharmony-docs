# USBDevice

USB设备信息，继承自[Device](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)。

**继承/实现关系：** USBDevice extends [Device](arkts-driverdevelopment-devicemanager-device-i.md)

**起始版本：** 10

<!--Device-deviceManager-interface USBDevice extends Device--><!--Device-deviceManager-interface USBDevice extends Device-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## productId

```TypeScript
productId: number
```

USB设备Product ID。

**类型：** number

**起始版本：** 10

<!--Device-USBDevice-productId: int--><!--Device-USBDevice-productId: int-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

## vendorId

```TypeScript
vendorId: number
```

USB设备Vendor ID。

**类型：** number

**起始版本：** 10

<!--Device-USBDevice-vendorId: int--><!--Device-USBDevice-vendorId: int-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

