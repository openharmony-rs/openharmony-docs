# PreviewMenuOptions

```TypeScript
declare interface PreviewMenuOptions
```

Defines the options of the preview menu.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hapticFeedbackMode

```TypeScript
hapticFeedbackMode? : HapticFeedbackMode
```

Vibration effect when the menu pops up. It takes effect when an ImageSpan or BuilderSpan is bound to a preview menu.

Default value: HapticFeedbackMode.DISABLED, which means no vibration when the menu pops up.

**Note:** It takes effect only when the application has the ohos.permission.VIBRATE permission, the user has enabled haptic feedback, and the system hardware supports it.

**Type:** [HapticFeedbackMode](arkts-arkui-common-comp-hapticfeedbackmode-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
