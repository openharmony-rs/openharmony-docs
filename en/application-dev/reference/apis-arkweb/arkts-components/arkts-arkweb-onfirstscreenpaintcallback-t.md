# OnFirstScreenPaintCallback

```TypeScript
type OnFirstScreenPaintCallback = (firstScreenPaint: FirstScreenPaint) => void
```

This callback is triggered when the first screen rendering is detected to be complete. Compared with OnFirstMeaningfulPaintCallback, which focuses on the completion of main content loading, and OnLargestContentfulPaintCallback, which focuses on the paint time of the largest content element, this callback focuses more on the rendering completion time of the first screen's visible content, making it suitable for evaluating the user's first visual experience.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| firstScreenPaint | [FirstScreenPaint](arkts-arkweb-firstscreenpaint-i.md) | Yes | Details about the first screen paint. |
