# PlainText

```TypeScript
class PlainText extends Text
```

A subclass of [Text](arkts-arkdata-unifieddatachannel-text-c.md) that describes plain text data.

**Inheritance/Implementation:** PlainText extends [Text](arkts-arkdata-unifieddatachannel-text-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class PlainText extends Text--><!--Device-unifiedDataChannel-class PlainText extends Text-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## abstract

```TypeScript
abstract?: string
```

Plain text abstract. This is an optional field, and the default value is an empty string.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PlainText-abstract?: string--><!--Device-PlainText-abstract?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## textContent

```TypeScript
get textContent(): string
```

Plain text content.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PlainText-get textContent(): string--><!--Device-PlainText-get textContent(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set textContent(value: string)
```

Plain text content.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PlainText-set textContent(value: string)--><!--Device-PlainText-set textContent(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
