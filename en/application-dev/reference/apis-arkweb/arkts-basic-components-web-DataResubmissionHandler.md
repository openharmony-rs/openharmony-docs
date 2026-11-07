# Class (DataResubmissionHandler)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:13:00.678Z pushedAt=2026-11-04T11:22:07.985Z nl=1 -->

DataResubmissionHandler is a handler class in the Web component for processing web page form data resubmission. When a web page needs to resubmit previously sent form data, the Web component provides a DataResubmissionHandler instance to the application through the `onDataResubmitted` event callback, allowing the application to decide whether to resubmit the form data or cancel the navigation.

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This class is supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **DataResubmissionHandler** object.

**System capability**: SystemCapability.Web.Webview.Core

## resend<sup>9+</sup>

resend(): void

Resends the web form data.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
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

## cancel<sup>9+</sup>

cancel(): void

Cancels the resending of web form data.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
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
            event.handler.cancel();
          })
      }
    }
  }
  ```