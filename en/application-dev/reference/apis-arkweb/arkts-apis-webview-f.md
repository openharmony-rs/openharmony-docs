# Functions
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @runlei-->
<!--Designer: @shulssins-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=a40d54eb841d3251f24cd251233d70758a16c2e7 translatedAt=2026-11-06T11:01:51.407Z pushedAt=2026-11-09T11:16:33.618Z nl=1 -->

The ArkWeb Functions module is a collection of function capabilities of ArkWeb (Web subsystem). It provides independent functions required during the running of the Web component, such as subscribing to the Web engine initialization completion event. When using the Web component, developers can use the functions in this module to listen for key lifecycle events of the Web engine or perform global Web operations.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual device.

## Module to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## webview.once

once(type: string, callback: Callback\<void\>): void

Registers a one-time callback for web events of the specified type. Currently, only **webInited** is supported. This callback is triggered when the Web engine initialization is complete.

When the first **Web** component is loaded in an app, the Web engine is initialized, and the once() callback is not triggered when other **Web** components are subsequently loaded in the same app. When the app destroys the last **Web** component, if the first **Web** component is loaded again, the app re-enters the Web engine initialization process.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type             | Mandatory| Description                 |
| ------- | ---------------- | ---- | -------------------- |
| type     | string          | Yes   | Type of the Web event. Currently, only **"webInited"** (Web engine initialization complete) is supported.      |
| callback | Callback\<void\> | Yes   | Callback invoked when the Web engine initialization is complete. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                 |
| -------- | ----------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.   |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

webview.once('webInited', () => {
  console.info('configCookieSync');
  webview.WebCookieManager.configCookieSync('https://www.example.com', 'a=b');
});

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```