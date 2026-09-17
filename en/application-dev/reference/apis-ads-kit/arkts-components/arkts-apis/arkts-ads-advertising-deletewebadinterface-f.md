# deleteWebAdInterface

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## deleteWebAdInterface

```TypeScript
function deleteWebAdInterface(controller: web_webview.WebviewController, needRefresh: boolean): void
```

Deletes the ad JavaScript object injected through **registerWebAdInterface** (this API is only open to some pre-installed system applications).

**Since:** 16

**Atomic service API:** This API can be used in atomic services since API version 16.

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [web_webview.WebviewController](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webview.md) | Yes | Web component controller. |
| needRefresh | boolean | Yes | Whether to refresh the page (true: yes; false: no). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../errorcode-ads.md#401-incorrect-ads-request-parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| [21800001](../errorcode-ads.md#21800001-internal-system-error) | System internal error. |

**Examples**

```TypeScript
import { advertising } from '@kit.AdsKit';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  private webViewController: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('deleteWebAdInterface')
        .onClick(() => {
          advertising.deleteWebAdInterface(this.webViewController, true);
        })

      Web({ src: 'https://www.example.com', controller: this.webViewController })
    }
    .width('100%')
    .height('100%')
  }
}
```
