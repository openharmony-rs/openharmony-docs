# SliderChangeMode

```TypeScript
declare enum SliderChangeMode
```

Enumerates the slider states.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Begin

```TypeScript
Begin
```

The user touches or clicks the thumb.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Moving

```TypeScript
Moving
```

The user is dragging the slider.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## End

```TypeScript
End
```

The user stops dragging the slider by lifting their finger or releasing the mouse device.

**NOTE:** 

The trigger occurs when an invalid value is restored to the default value, that is, when the value is set to less than **min** or greater than **max**.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Click

```TypeScript
Click
```

The user moves the thumb by touching or clicking the track.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
