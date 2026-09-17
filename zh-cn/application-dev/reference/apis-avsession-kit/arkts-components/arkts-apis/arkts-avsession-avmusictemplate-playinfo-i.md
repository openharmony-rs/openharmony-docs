# PlayInfo

播放信息的定义。

@interface MediaElement

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## currentPlayDuration

```TypeScript
currentPlayDuration: number
```

当前播放的时长，单位为毫秒（ms）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## currentPlayRate

```TypeScript
currentPlayRate: string
```

当前的播放速率。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportNext

```TypeScript
isSupportNext: boolean
```

是否支持下一首。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportPlayMode

```TypeScript
isSupportPlayMode: boolean
```

是否支持切换播放模式。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportPlayRate

```TypeScript
isSupportPlayRate: boolean
```

是否支持改变播放速率。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportPrev

```TypeScript
isSupportPrev: boolean
```

是否支持上一首。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportProgress

```TypeScript
isSupportProgress: boolean
```

是否支持进度。true表示支持，false表示不支持。默认值为true。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportQuickBackward

```TypeScript
isSupportQuickBackward: boolean
```

是否支持快退。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportQuickForward

```TypeScript
isSupportQuickForward: boolean
```

是否支持快进。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportSkipHead

```TypeScript
isSupportSkipHead: boolean
```

是否支持跳过开头。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportSkipTail

```TypeScript
isSupportSkipTail: boolean
```

是否支持跳过结尾。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportSoundEffect

```TypeScript
isSupportSoundEffect: boolean
```

是否支持音效。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSupportSoundQuality

```TypeScript
isSupportSoundQuality: boolean
```

是否支持声音质量。true表示支持，false表示不支持。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## playCounts

```TypeScript
playCounts: string
```

播放量。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## quickBackwardStep

```TypeScript
quickBackwardStep: number
```

快退的步长，单位为毫秒（ms）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## quickForwardStep

```TypeScript
quickForwardStep: number
```

快进的步长，单位为毫秒（ms）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## supportedPlayRate

```TypeScript
supportedPlayRate: string[]
```

支持的播放速率的数组。

**类型：** string[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## totalDuration

```TypeScript
totalDuration: number
```

播放总时长，单位为毫秒（ms）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
