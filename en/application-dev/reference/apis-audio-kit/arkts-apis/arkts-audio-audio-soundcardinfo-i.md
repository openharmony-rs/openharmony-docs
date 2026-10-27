# SoundCardInfo

```TypeScript
interface SoundCardInfo
```

Describes sound card information.

**Since:** 26.1.0

<!--Device-audio-interface SoundCardInfo--><!--Device-audio-interface SoundCardInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## busAddress

```TypeScript
busAddress: string
```

Sound card bus address. The maximum length is 256.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundCardInfo-busAddress: string--><!--Device-SoundCardInfo-busAddress: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## cardId

```TypeScript
cardId?: string
```

Sound card ID. The maximum length is 128. Default value: Default sound card ID of the onboard sound card.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundCardInfo-cardId?: string--><!--Device-SoundCardInfo-cardId?: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## cardType

```TypeScript
cardType?: SoundCardType
```

Sound card type. Default value: The default is the onboard sound card type.

**Type:** [SoundCardType](arkts-audio-audio-soundcardtype-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundCardInfo-cardType?: SoundCardType--><!--Device-SoundCardInfo-cardType?: SoundCardType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## driver

```TypeScript
driver: string
```

Sound card driver. The maximum length is 128.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundCardInfo-driver: string--><!--Device-SoundCardInfo-driver: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## model

```TypeScript
model: string
```

Sound card model. The maximum length is 128.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundCardInfo-model: string--><!--Device-SoundCardInfo-model: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## name

```TypeScript
name: string
```

Sound card name. The maximum length is 256.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundCardInfo-name: string--><!--Device-SoundCardInfo-name: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## vendor

```TypeScript
vendor: string
```

Sound card vendor. The maximum length is 128.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundCardInfo-vendor: string--><!--Device-SoundCardInfo-vendor: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core
