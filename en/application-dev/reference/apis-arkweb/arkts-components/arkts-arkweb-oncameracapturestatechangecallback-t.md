# OnCameraCaptureStateChangeCallback

```TypeScript
type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void
```

This callback is triggered when the camera device state of the page changes.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [CameraCaptureStateChangeInfo](arkts-arkweb-cameracapturestatechangeinfo-i.md) | Yes | Original and new camera state. |
