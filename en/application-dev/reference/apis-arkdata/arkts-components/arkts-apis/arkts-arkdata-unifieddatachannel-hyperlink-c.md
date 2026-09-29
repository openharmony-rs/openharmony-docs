# Hyperlink

```TypeScript
class Hyperlink extends Text
```

Represents the hyperlink data. It is a child class of [Text](arkts-arkdata-unifieddatachannel-text-c.md).

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

Indicates the description of a link

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

Indicates the url of a link

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Hyperlink-get url(): string--><!--Device-Hyperlink-get url(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set url(value: string)
```

Indicates the url of a link

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Hyperlink-set url(value: string)--><!--Device-Hyperlink-set url(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
