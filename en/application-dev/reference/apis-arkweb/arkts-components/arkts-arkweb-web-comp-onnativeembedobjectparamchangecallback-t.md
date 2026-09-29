# OnNativeEmbedObjectParamChangeCallback

```TypeScript
type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void
```

Defines a callback triggered when the **param** element embedded in the same-layer rendered **object** tag is added, modified, or deleted.

**Since:** 21

<!--Device-unnamed-type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void--><!--Device-unnamed-type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [NativeEmbedParamDataInfo](arkts-arkweb-web-comp-nativeembedparamdatainfo-i.md) | Yes | Detailed information about the changes of the **param** element embedded in the **object** tag. |
