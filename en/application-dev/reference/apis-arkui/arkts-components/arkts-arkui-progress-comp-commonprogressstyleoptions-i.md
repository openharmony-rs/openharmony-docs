# CommonProgressStyleOptions

```TypeScript
declare interface CommonProgressStyleOptions
```

Provides common style configuration options for the progress indicator.

**Since:** 10

<!--Device-unnamed-declare interface CommonProgressStyleOptions--><!--Device-unnamed-declare interface CommonProgressStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableSmoothEffect

```TypeScript
enableSmoothEffect?: boolean
```

Switch for the progress smooth effect. When the smooth effect is enabled, setting the progress changes it gradually from the current value to the specified value, with an animation on the page. Otherwise, the progress changes abruptly from the current value to the specified value, with no animation on the page.

true: enables the progress smooth effect.

false: disables the progress smooth effect.

Default value: true

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonProgressStyleOptions-enableSmoothEffect?: boolean--><!--Device-CommonProgressStyleOptions-enableSmoothEffect?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
