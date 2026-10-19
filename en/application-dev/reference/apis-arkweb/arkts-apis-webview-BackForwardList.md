# Interface (BackForwardList)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=c3549f5fc26f86afdb3e7a215c50ff6d6d5cab0c translatedAt=2026-08-07T04:43:27.492Z pushedAt=2026-08-07T07:49:01.579Z -->

BackForwardList is an interface in the ArkWeb framework for accessing the browsing history list of a Web component. It is obtained through the [getBackForwardEntries](./arkts-apis-webview-WebviewController.md#getbackforwardentries) method. This interface provides read-only access to the page navigation history. Developers can obtain basic information about the current history list (the current index and the total number of history entries), as well as detailed information about a specific history item by index.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this interface are supported since API version 9.
>
> - The sample effect is subject to the actual device.

## Module to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## Attributes

**System capability**: SystemCapability.Web.Webview.Core

| Name        | Type  | Read-Only| Optional| Description                                                        |
| ------------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| currentIndex | number | No  | No  | Index of the current page in the backforward list.                                |
| size | number | No | No | Number of history records in the history list. A maximum of 50 records are saved. When the limit is exceeded, the earliest record is overwritten. |

## getItemAtIndex

getItemAtIndex(index: number): HistoryItem

Obtains the information of the history item at the specified index in the history list. A BackForwardList instance must be obtained first through the [getBackForwardEntries](./arkts-apis-webview-WebviewController.md#getbackforwardentries) method.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| index  | number | Yes  | Index of the history item in the backforward list.|

**Returns**

| Type                       | Description        |
| --------------------------- | ------------ |
| [HistoryItem](./arkts-apis-webview-i.md#historyitem) | History item.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  @State icon: image.PixelMap | undefined = undefined;

  build() {
    Column() {
      Button('getBackForwardEntries')
        .onClick(() => {
          try {
            let list = this.controller.getBackForwardEntries();
            let historyItem = list.getItemAtIndex(list.currentIndex);
            console.info("HistoryItem: " + JSON.stringify(historyItem));
            this.icon = historyItem.icon;
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```