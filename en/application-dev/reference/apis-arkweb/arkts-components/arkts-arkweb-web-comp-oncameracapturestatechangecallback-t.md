# OnCameraCaptureStateChangeCallback

```TypeScript
type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void
```

This callback is triggered when the camera device state of the page changes.

**Since:** 23

<!--Device-unnamed-type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void--><!--Device-unnamed-type OnCameraCaptureStateChangeCallback = (event: CameraCaptureStateChangeInfo) => void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [CameraCaptureStateChangeInfo](arkts-arkweb-web-comp-cameracapturestatechangeinfo-i.md) | Yes | Original and new camera state. |
