# USBDriverInfo (System API)

```TypeScript
interface USBDriverInfo extends DriverInfo
```

Defines detailed information about the USB device driver. It is inherited from [DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md).

**Inheritance/Implementation:** USBDriverInfo extends [DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md)

**Since:** 12

<!--Device-deviceManager-interface USBDriverInfo extends DriverInfo--><!--Device-deviceManager-interface USBDriverInfo extends DriverInfo-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## productIdList

```TypeScript
productIdList: Array<number>
```

Product ID list of the USB devices supported by the driver.

**Type:** Array&lt;number&gt;

**Since:** 12

<!--Device-USBDriverInfo-productIdList: Array<int>--><!--Device-USBDriverInfo-productIdList: Array<int>-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## vendorIdList

```TypeScript
vendorIdList: Array<number>
```

Vendor ID list of the USB devices supported by the driver.

**Type:** Array&lt;number&gt;

**Since:** 12

<!--Device-USBDriverInfo-vendorIdList: Array<int>--><!--Device-USBDriverInfo-vendorIdList: Array<int>-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.
