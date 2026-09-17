# OnIntelligentTrackingPreventionCallback

```TypeScript
type OnIntelligentTrackingPreventionCallback = (details: IntelligentTrackingPreventionDetails) => void
```

Defines a callback invoked when the tracker cookie is intercepted.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| details | [IntelligentTrackingPreventionDetails](arkts-arkweb-intelligenttrackingpreventiondetails-i.md) | Yes | Detailed information about intelligent tracking prevention. |
