# ApplicationDefinedRecord

```TypeScript
class ApplicationDefinedRecord extends UnifiedRecord
```

Represents the custom data type for applications only. It is a child class of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and a base class of custom data types of applications. Applications can extend custom data types based on this class.

**Inheritance/Implementation:** ApplicationDefinedRecord extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class ApplicationDefinedRecord extends UnifiedRecord--><!--Device-unifiedDataChannel-class ApplicationDefinedRecord extends UnifiedRecord-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## applicationDefinedType

```TypeScript
get applicationDefinedType(): string
```

Indicates the type of data, should always be started with 'ApplicationDefined.', will return error otherwise

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ApplicationDefinedRecord-get applicationDefinedType(): string--><!--Device-ApplicationDefinedRecord-get applicationDefinedType(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set applicationDefinedType(value: string)
```

Indicates the type of data, should always be started with 'ApplicationDefined.', will return error otherwise

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ApplicationDefinedRecord-set applicationDefinedType(value: string)--><!--Device-ApplicationDefinedRecord-set applicationDefinedType(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## rawData

```TypeScript
get rawData(): Uint8Array
```

Indicates the raw data of application defined data

**Type:** Uint8Array

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ApplicationDefinedRecord-get rawData(): Uint8Array--><!--Device-ApplicationDefinedRecord-get rawData(): Uint8Array-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set rawData(value: Uint8Array)
```

Indicates the raw data of application defined data

**Type:** Uint8Array

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ApplicationDefinedRecord-set rawData(value: Uint8Array)--><!--Device-ApplicationDefinedRecord-set rawData(value: Uint8Array)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
