# PlainText

Represents the plain text data. It is a child class of [Text](arkts-arkdata-unifieddatachannel-text-c.md).

**Inheritance/Implementation:** PlainText extends [Text](arkts-arkdata-unifieddatachannel-text-c.md)

**Since:** 10

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

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## textContent

```TypeScript
get textContent(): string
```

Indicates the content of text

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set textContent(value: string)
```

Indicates the content of text

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
