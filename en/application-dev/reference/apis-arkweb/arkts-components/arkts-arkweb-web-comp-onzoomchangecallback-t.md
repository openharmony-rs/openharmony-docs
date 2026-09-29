# OnZoomChangeCallback

```TypeScript
type OnZoomChangeCallback = (zoomChangeInfo: OnZoomChangeEvent) => void
```

Called when the browser zoom factor of the page changes.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type OnZoomChangeCallback = (zoomChangeInfo: OnZoomChangeEvent) => void--><!--Device-unnamed-type OnZoomChangeCallback = (zoomChangeInfo: OnZoomChangeEvent) => void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| zoomChangeInfo | [OnZoomChangeEvent](arkts-arkweb-web-comp-onzoomchangeevent-i.md) | Yes | Details about the browser zoom factor change. |
