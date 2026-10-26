# SoundCardInfo

```TypeScript
interface SoundCardInfo
```

描述声卡信息。

**起始版本：** 26.1.0

<!--Device-audio-interface SoundCardInfo--><!--Device-audio-interface SoundCardInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## busAddress

```TypeScript
busAddress: string
```

声卡总线地址。最大长度为256。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundCardInfo-busAddress: string--><!--Device-SoundCardInfo-busAddress: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## cardId

```TypeScript
cardId?: string
```

声卡ID。最大长度为128。默认值：默认使用板载声卡的声卡Id。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundCardInfo-cardId?: string--><!--Device-SoundCardInfo-cardId?: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## cardType

```TypeScript
cardType?: SoundCardType
```

声卡类型。默认值：默认是板载声卡类型。

**类型：** [SoundCardType](arkts-audio-audio-soundcardtype-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundCardInfo-cardType?: SoundCardType--><!--Device-SoundCardInfo-cardType?: SoundCardType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## driver

```TypeScript
driver: string
```

声卡驱动信息。最大长度为128。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundCardInfo-driver: string--><!--Device-SoundCardInfo-driver: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## model

```TypeScript
model: string
```

声卡型号。最大长度为128。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundCardInfo-model: string--><!--Device-SoundCardInfo-model: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## name

```TypeScript
name: string
```

声卡名称。最大长度为256。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundCardInfo-name: string--><!--Device-SoundCardInfo-name: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## vendor

```TypeScript
vendor: string
```

声卡厂商。最大长度为128。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundCardInfo-vendor: string--><!--Device-SoundCardInfo-vendor: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core
