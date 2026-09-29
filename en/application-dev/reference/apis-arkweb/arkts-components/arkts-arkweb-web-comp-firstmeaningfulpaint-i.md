# FirstMeaningfulPaint

```TypeScript
declare interface FirstMeaningfulPaint
```

Provides detailed information about the first meaningful paint on the web page, including the navigation time and paint time. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience.

**Since:** 12

<!--Device-unnamed-declare interface FirstMeaningfulPaint--><!--Device-unnamed-declare interface FirstMeaningfulPaint-End-->

**System capability:** SystemCapability.Web.Webview.Core

## firstMeaningfulPaintTime

```TypeScript
firstMeaningfulPaintTime?: number
```

Time taken for the first meaningful paint of the page, in milliseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FirstMeaningfulPaint-firstMeaningfulPaintTime?: number--><!--Device-FirstMeaningfulPaint-firstMeaningfulPaintTime?: number-End-->

**System capability:** SystemCapability.Web.Webview.Core

## navigationStartTime

```TypeScript
navigationStartTime?: number
```

Start time of the navigation, in microseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FirstMeaningfulPaint-navigationStartTime?: number--><!--Device-FirstMeaningfulPaint-navigationStartTime?: number-End-->

**System capability:** SystemCapability.Web.Webview.Core
