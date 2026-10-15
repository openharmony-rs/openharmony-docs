# GestureInfo

```TypeScript
declare interface GestureInfo
```

Defines the gesture information type.

**Since:** 11

<!--Device-unnamed-declare interface GestureInfo--><!--Device-unnamed-declare interface GestureInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isSystemGesture

```TypeScript
isSystemGesture: boolean
```

Whether the current gesture is a system built-in gesture. The value **true** indicates that the gesture is a system built-in gesture, and **false** indicates the opposite.

Default value: **false**

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureInfo-isSystemGesture: boolean--><!--Device-GestureInfo-isSystemGesture: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tag

```TypeScript
tag?: string
```

Gesture tag.

**NOTE:** 

Returns **undefined** if the gesture's **tag** attribute was not set.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureInfo-tag?: string--><!--Device-GestureInfo-tag?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: GestureControl.GestureType
```

Gesture type.

**NOTE:** 

Returns **-1** for built-in gestures of unexposed types.

**Type:** [GestureControl.GestureType](arkts-arkui-tapgesture-comp-gesturetype-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureInfo-type: GestureControl.GestureType--><!--Device-GestureInfo-type: GestureControl.GestureType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
