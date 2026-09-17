# ExpectedFrameRateRange

Sets the expected frame rate range for an animation.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## expected

```TypeScript
expected: number
```

Expected optimal frame rate, in fps.

The value range is [**min**, **max**]. When this parameter is set to **0**, the frame rate of the app is used.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max: number
```

Expected maximum frame rate, in fps.

The value range is [**min**, Maximum frame rate of the device].

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min: number
```

Expected minimum frame rate, in fps.

The value range is [0, Maximum frame rate of the device].

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
