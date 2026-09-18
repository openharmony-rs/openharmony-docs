# CallMetadata

The metadata of the current call.

@interface CallMetadata [since 11 - 11]

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## avatar

```TypeScript
avatar?: image.PixelMap
```

The displayed picture that represents a particular user.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## name

```TypeScript
name?: string
```

The displayed user name of current call.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## phoneNumber

```TypeScript
phoneNumber?: string
```

The phone number of current call.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core
