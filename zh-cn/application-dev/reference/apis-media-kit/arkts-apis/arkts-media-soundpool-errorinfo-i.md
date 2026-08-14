# ErrorInfo

错误信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ErrorInfo--><!--Device-unnamed-export interface ErrorInfo-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## errorCode

```TypeScript
errorCode: T
```

错误码。errorCode的类型T为BusinessError类型。

**类型：** T

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ErrorInfo-errorCode: T--><!--Device-ErrorInfo-errorCode: T-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## errorType

```TypeScript
errorType?: ErrorType
```

表示错误发生阶段。

**类型：** [ErrorType](arkts-media-soundpool-errortype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ErrorInfo-errorType?: ErrorType--><!--Device-ErrorInfo-errorType?: ErrorType-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## soundId

```TypeScript
soundId?: int
```

发生错误的资源ID，load方法能够获取soundId。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ErrorInfo-soundId?: int--><!--Device-ErrorInfo-soundId?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## streamId

```TypeScript
streamId?: int
```

发生错误的音频流ID，play方法能够获取streamId。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ErrorInfo-streamId?: int--><!--Device-ErrorInfo-streamId?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

