# LargestContentfulPaint

```TypeScript
declare interface LargestContentfulPaint
```

Provides detailed information about the largest contentful paint on the web page, including the navigation time and various paint times. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## imageBPP

```TypeScript
imageBPP?: number
```

Number of pixels of the maximum image.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## largestImageLoadEndTime

```TypeScript
largestImageLoadEndTime?: number
```

End time of the loading of the maximum image, in milliseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## largestImageLoadStartTime

```TypeScript
largestImageLoadStartTime?: number
```

Start time of the loading of the maximum image, in milliseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## largestImagePaintTime

```TypeScript
largestImagePaintTime?: number
```

Loading time of the maximum image, in milliseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## largestTextPaintTime

```TypeScript
largestTextPaintTime?: number
```

Loading time of the maximum text, in milliseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## navigationStartTime

```TypeScript
navigationStartTime?: number
```

Start time of the navigation, in microseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
