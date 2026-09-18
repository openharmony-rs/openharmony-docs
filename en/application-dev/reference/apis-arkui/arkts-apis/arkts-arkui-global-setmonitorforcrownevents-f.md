# setMonitorForCrownEvents

## setMonitorForCrownEvents

```TypeScript
export declare function setMonitorForCrownEvents(handler: Function): void
```

Sets a digital crown events listener for current page, only be supported on the devices supporting digital crown. Please be awared, the listener will be removed automaticlly if the current page is pushed back or replaced, so it's recommaned to call this function in the onShow lifecycle callback of the page. And only one listener can be set for current page, the system will use the listener passed in through the latest calling of this function. Do not use this function in app.js, the behavior is undefined.

**Since:** 24

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | Function | Yes | Indicates the function to be called when the crown event trigger. |
