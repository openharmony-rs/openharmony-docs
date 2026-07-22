# ErrorInfo

错误信息。

**起始版本：** 20

<!--Device-unnamed-export interface ErrorInfo<T extends Error = BusinessError>--><!--Device-unnamed-export interface ErrorInfo<T extends Error = BusinessError>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## errorCode

```TypeScript
errorCode: T
```

错误码。errorCode的类型T为[BusinessError](../../../reference/apis-basic-services-kit/js-apis-base.md)类型。

**类型：** T

**起始版本：** 20

<!--Device-ErrorInfo-errorCode: T--><!--Device-ErrorInfo-errorCode: T-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## errorType

```TypeScript
errorType?: ErrorType
```

表示错误发生阶段。

**类型：** ErrorType

**起始版本：** 20

<!--Device-ErrorInfo-errorType?: ErrorType--><!--Device-ErrorInfo-errorType?: ErrorType-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## soundId

```TypeScript
soundId?: number
```

发生错误的资源ID，load方法能够获取soundId。

**类型：** number

**起始版本：** 20

<!--Device-ErrorInfo-soundId?: int--><!--Device-ErrorInfo-soundId?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## streamId

```TypeScript
streamId?: number
```

发生错误的音频流ID，play方法能够获取streamId。

**类型：** number

**起始版本：** 20

<!--Device-ErrorInfo-streamId?: int--><!--Device-ErrorInfo-streamId?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

