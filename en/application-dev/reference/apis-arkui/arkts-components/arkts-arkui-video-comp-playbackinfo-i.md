# PlaybackInfo

```TypeScript
interface PlaybackInfo
```

Describes the current progress of video playback.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While the initial version information of historical anonymous objects is preserved, there may be cases where the
> outer element's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## time

```TypeScript
time: number
```

Playback progress of the current video.

Unit: s

Value range: [0, +∞)

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
