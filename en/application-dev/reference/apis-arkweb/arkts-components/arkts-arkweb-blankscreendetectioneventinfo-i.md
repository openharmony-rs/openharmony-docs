# BlankScreenDetectionEventInfo

Provides the event information when a blank screen is detected, including the URL, reason, and details. It is suitable for scenarios where monitoring page blank screen issues is required, improving blank screen diagnosis accuracy and user experience.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## blankScreenDetails

```TypeScript
blankScreenDetails?: BlankScreenDetails
```

Details of the blank screen detection result. When the detection strategy that detects nodes with content is used and the number of detected nodes with content does not exceed the threshold, this parameter contains detailed information such as the number of nodes with content that are hit. If this strategy is not used or the number of nodes exceeds the threshold, this parameter is empty.

**Type:** [BlankScreenDetails](arkts-arkweb-blankscreendetails-i.md)

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## blankScreenReason

```TypeScript
blankScreenReason: DetectedBlankScreenReason
```

Reason for the blank screen issue, which depends on the detection method.

**Type:** [DetectedBlankScreenReason](arkts-arkweb-detectedblankscreenreason-e.md)

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL of the page when a blank screen is detected.

**Type:** string

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core
