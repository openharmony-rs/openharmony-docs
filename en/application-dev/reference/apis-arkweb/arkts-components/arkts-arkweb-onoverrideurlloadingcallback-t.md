# OnOverrideUrlLoadingCallback

```TypeScript
type OnOverrideUrlLoadingCallback = (webResourceRequest: WebResourceRequest) => boolean
```

Callback used to intercept URL loading requests. It can block the loading of specific URLs or perform custom processing. Applicable to scenarios such as intercepting ads and blocking redirects to malicious websites.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| webResourceRequest | [WebResourceRequest](arkts-arkweb-webresourcerequest-c.md) | Yes | Information about the URL request. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the loading is blocked. **true** is returned if the loading is blocked; otherwise, **false** is returned. |
