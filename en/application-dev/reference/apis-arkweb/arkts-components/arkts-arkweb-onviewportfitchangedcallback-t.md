# OnViewportFitChangedCallback

```TypeScript
type OnViewportFitChangedCallback = (viewportFit: ViewportFit) => void
```

Defines a callback invoked when the **viewport-fit** configuration in the web page's **\&lt;meta&gt;** tag changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| viewportFit | [ViewportFit](arkts-arkweb-viewportfit-e.md) | Yes | Viewport type for **viewport-fit** in the web page **&lt;meta&gt;** tag. |
