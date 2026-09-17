# InterceptionModeCallback

```TypeScript
declare type InterceptionModeCallback = (mode: NavigationMode) => void
```

Implements an interception callback invoked when the display mode of the **Navigation** component switches between single-column and split-column.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [NavigationMode](arkts-arkui-navigationmode-e.md) | Yes | Display mode of the navigation page. |
