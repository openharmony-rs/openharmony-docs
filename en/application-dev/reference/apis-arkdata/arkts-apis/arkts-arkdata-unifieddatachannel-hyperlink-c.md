# Hyperlink

```TypeScript
class Hyperlink extends Text
```

A subclass of [Text](arkts-arkdata-unifieddatachannel-text-c.md) that describes hyperlink data.

**Inheritance/Implementation:** Hyperlink extends [Text](arkts-arkdata-unifieddatachannel-text-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class Hyperlink extends Text--><!--Device-unifiedDataChannel-class Hyperlink extends Text-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## description

```TypeScript
description?: string
```

Description of the link content. This is an optional field, and the default value is an empty string.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Hyperlink-description?: string--><!--Device-Hyperlink-description?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## url

```TypeScript
get url(): string
```

URL of the link.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Hyperlink-get url(): string--><!--Device-Hyperlink-get url(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set url(value: string)
```

URL of the link.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Hyperlink-set url(value: string)--><!--Device-Hyperlink-set url(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
