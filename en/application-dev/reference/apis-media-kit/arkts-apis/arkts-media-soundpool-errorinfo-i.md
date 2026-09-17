# ErrorInfo

Describes the error information.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## errorCode

```TypeScript
errorCode: T
```

Error code. The type of **errorCode** is [BusinessError](../../../reference/apis-basic-services-kit/js-apis-base.md).

**Type:** T

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## errorType

```TypeScript
errorType?: ErrorType
```

Stage at which the error occurred.

**Type:** [ErrorType](arkts-media-soundpool-errortype-e.md)

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## soundId

```TypeScript
soundId?: number
```

ID of the resource where the error occurred. It can be obtained by calling **load**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## streamId

```TypeScript
streamId?: number
```

ID of the audio stream where the error occurred. It can be obtained by calling **play**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.SoundPool
