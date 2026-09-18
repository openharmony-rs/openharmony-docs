# BackForwardList

BackForwardList is an interface in the ArkWeb framework for accessing the browsing history list of a Web component. It is obtained through the [getBackForwardEntries](arkts-arkweb-webview-webviewcontroller-c.md#getbackforwardentries) method. This interface provides read-only access to the page navigation history. Developers can obtain basic information about the current history list (the current index and the total number of history entries), as well as detailed information about a specific history item by index.

@interface BackForwardList [since 9 - 11]

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getItemAtIndex

```TypeScript
getItemAtIndex(index: number): HistoryItem
```

Obtains the information of the history item at the specified index in the history list. A BackForwardList instance must be obtained first through the [getBackForwardEntries](arkts-arkweb-webview-webviewcontroller-c.md#getbackforwardentries) method.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the history item in the backforward list. |

**Return value:**

| Type | Description |
| --- | --- |
| [HistoryItem](arkts-arkweb-webview-historyitem-i.md) | History item. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## currentIndex

```TypeScript
currentIndex: number
```

Index of the current page in the backforward list.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## size

```TypeScript
size: number
```

Number of history records in the history list. A maximum of 50 records are saved. When the limit is exceeded, the earliest record is overwritten.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
