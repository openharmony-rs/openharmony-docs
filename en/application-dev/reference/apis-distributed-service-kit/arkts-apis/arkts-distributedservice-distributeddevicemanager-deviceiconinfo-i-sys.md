# DeviceIconInfo (System API)

```TypeScript
interface DeviceIconInfo
```

Defines the device icon information.

**Since:** 18

<!--Device-distributedDeviceManager-interface DeviceIconInfo--><!--Device-distributedDeviceManager-interface DeviceIconInfo-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## icon

```TypeScript
icon: ArrayBuffer
```

Icon.

**Type:** ArrayBuffer

**Since:** 18

<!--Device-DeviceIconInfo-icon: ArrayBuffer--><!--Device-DeviceIconInfo-icon: ArrayBuffer-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## imageType

```TypeScript
imageType: string
```

Image type. This parameter has a fixed value of **ID**, indicating the product's physical image.

**Type:** string

**Since:** 18

<!--Device-DeviceIconInfo-imageType: string--><!--Device-DeviceIconInfo-imageType: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## internalModel

```TypeScript
internalModel?: string
```

Internal product model. This parameter is left unspecified by default.

**Type:** string

**Since:** 18

<!--Device-DeviceIconInfo-internalModel?: string--><!--Device-DeviceIconInfo-internalModel?: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## productId

```TypeScript
productId: string
```

Product ID.

**Type:** string

**Since:** 18

<!--Device-DeviceIconInfo-productId: string--><!--Device-DeviceIconInfo-productId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## specName

```TypeScript
specName: string
```

Image specification name. Value:  
- **lg**: large image (size: 1008×1008 pixels)  
- **sm**: small image (size: 256×256 pixels).

**Type:** string

**Since:** 18

<!--Device-DeviceIconInfo-specName: string--><!--Device-DeviceIconInfo-specName: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## subProductId

```TypeScript
subProductId?: string
```

Sub-product ID. This parameter is left unspecified by default.

**Type:** string

**Since:** 18

<!--Device-DeviceIconInfo-subProductId?: string--><!--Device-DeviceIconInfo-subProductId?: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## url

```TypeScript
url: string
```

URL.

**Type:** string

**Since:** 18

<!--Device-DeviceIconInfo-url: string--><!--Device-DeviceIconInfo-url: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
