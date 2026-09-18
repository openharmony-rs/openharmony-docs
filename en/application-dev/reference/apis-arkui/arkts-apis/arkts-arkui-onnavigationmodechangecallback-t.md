# OnNavigationModeChangeCallback

```TypeScript
declare type OnNavigationModeChangeCallback = (mode: NavigationMode) => void
```

Represents the callback invoked when the mode of the **MultiNavigation** component changes.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [NavigationMode](../arkts-components/arkts-arkui-navigationmode-e.md) | Yes | Navigation mode when the callback is invoked. |
