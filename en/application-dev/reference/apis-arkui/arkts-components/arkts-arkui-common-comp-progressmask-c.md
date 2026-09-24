# ProgressMask

```TypeScript
declare class ProgressMask
```

Sets the progress, maximum value, and color for a mask.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: number, total: number, color: ResourceColor)
```

Constructs a **ProgressMask** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Current value of the progress mask.<br> Value range: [0.0, +∞) |
| total | number | Yes | Maximum value of the progress mask.<br> Value range: [0.0, +∞) |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the progress mask. |

## enableBreathingAnimation

```TypeScript
enableBreathingAnimation(value: boolean): void
```

Sets whether to enable the breathing animation when the progress indicator is full. If this API is not set, the breathing animation is disabled by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable the breathing animation.<br>**true**: The breathing animation is enabled.<br>**false**: The breathing halo animation is disabled. |

## updateColor

```TypeScript
updateColor(value: ResourceColor): void
```

Updates the color of the progress mask.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Current value of the progress mask. |
