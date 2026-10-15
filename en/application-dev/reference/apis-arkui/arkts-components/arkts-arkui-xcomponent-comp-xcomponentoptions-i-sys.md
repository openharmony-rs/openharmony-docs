# XComponentOptions

```TypeScript
declare interface XComponentOptions
```

Defines the options of the **XComponent**.

**Since:** 12

<!--Device-unnamed-declare interface XComponentOptions--><!--Device-unnamed-declare interface XComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## screenId

```TypeScript
screenId?: number
```

Sets the ID of the screen associated with the component. With this parameter, the screen content associated with the component can be displayed on the component. The screen ID can be obtained through the getAllScreens API of the [@ohos.screen](../arkts-apis/arkts-arkui-screen.md) module. Default value: **0**, which indicates the primary screen.

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

<!--Device-XComponentOptions-screenId?: number--><!--Device-XComponentOptions-screenId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
