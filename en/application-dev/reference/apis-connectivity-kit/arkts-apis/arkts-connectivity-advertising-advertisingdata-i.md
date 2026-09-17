# AdvertisingData

Represents an advertising data packet.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## includeDeviceName

```TypeScript
includeDeviceName?: boolean
```

Whether the advertising data contains the local device name. **true**: **yes**. **false**: **no**. The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## manufacturerData

```TypeScript
manufacturerData?: ManufacturerData[]
```

Manufacturer data. By default, this field is not carried if it is not set.

**Type:** [ManufacturerData](arkts-connectivity-advertising-manufacturerdata-i.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## serviceData

```TypeScript
serviceData?: ServiceData[]
```

Service data. By default, this field is not carried if it is not set.

**Type:** [ServiceData](arkts-connectivity-advertising-servicedata-i.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## serviceUuids

```TypeScript
serviceUuids?: string[]
```

Service UUIDs. A UUID must contain 36 characters, including 32 hexadecimal digits and four hyphens (-). By default, this field is not used if not set.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base
