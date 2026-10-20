# ProgressMask

```TypeScript
declare class ProgressMask
```

Sets the progress, maximum value, and color for a mask.

**Since:** 10

<!--Device-unnamed-declare class ProgressMask--><!--Device-unnamed-declare class ProgressMask-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: number, total: number, color: ResourceColor)
```

Constructs a **ProgressMask** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ProgressMask-constructor(value: number, total: number, color: ResourceColor)--><!--Device-ProgressMask-constructor(value: number, total: number, color: ResourceColor)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Current value of the progress mask. It is used together with total to determine the progress ratio. When value equals total, the progress is full. <br>Value range: [0.0, +∞). If a negative number is passed in, it is automatically corrected to 0. |
| total | number | Yes | Maximum value of the progress mask. <br> Value range: [0.0, +∞). If a negative number is passed in, it is automatically corrected to 100. |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the progress mask. |

## enableBreathingAnimation

```TypeScript
enableBreathingAnimation(value: boolean): void
```

Switch for the breathing glow animation when the progress is full. When enabled, a periodic brightening and dimming glow effect appears at the mask edge when the progress is full. When not set, the breathing glow animation is disabled by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ProgressMask-enableBreathingAnimation(value: boolean): void--><!--Device-ProgressMask-enableBreathingAnimation(value: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable the breathing halo animation when the progress is full. <br>true: enables the breathing halo animation. <br>false: disables the breathing halo animation. |

## updateColor

```TypeScript
updateColor(value: ResourceColor): void
```

Updates the color of the progress mask.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ProgressMask-updateColor(value: ResourceColor): void--><!--Device-ProgressMask-updateColor(value: ResourceColor): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the progress mask. |

## updateProgress

```TypeScript
updateProgress(value: number): void
```

Updates the progress value of the progress mask.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ProgressMask-updateProgress(value: number): void--><!--Device-ProgressMask-updateProgress(value: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Current value of the progress mask. |
