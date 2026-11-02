# Image

```TypeScript
class Image extends File
```

Represents image data. It is a subclass of [File](arkts-arkdata-unifieddatachannel-file-c.md) and is used to describe an image file.

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

URI of the local image data or network image. The URI of the local image data can be obtained by calling [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Image-get imageUri(): string--><!--Device-Image-get imageUri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set imageUri(value: string)
```

URI of the local image data or network image. The URI of the local image data can be obtained by calling [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Image-set imageUri(value: string)--><!--Device-Image-set imageUri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
