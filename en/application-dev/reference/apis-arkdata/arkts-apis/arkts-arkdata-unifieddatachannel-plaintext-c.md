# PlainText

```TypeScript
class PlainText extends Text
```

Represents the plain text data. It is a child class of [Text](arkts-arkdata-unifieddatachannel-text-c.md).

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

Indicates the abstract of text

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

Indicates the content of text

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PlainText-get textContent(): string--><!--Device-PlainText-get textContent(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set textContent(value: string)
```

Indicates the content of text

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PlainText-set textContent(value: string)--><!--Device-PlainText-set textContent(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
