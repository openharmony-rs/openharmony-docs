# getPageContent (System API)

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## getPageContent

```TypeScript
function getPageContent(options?: ContentOptions): Promise<PageContent>
```

Obtains the onscreen content when a window is displayed on the screen.

**Since:** 20

**Required permissions:** ohos.permission.GET_SCREEN_CONTENT

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ContentOptions](arkts-multimodalawareness-onscreen-contentoptions-i-sys.md) | No | Options for obtaining the onscreen screen content. By default, the window ID is not specified, and other options are **False**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md)&gt; | Indicates the promise which carries retrieved page content |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to get page content forbidden by<br> permission: ohos.permission.GET_SCREEN_CONTENT. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission check failed. A non-system application uses the system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-specified-capability-not-supported) | The application or page is not supported. |
| [34000003](../errorcode-onScreen.md#34000003-invalid-window-id) | The window ID is invalid. Possible causes: 1. window id is not passed<br> when screen is splited. 2. passed window id is not on screen or floating. |
| [34000004](../errorcode-onScreen.md#34000004-page-not-ready) | The page is not ready. |
| [34000006](../errorcode-onScreen.md#34000006-request-timeout) | The request timed out. |

**Examples**

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: onScreen.ContentOptions = {
   contentUnderstand: true,
   pageLink: true
};
try {
   onScreen.getPageContent(options).then((pageContent: onScreen.PageContent) => {
      console.info("get page content succeed, bundleName = " + pageContent.bundleName);
   }).catch((err: BusinessError) => {
      console.error("get page content failed, errCode = " + err.code);
   });
} catch (err) {
   console.error('get page content failed, errCode = ' + err.code);
}
```
