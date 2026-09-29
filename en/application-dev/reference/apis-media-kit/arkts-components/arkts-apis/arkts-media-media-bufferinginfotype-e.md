# BufferingInfoType

```TypeScript
enum BufferingInfoType
```

Enumerates the buffering event types.

**Since:** 8

<!--Device-media-enum BufferingInfoType--><!--Device-media-enum BufferingInfoType-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## BUFFERING_START

```TypeScript
BUFFERING_START = 1
```

Buffering starts. When this event is triggered, the player pauses the playback.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BufferingInfoType-BUFFERING_START = 1--><!--Device-BufferingInfoType-BUFFERING_START = 1-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## BUFFERING_END

```TypeScript
BUFFERING_END = 2
```

Buffering ends. When this event is triggered, the player resumes the playback.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BufferingInfoType-BUFFERING_END = 2--><!--Device-BufferingInfoType-BUFFERING_END = 2-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## BUFFERING_PERCENT

```TypeScript
BUFFERING_PERCENT = 3
```

Buffering percentage. You can use this event to monitor the buffering status.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BufferingInfoType-BUFFERING_PERCENT = 3--><!--Device-BufferingInfoType-BUFFERING_PERCENT = 3-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## CACHED_DURATION

```TypeScript
CACHED_DURATION = 4
```

Estimated duration, in ms, that the buffered data can be played. This event is triggered once the data change amount in the buffer exceeds 500 ms. You can use this event to develop a progress bar.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BufferingInfoType-CACHED_DURATION = 4--><!--Device-BufferingInfoType-CACHED_DURATION = 4-End-->

**System capability:** SystemCapability.Multimedia.Media.Core
