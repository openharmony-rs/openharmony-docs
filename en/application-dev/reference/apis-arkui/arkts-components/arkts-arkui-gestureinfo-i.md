# GestureInfo

Defines the gesture information type.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isSystemGesture

```TypeScript
isSystemGesture: boolean
```

Whether the gesture is a system/component gesture. **true** if the gesture is a system/component gesture, **false** otherwise.

Default value: **false**

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: GestureControl.GestureType
```

Gesture type.

**NOTE:** 

Returns **-1** for built-in gestures of unexposed types.

**Type:** [GestureControl.GestureType](arkts-arkui-gesturecontrol-gesturetype-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
