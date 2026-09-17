# ScanFilters

Defines the scan filters

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address?: string
```

Device address. By default, this field is not used if it is not set. The address format is **11:22:33:AA:BB:FF**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## deviceName

```TypeScript
deviceName?: string
```

Device name. The value contains 0 to 30 characters. By default, this field is not used if it is not set.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## manufacturerData

```TypeScript
manufacturerData?: ArrayBuffer
```

Manufacturer data. By default, this field is not used if it is not set. **manufacturerId** must be set along with the field.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## manufacturerDataMask

```TypeScript
manufacturerDataMask?: ArrayBuffer
```

Manufacturer data mask. By default, this field is not used if it is not set. This field must be set along with **manufacturerData**, and the lengths of the two fields must be the same. A bitwise AND operation is performed on the mask and manufacturer data to accurately match the specified bits in the manufacturer data.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## manufacturerId

```TypeScript
manufacturerId?: number
```

Manufacturer ID. The value range is [1, 65535]. By default, this field is not used if it is not set.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## rssi

```TypeScript
rssi?: number
```

RSSI threshold, in dBm. The value range is this threshold will be filtered out. You are advised to set the threshold within the range of default, the signal strength is not filtered if this parameter is not set. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base
