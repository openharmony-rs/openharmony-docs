# DepthMapCallback (System API)

```TypeScript
declare type DepthMapCallback = (error: BusinessError<void>) => void
```

type DepthMapCallback = (error: BusinessError&lt;void&gt;) =&gt; void

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-declare type DepthMapCallback = (error: BusinessError<void>) => void--><!--Device-unnamed-declare type DepthMapCallback = (error: BusinessError<void>) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| error | [BusinessError](arkts-arkui-image-comp-businesserror-t.md)&lt;void&gt; | Yes | Error information returned when the depth map resource finishes loading. On load success, **error.code** is **0**; on load failure, **error** contains the error code and error message. |
