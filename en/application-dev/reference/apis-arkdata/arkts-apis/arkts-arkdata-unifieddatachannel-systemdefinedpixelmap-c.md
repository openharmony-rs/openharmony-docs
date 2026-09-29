# SystemDefinedPixelMap

```TypeScript
class SystemDefinedPixelMap extends SystemDefinedRecord
```

Represents the image data type corresponding to [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) defined by the system. It is a child class of [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md) and holds only binary data of **PixelMap**.

**Inheritance/Implementation:** SystemDefinedPixelMap extends [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class SystemDefinedPixelMap extends SystemDefinedRecord--><!--Device-unifiedDataChannel-class SystemDefinedPixelMap extends SystemDefinedRecord-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## rawData

```TypeScript
get rawData(): Uint8Array
```

Indicates the raw data of pixel map

**Type:** Uint8Array

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SystemDefinedPixelMap-get rawData(): Uint8Array--><!--Device-SystemDefinedPixelMap-get rawData(): Uint8Array-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set rawData(value: Uint8Array)
```

Indicates the raw data of pixel map

**Type:** Uint8Array

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SystemDefinedPixelMap-set rawData(value: Uint8Array)--><!--Device-SystemDefinedPixelMap-set rawData(value: Uint8Array)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
