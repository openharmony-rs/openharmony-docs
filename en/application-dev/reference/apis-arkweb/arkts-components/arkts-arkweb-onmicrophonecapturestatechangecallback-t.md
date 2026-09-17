# OnMicrophoneCaptureStateChangeCallback

```TypeScript
type OnMicrophoneCaptureStateChangeCallback = (event: MicrophoneCaptureStateChangeInfo) => void
```

Defines a callback triggered when the microphone state of the page changes.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [MicrophoneCaptureStateChangeInfo](arkts-arkweb-microphonecapturestatechangeinfo-i.md) | Yes | Original and new microphone state. |
