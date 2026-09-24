# ImageAnimatorElement

```TypeScript
export interface ImageAnimatorElement
```

Image animator element @interface ImageAnimatorElement

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## getState

```TypeScript
getState(): "Playing" | "Paused" | "Stopped"
```

Obtains the playback state. Available values are as follows: Playing Paused Stopped

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Return value:**

| Type | Description |
| --- | --- |
| "Playing" &#124; "Paused" &#124; "Stopped" |  |

## pause

```TypeScript
pause(): void
```

Pauses the frame animation playback of an image.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## resume

```TypeScript
resume(): void
```

Resumes the frame animation playback of an image.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## start

```TypeScript
start(): void
```

Starts to play the frame animation of an image. If this method is called again, the playback starts from the first frame.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## stop

```TypeScript
stop(): void
```

Stops the frame animation playback of an image.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
