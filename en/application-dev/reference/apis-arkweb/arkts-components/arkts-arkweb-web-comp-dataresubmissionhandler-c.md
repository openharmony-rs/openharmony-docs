# DataResubmissionHandler

```TypeScript
declare class DataResubmissionHandler
```

Implements the **DataResubmissionHandler** object for resubmitting or canceling the web form data.

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## cancel

```TypeScript
cancel(): void
```

Cancels the resending of web form data.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Examples**

## constructor

```TypeScript
constructor()
```

Constructs a **DataResubmissionHandler** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## resend

```TypeScript
resend(): void
```

Resends the web form data.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Examples**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Web({ src: 'www.example.com', controller: this.controller })
        .onDataResubmitted((event) => {
          console.info('onDataResubmitted');
          event.handler.resend();
        })
    }
  }
}
```
