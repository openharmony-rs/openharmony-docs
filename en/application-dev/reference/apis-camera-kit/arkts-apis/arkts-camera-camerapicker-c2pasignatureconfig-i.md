# C2PASignatureConfig

```TypeScript
interface C2PASignatureConfig
```

Describes the C2PA signature configuration, which includes the author name and author ID for C2PA signature generation.

**Since:** 26.0.1

<!--Device-cameraPicker-interface C2PASignatureConfig--><!--Device-cameraPicker-interface C2PASignatureConfig-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
```

## authorID

```TypeScript
authorID?: string
```

Author ID for the C2PA signature. This field is optional. If not set, the author ID will not be included in the C2PA signature.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-C2PASignatureConfig-authorID?: string--><!--Device-C2PASignatureConfig-authorID?: string-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## authorName

```TypeScript
authorName?: string
```

Author name for the C2PA signature. This field is optional. If not set, the author name will not be included in the C2PA signature.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-C2PASignatureConfig-authorName?: string--><!--Device-C2PASignatureConfig-authorName?: string-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
