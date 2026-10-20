# DeviceProfileInfoFilterOptions (System API)

```TypeScript
interface DeviceProfileInfoFilterOptions
```

Defines device profile information filter options.

**Since:** 15

<!--Device-distributedDeviceManager-interface DeviceProfileInfoFilterOptions--><!--Device-distributedDeviceManager-interface DeviceProfileInfoFilterOptions-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## deviceIdList

```TypeScript
deviceIdList?: Array<string>
```

Device ID. The device ID is usually the UDID of the device. If the device does not have a UDID, the MAC address or SN of the device is used as the device ID. This parameter is left unspecified by default.

**Type:** Array&lt;string&gt;

**Since:** 15

<!--Device-DeviceProfileInfoFilterOptions-deviceIdList?: Array<string>--><!--Device-DeviceProfileInfoFilterOptions-deviceIdList?: Array<string>-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## isCloud

```TypeScript
isCloud : boolean
```

Whether to obtain the device list from the cloud in real time.

- **false**: Obtain the device list from the device.  
- **true**: Obtain the device list from the cloud.

**Type:** boolean

**Since:** 15

<!--Device-DeviceProfileInfoFilterOptions-isCloud : boolean--><!--Device-DeviceProfileInfoFilterOptions-isCloud : boolean-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
