# ControlPanelActionEventCallback

```TypeScript
type ControlPanelActionEventCallback = (event: PiPActionEventType, status?: number) => void
```

Describes the action event callback of the PiP controller.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [PiPActionEventType](arkts-arkui-pipwindow-pipactioneventtype-t.md) | Yes | Type of the action event of the PiP controller.<br>The application performs processing based on the action event. For example, if the **'playbackStateChanged'** event is triggered, the application starts or stops the video. |
| status | number | No | Status of a component that can be switched. For example, for a microphone on/off component group, a camera on/off component group, and a mute/unmute component group, the value **1** means that the component is enabled and **0** means that the component is disabled. For other components, the default value **-1** is used. The value should be an integer. |
