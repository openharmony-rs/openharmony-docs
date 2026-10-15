# setMonitorForCrownEvents

## setMonitorForCrownEvents

```TypeScript
export declare function setMonitorForCrownEvents(handler: Function): void
```

Sets a rotary crown event monitor for the page. When a rotating crown event is triggered, the monitor triggers a callback.

This monitor is automatically removed when page routing occurs. It can be manually removed using the **clearMonitorForCrownEvents** API.

> **NOTE:** 
> 
> - The monitor is automatically removed when page routing occurs. Therefore, it is recommended that this API be called in the **onShow** lifecycle callback of the page.
> - Only one monitor is supported per page. A newly registered monitor overwrites the previous one, and the system uses the monitor passed in the last call to this API.
> - Do not use this function in app.js, as its behavior is undefined.

**Since:** 24

**Model restriction:** This API can be used only in the FA model.

<!--Device-unnamed-export declare function setMonitorForCrownEvents(handler: Function): void--><!--Device-unnamed-export declare function setMonitorForCrownEvents(handler: Function): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | Function | Yes | Callback executed after a rotating crown event occurs. The callback format is **(event)=&gt;{ return false/true; }**.<br>If **true** is returned, the rotating crown event is no longer distributed to the focused component.<br>If **false** is returned, the rotating crown event continues to be distributed to the focused component. If the callback returns an abnormal value, such as **undefined** or no return value, the default value is **false**.<br>The rotating crown event information can be obtained through the input parameter. |
