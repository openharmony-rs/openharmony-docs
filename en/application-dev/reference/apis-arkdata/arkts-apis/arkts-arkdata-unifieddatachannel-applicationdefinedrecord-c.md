# ApplicationDefinedRecord

```TypeScript
class ApplicationDefinedRecord extends UnifiedRecord
```

ApplicationDefinedRecord is a subclass of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and the base class of application-defined data types. It describes custom data types that circulate only within the application ecosystem. Applications can extend custom data types based on this class.

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

Identifier of the application-defined type. It must start with 'ApplicationDefined'.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationDefinedRecord-get applicationDefinedType(): string--><!--Device-ApplicationDefinedRecord-get applicationDefinedType(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set applicationDefinedType(value: string)
```

Identifier of the application-defined type. It must start with 'ApplicationDefined'.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationDefinedRecord-set applicationDefinedType(value: string)--><!--Device-ApplicationDefinedRecord-set applicationDefinedType(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## rawData

```TypeScript
get rawData(): Uint8Array
```

Binary data of the application-defined data type.

**Type:** Uint8Array

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationDefinedRecord-get rawData(): Uint8Array--><!--Device-ApplicationDefinedRecord-get rawData(): Uint8Array-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set rawData(value: Uint8Array)
```

Binary data of the application-defined data type.

**Type:** Uint8Array

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationDefinedRecord-set rawData(value: Uint8Array)--><!--Device-ApplicationDefinedRecord-set rawData(value: Uint8Array)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
