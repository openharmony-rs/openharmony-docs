# CommonProgressStyleOptions

Provides common style configuration options for the progress indicator.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableSmoothEffect

```TypeScript
enableSmoothEffect?: boolean
```

Whether to enable the smooth effect. When this feature is enabled, the progress value transitions from the current value to the target value with a progress change animation displayed on the page. When this feature is disabled, the progress value jumps directly to the target value without any animation.

**true**: The smooth effect is enabled.

**false**: The smooth effect is disabled.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
