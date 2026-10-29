# WindowLifeCycleCallback (System API)

```TypeScript
type WindowLifeCycleCallback = (winObj: window.Window) => void
```

Window lifecycle callback function, which is called by system when the window has alredy destroyed.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type WindowLifeCycleCallback = (winObj: window.Window) => void--><!--Device-unnamed-type WindowLifeCycleCallback = (winObj: window.Window) => void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| winObj | [window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md) | Yes | Window object which has already destroyed. |
