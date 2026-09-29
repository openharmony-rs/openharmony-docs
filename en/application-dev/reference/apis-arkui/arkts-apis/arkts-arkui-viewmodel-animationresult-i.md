# AnimationResult

```TypeScript
export interface AnimationResult
```

AnimationResult

@interface AnimationResult

**Since:** 4

<!--Device-unnamed-export interface AnimationResult--><!--Device-unnamed-export interface AnimationResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel(): void
```

Cancels the animation.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-cancel(): void--><!--Device-AnimationResult-cancel(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## finish

```TypeScript
finish(): void
```

Ends the animation.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-finish(): void--><!--Device-AnimationResult-finish(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## oncancel

```TypeScript
oncancel: () => void
```

The animation is canceled.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-oncancel: () => void--><!--Device-AnimationResult-oncancel: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onfinish

```TypeScript
onfinish: () => void
```

The animation is finished.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-onfinish: () => void--><!--Device-AnimationResult-onfinish: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onrepeat

```TypeScript
onrepeat: () => void
```

The animation is repeated.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-onrepeat: () => void--><!--Device-AnimationResult-onrepeat: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onstart

```TypeScript
onstart: () => void
```

The animation is started.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-onstart: () => void--><!--Device-AnimationResult-onstart: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause(): void
```

Pauses the animation.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-pause(): void--><!--Device-AnimationResult-pause(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## play

```TypeScript
play(): void
```

Starts the animation.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-play(): void--><!--Device-AnimationResult-play(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reverse

```TypeScript
reverse(): void
```

Plays the animation in reverse direction.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-reverse(): void--><!--Device-AnimationResult-reverse(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## finished

```TypeScript
finished: boolean
```

Read-only attribute, which indicates whether the animation playback is complete.

**Type:** boolean

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-finished: boolean--><!--Device-AnimationResult-finished: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pending

```TypeScript
pending: boolean
```

Read-only attribute, which indicates whether an animation is waiting for the completion of other asynchronous operations (for example, start an animation with a delay).

**Type:** boolean

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-pending: boolean--><!--Device-AnimationResult-pending: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## playstate

```TypeScript
playstate: string
```

Animation running state: idle: The animation is not running (playback ended or not started). running: The animation is running. paused: The animation is paused. finished: Animation playback ends.

**Type:** string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-playstate: string--><!--Device-AnimationResult-playstate: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startTime

```TypeScript
startTime: number
```

Animation start time. This attribute is similar to that of delay in the options parameters.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-AnimationResult-startTime: number--><!--Device-AnimationResult-startTime: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
