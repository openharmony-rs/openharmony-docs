# BlankScreenDetectionMethod

Defines the detection strategy methods used for blank screen detection, which specify the specific algorithms and points for page content detection and help developers strike a balance between detection accuracy and performance overhead, enabling timely identification of page rendering anomalies.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## DETECTION_CONTENTFUL_NODES_SEVENTEEN

```TypeScript
DETECTION_CONTENTFUL_NODES_SEVENTEEN = 0
```

The page is detected using the 17-point detection method. When a rendered and contentful node is detected by a detection point, it is considered that the detection point is hit. A contentful node refers to an image, video, or text node.

If no contentful node is detected or the number of contentful nodes is less than the threshold, a blank or near- blank screen is displayed.

The 17 detection points are as follows:

Center point (1): The center point is at the geometric center of the page.

Internal grid intersection points (16): A 5 × 5 uniform grid is defined in the page area. The 16 points are the intersection points of four vertical equal division lines and four horizontal equal division lines in the page.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core
