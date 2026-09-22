# PreviewMenuOptions

```TypeScript
declare interface PreviewMenuOptions
```

Configures preview menu options, supporting the vibration effect when the menu pops up. It is suitable for scenarios where enhanced menu interaction feedback is required, improving user experience.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## hapticFeedbackMode

```TypeScript
hapticFeedbackMode?: HapticFeedbackMode
```

Vibration effect when the menu is displayed. The **ohos.permission.VIBRATE** permission is required.

Default value: **HapticFeedbackMode.DISABLED**, indicating no vibration when the menu is displayed.

**Type:** [HapticFeedbackMode](../../apis-arkui/arkts-components/arkts-arkui-common-comp-hapticfeedbackmode-e.md)

**Default:** HapticFeedbackMode.DISABLED

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core
