# ScrollSnapOffsetProvider

```TypeScript
declare interface ScrollSnapOffsetProvider
```

Provides offsets for a two-stage scroll snap of a scrollable component.

Offsets are in vp and velocity is in vp/s. Callbacks are invoked synchronously on the UI thread and must be pure calculations. No layout snapshot is provided; a provider must maintain or derive item geometry itself. velocity is the time derivative of the logical content scroll offset, positive toward the content end. The component normalizes reversed layouts and RTL directions. decayOffset is the non-negative magnitude of the natural friction decay distance.

**Since:** 26.2.0

<!--Device-unnamed-declare interface ScrollSnapOffsetProvider--><!--Device-unnamed-declare interface ScrollSnapOffsetProvider-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## calculateApproachOffset

```TypeScript
calculateApproachOffset(velocity: number, decayOffset: number): number
```

Called once during a fling to determine the approach offset.

The return value is a non-negative finite distance magnitude and may be greater than or equal to decayOffset. A non-finite return value, a negative return value, or a callback exception falls back to the natural decay offset.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-ScrollSnapOffsetProvider-calculateApproachOffset(velocity: number, decayOffset: number): number--><!--Device-ScrollSnapOffsetProvider-calculateApproachOffset(velocity: number, decayOffset: number): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| velocity | number | Yes | Current fling velocity, positive toward the content end, in vp/s. |
| decayOffset | number | Yes | Non-negative natural friction decay distance magnitude, in vp. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Approach offset magnitude, in vp. |

## calculateSnapOffset

```TypeScript
calculateSnapOffset(velocity: number): number
```

Called once when the approach motion hands off to the final snap animation.

The return value is an absolute content scroll target; 0 is valid. A finite target outside the legal scroll range is clamped to that range. A non-finite return value or a callback exception uses the component fallback target. A Grid custom strategy stays at the approach endpoint without returning to the gesture start position.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-ScrollSnapOffsetProvider-calculateSnapOffset(velocity: number): number--><!--Device-ScrollSnapOffsetProvider-calculateSnapOffset(velocity: number): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| velocity | number | Yes | Velocity at the start of this approach stage, positive toward the content end, in vp/s. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Absolute target scroll offset, in vp. |
