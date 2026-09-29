# Image

```TypeScript
class Image extends File
```

Represents the image data. It is a child class of [File](arkts-arkdata-unifieddatachannel-file-c.md) and is used to describe images.

**Inheritance/Implementation:** Image extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class Image extends File--><!--Device-unifiedDataChannel-class Image extends File-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Image-get imageUri(): string--><!--Device-Image-get imageUri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set imageUri(value: string)
```

Indicates the uri of image

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Image-set imageUri(value: string)--><!--Device-Image-set imageUri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
