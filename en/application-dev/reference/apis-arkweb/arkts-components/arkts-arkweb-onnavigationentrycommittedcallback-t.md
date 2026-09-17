# OnNavigationEntryCommittedCallback

```TypeScript
type OnNavigationEntryCommittedCallback = (loadCommittedDetails: LoadCommittedDetails) => void
```

Defines a callback invoked when a navigation entry is submitted.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| loadCommittedDetails | [LoadCommittedDetails](arkts-arkweb-loadcommitteddetails-i.md) | Yes | Detailed information about the web page that has been submitted for redirection. |
