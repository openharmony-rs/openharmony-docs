# WebController

WebController is the controller class of the ArkWeb component, used to control various behaviors of the Web component. A WebController object can be bound to only one Web component. After binding, developers can use the controller to perform operations on the Web component, such as page navigation (forward/backward/loading), focus control, zoom adjustment, page refresh and stop, cookie management, and JavaScript injection and execution.

WebController is suitable for scenarios where active control of the embedded Web component is required on the app side, such as implementing browser-like forward and backward navigation, establishing a JavaScript interaction channel between the app side and the web page side, dynamically loading web page content, or managing cookie data.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** WebviewController

**System capability:** SystemCapability.Web.Webview.Core

## accessBackward

```TypeScript
accessBackward(): boolean
```

Checks whether going to the previous page can be performed on the current page.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** accessBackward

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** is returned if going to the previous page can be performed on the current page; otherwise, **false** is returned. |

## accessForward

```TypeScript
accessForward(): boolean
```

Checks whether going to the next page can be performed on the current page.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** accessForward

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | If going to the next page can be performed on the current page, **true** is returned; otherwise, **false** is returned. |

## accessStep

```TypeScript
accessStep(step: number): boolean
```

Checks whether the current page can move forward or backward by the given step.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** accessStep

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| step | number | Yes | Number of the steps to take. A positive number means to go forward, and a negative number means to go backward. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the page can go forward or backward by the given step. The value **true** means it can, and **false** means it cannot. |

## backward

```TypeScript
backward()
```

Goes backward by one page in the history stack. You are advised to call [accessBackward&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#accessbackward) to check whether the current page can go backward before calling **backward**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** backward

**System capability:** SystemCapability.Web.Webview.Core

## clearHistory

```TypeScript
clearHistory(): void
```

Clears the browsing history.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** clearHistory

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **WebController** object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** constructor

**System capability:** SystemCapability.Web.Webview.Core

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string)
```

Deletes a specific application JavaScript object that is registered with the window through **registerJavaScriptProxy**. The deletion takes effect immediately, with no need for invoking the [refresh](#refresh) API.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** deleteJavaScriptRegister

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the registered JavaScript object, which can be used to invoke the corresponding object on the application side from the web side. |

## forward

```TypeScript
forward()
```

Goes forward by one page in the history stack. You are advised to call [accessForward&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#accessforward) to check whether the current page can go forward before calling **forward**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** forward

**System capability:** SystemCapability.Web.Webview.Core

## getCookieManager

```TypeScript
getCookieManager(): WebCookie
```

Obtains the cookie management object of the **Web** component.

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [WebCookieManager](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md)

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WebCookie](arkts-arkweb-webcookie-c.md) | Cookie management object of the **Web** component. For details, see WebCookie. |

## getHitTest

```TypeScript
getHitTest(): HitTestType
```

Obtains the element type of the area being clicked.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getHitTest](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#gethittest)

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [HitTestType](arkts-arkweb-hittesttype-e.md) | Element type of the area being clicked. |

## loadData

```TypeScript
loadData(options: { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string })
```

If **baseUrl** is empty, the specified character string will be loaded using the data protocol.

If **baseUrl** is set to a data URL, the encoded data string will be loaded by the Web component using the data protocol.

If **baseUrl** is set to an HTTP or HTTPS URL, the encoded data string will be processed by the Web component as a non-encoded string in a manner similar to **loadUrl**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** loadData

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string } | Yes | The options with the data or URL and other information. |

## loadUrl

```TypeScript
loadUrl(options: { url: string | Resource, headers?: Array<Header> })
```

Loads the specified URL with the given HTTP headers.

The object injected through **loadUrl** is valid only in the current document. It will be invalid on a new page navigated to through **loadUrl**.

The object injected through **registerJavaScriptProxy** is still valid on a new page redirected through **loadUrl**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** loadUrl

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | { url: string &#124; Resource, headers?: Array&lt;[Header](arkts-arkweb-header-i.md)&gt; } | Yes | The options with the URL and other information. |

## onActive

```TypeScript
onActive(): void
```

Called when the **Web** component enters the active state.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** onActive

**System capability:** SystemCapability.Web.Webview.Core

## onInactive

```TypeScript
onInactive(): void
```

Called when the **Web** component enters the inactive state.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** onInactive

**System capability:** SystemCapability.Web.Webview.Core

## refresh

```TypeScript
refresh()
```

Called when the **Web** component refreshes the web page.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** refresh

**System capability:** SystemCapability.Web.Webview.Core

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })
```

Injects a JavaScript object into the window object and calls the methods of the object in the window object. The injected object does not appear in JavaScript until the next (re)load of the page.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** registerJavaScriptProxy

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | { object: object, name: string, methodList: Array&lt;string&gt; } | Yes | The option with the JavaScript object and method list. |

## requestFocus

```TypeScript
requestFocus()
```

Makes the current web page obtain focus.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** requestFocus

**System capability:** SystemCapability.Web.Webview.Core

## runJavaScript

```TypeScript
runJavaScript(options: { script: string, callback?: (result: string) => void })
```

Executes a JavaScript script. This API uses an asynchronous callback to return the script execution result. **runJavaScript** can be invoked only after **loadUrl** is executed. For example, it can be invoked in **onPageEnd**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** runJavaScript

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | { script: string, callback?: (result: string) =&gt; void } | Yes | The options with a piece of code and a callback. |

## stop

```TypeScript
stop()
```

Stops page loading.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** stop

**System capability:** SystemCapability.Web.Webview.Core

## zoom

```TypeScript
zoom(factor: number): void
```

Sets a zoom factor for the current web page.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [zoom](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#zoom)

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| factor | number | Yes | Zoom factor. The value **1** indicates that the current zoom ratio remains unchanged. A value less than **1** indicates zooming out, and a value greater than **1** indicates zooming in. The value ranges from (0, 100]. |
