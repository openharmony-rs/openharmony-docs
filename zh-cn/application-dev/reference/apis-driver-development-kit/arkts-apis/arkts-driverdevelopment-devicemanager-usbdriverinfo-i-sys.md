# USBDriverInfo（系统接口）

USB设备驱动详细信息，继承自[DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md)。

**继承/实现关系：** USBDriverInfo extends [DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md)

**起始版本：** 12

<!--Device-deviceManager-interface USBDriverInfo extends DriverInfo--><!--Device-deviceManager-interface USBDriverInfo extends DriverInfo-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## productIdList

```TypeScript
productIdList: Array<number>
```

驱动支持的USB设备product ID列表。

**类型：** Array&lt;number&gt;

**起始版本：** 12

<!--Device-USBDriverInfo-productIdList: Array<int>--><!--Device-USBDriverInfo-productIdList: Array<int>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## vendorIdList

```TypeScript
vendorIdList: Array<number>
```

驱动支持的USB设备vendor ID列表。

**类型：** Array&lt;number&gt;

**起始版本：** 12

<!--Device-USBDriverInfo-vendorIdList: Array<int>--><!--Device-USBDriverInfo-vendorIdList: Array<int>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

