# registerWebAdInterface

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## registerWebAdInterface

```TypeScript
function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext): void
```

Injects an ad JavaScript object to the **Web** component (this API is only open to some pre-installed system applications).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [web_webview.WebviewController](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webview.md) | Yes | Web component controller. |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | Yes | Context of the UIAbility. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [21800001](../errorcode-ads.md#21800001-internal-system-error) | System internal error. |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private webViewController: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('registerWebAdInterface')
        .onClick(() => {
          advertising.registerWebAdInterface(this.webViewController, this.context);
        })
      // ...

      Web({ src: 'https://www.example.com', controller: this.webViewController })
    }
    .width('100%')
    .height('100%')
  }
}
```


<a id="registerwebadinterface-1"></a>

## registerWebAdInterface

```TypeScript
function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext, 
    needRefresh: boolean): void
```

Injects an ad JavaScript object to the **Web** component (this API is only open to some pre-installed system applications).

**Since:** 16

**Atomic service API:** This API can be used in atomic services since API version 16.

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [web_webview.WebviewController](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webview.md) | Yes | Web component controller. |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | Yes | Context of the UIAbility. |
| needRefresh | boolean | Yes | Whether to refresh the page (true: yes; false: no). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| [21800001](../errorcode-ads.md#21800001-internal-system-error) | System internal error. |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private webViewController: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      // ...
      Button('registerWebAdInterface')
        .onClick(() => {
          advertising.registerWebAdInterface(this.webViewController, this.context, true);
        })

      Web({ src: 'https://www.example.com', controller: this.webViewController })
    }
    .width('100%')
    .height('100%')
  }
}
```
