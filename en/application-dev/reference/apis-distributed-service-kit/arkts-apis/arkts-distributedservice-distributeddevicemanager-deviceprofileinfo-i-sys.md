# DeviceProfileInfo (System API)

```TypeScript
interface DeviceProfileInfo
```

Defines the device profile information.

**Since:** 15

<!--Device-distributedDeviceManager-interface DeviceProfileInfo--><!--Device-distributedDeviceManager-interface DeviceProfileInfo-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## bleMac

```TypeScript
bleMac: string
```

Bluetooth BLE MAC address.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-bleMac: string--><!--Device-DeviceProfileInfo-bleMac: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## brMac

```TypeScript
brMac: string
```

Bluetooth BR MAC address.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-brMac: string--><!--Device-DeviceProfileInfo-brMac: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: string
```

Device ID.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-deviceId: string--><!--Device-DeviceProfileInfo-deviceId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## deviceName

```TypeScript
deviceName: string
```

Device name.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-deviceName: string--><!--Device-DeviceProfileInfo-deviceName: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## deviceSn

```TypeScript
deviceSn: string
```

Device SN.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-deviceSn: string--><!--Device-DeviceProfileInfo-deviceSn: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## deviceType

```TypeScript
deviceType: string
```

Device type.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-deviceType: string--><!--Device-DeviceProfileInfo-deviceType: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## firmwareVersion

```TypeScript
firmwareVersion: string
```

Firmware version.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-firmwareVersion: string--><!--Device-DeviceProfileInfo-firmwareVersion: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## hardwareVersion

```TypeScript
hardwareVersion: string
```

Hardware version.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-hardwareVersion: string--><!--Device-DeviceProfileInfo-hardwareVersion: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## internalModel

```TypeScript
internalModel?: string
```

Internal product model. This parameter is left unspecified by default.

**Type:** string

**Since:** 18

<!--Device-DeviceProfileInfo-internalModel?: string--><!--Device-DeviceProfileInfo-internalModel?: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## isLocalDevice

```TypeScript
isLocalDevice: boolean
```

Whether the device is a local device.

- **false**: non-local device.  
- **true**: local device.

**Type:** boolean

**Since:** 15

<!--Device-DeviceProfileInfo-isLocalDevice: boolean--><!--Device-DeviceProfileInfo-isLocalDevice: boolean-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## mac

```TypeScript
mac: string
```

MAC address.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-mac: string--><!--Device-DeviceProfileInfo-mac: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## manufacturer

```TypeScript
manufacturer: string
```

Manufacturer.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-manufacturer: string--><!--Device-DeviceProfileInfo-manufacturer: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## model

```TypeScript
model: string
```

Device model.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-model: string--><!--Device-DeviceProfileInfo-model: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## modifyTime

```TypeScript
modifyTime: string
```

Modification time.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-modifyTime: string--><!--Device-DeviceProfileInfo-modifyTime: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## productId

```TypeScript
productId: string
```

Product ID.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-productId: string--><!--Device-DeviceProfileInfo-productId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## productName

```TypeScript
productName?: string
```

Product name. This parameter is left unspecified by default.

**Type:** string

**Since:** 18

<!--Device-DeviceProfileInfo-productName?: string--><!--Device-DeviceProfileInfo-productName?: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## protocolType

```TypeScript
protocolType: number
```

Protocol type.

**Type:** number

**Since:** 15

<!--Device-DeviceProfileInfo-protocolType: int--><!--Device-DeviceProfileInfo-protocolType: int-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## registerTime

```TypeScript
registerTime: string
```

Registration time.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-registerTime: string--><!--Device-DeviceProfileInfo-registerTime: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## sdkVersion

```TypeScript
sdkVersion: string
```

SDK version.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-sdkVersion: string--><!--Device-DeviceProfileInfo-sdkVersion: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## services

```TypeScript
services?: Array<ServiceProfileInfo>
```

Service list. This parameter is left unspecified by default.

**Type:** Array&lt;[ServiceProfileInfo](arkts-distributedservice-distributeddevicemanager-serviceprofileinfo-i-sys.md)&gt;

**Since:** 15

<!--Device-DeviceProfileInfo-services?: Array<ServiceProfileInfo>--><!--Device-DeviceProfileInfo-services?: Array<ServiceProfileInfo>-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## setupType

```TypeScript
setupType: number
```

Setup type. The value should be an integer.

**Type:** number

**Since:** 15

<!--Device-DeviceProfileInfo-setupType: int--><!--Device-DeviceProfileInfo-setupType: int-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## shareTime

```TypeScript
shareTime: string
```

Share time.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-shareTime: string--><!--Device-DeviceProfileInfo-shareTime: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## sleMac

```TypeScript
sleMac: string
```

Starflash MAC address.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-sleMac: string--><!--Device-DeviceProfileInfo-sleMac: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## softwareVersion

```TypeScript
softwareVersion: string
```

Software version.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-softwareVersion: string--><!--Device-DeviceProfileInfo-softwareVersion: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## subProductId

```TypeScript
subProductId?: string
```

Sub-product ID. This parameter is left unspecified by default.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-subProductId?: string--><!--Device-DeviceProfileInfo-subProductId?: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## wiseDeviceId

```TypeScript
wiseDeviceId: string
```

Registered device ID.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-wiseDeviceId: string--><!--Device-DeviceProfileInfo-wiseDeviceId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## wiseUserId

```TypeScript
wiseUserId: string
```

Registered user ID.

**Type:** string

**Since:** 15

<!--Device-DeviceProfileInfo-wiseUserId: string--><!--Device-DeviceProfileInfo-wiseUserId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
