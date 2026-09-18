# DeviceIconInfoFilterOptions (System API)

Defines the device icon information filter options.

**Since:** 18

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## imageType

```TypeScript
imageType: string
```

Image type. This parameter has a fixed value of **ID**, indicating the product's physical image.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## internalModel

```TypeScript
internalModel?: string
```

Internal product model. This parameter is left unspecified by default.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## productId

```TypeScript
productId: string
```

Product ID.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## specName

```TypeScript
specName: string
```

Image specification name. Value:

- **lg**: large image (size: 1016064 pixels)  
- **sm**: small image (size: 65536 pixels)

**Type:** string

**Since:** 18

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## subProductId

```TypeScript
subProductId?: string
```

Sub-product ID. This parameter is left unspecified by default.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
