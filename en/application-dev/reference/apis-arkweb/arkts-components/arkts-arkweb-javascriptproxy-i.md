# JavaScriptProxy

Defines the JavaScript object to be injected, including the object name, method list, and permission configuration. It is suitable for scenarios where JavaScript-to-native interaction is required, improving cross-language call flexibility and security.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## asyncMethodList

```TypeScript
asyncMethodList?: Array<string>
```

Asynchronous methods of the JavaScript object to be registered at the application side. Asynchronous methods cannot obtain return values.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## controller

```TypeScript
controller: WebController | WebviewController
```

Controller. Since API version 9, WebController is no longer maintained. You are advised to use WebviewController instead.

**Type:** [WebController](arkts-arkweb-webcontroller-c.md) &#124; [WebviewController](arkts-arkweb-webviewcontroller-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## methodList

```TypeScript
methodList: Array<string>
```

Synchronous methods of the JavaScript object to be registered at the application side.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## name

```TypeScript
name: string
```

Name of the object to be registered, which is the same as that invoked in the window.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## object

```TypeScript
object: object
```

Object participating in the registration. Only methods can be declared, not attributes. Methods must be of the function type.

**Type:** object

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## permission

```TypeScript
permission?: string
```

JSON string, which is empty by default. This string is used to configure JSBridge permission control and define the URL trustlist at the object and method levels.

The **permission** parameter of JavaScriptProxy supports the resource, HTTP, and HTTPS protocols, but does not support the file protocol.

For the example, see [Invoking Application Functions on the Frontend Page](../../../web/web-in-page-app-function-invoking.md).

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
