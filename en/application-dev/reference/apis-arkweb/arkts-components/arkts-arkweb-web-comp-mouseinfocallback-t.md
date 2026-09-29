# MouseInfoCallback

```TypeScript
type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void
```

This callback is triggered when a same-layer tag is clicked using the mouse or touchpad.

**Since:** 20

<!--Device-unnamed-type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void--><!--Device-unnamed-type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [NativeEmbedMouseInfo](arkts-arkweb-web-comp-nativeembedmouseinfo-i.md) | Yes | Detailed information about the mouse or touchpad click or long press on the same-layer tag. |
