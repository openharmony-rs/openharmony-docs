# Image

Represents the image data. It is a child class of [File](arkts-arkdata-unifieddatachannel-file-c.md) and is used to describe images.

**Inheritance/Implementation:** Image extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## imageUri

```TypeScript
get imageUri(): string
```

Indicates the uri of image

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set imageUri(value: string)
```

Indicates the uri of image

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
