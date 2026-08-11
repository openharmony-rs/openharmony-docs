# Class (WebController)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-07T04:39:30.026Z pushedAt=2026-08-07T08:12:42.383Z -->

WebController is the controller class of the ArkWeb component, used to control various behaviors of the Web component. A WebController object can be bound to only one Web component. After binding, developers can use the controller to perform operations on the Web component, such as page navigation (forward/backward/loading), focus control, zoom adjustment, page refresh and stop, cookie management, and JavaScript injection and execution.

WebController is suitable for scenarios where active control of the embedded Web component is required on the app side, such as implementing browser-like forward and backward navigation, establishing a JavaScript interaction channel between the app side and the web page side, dynamically loading web page content, or managing cookie data.

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 8.
>
> - This component is deprecated since API version 9. You are advised to use [WebviewController](./arkts-apis-webview-WebviewController.md) instead.
>
> - The sample effects are subject to the actual running on a real device.

## Creating an Object

<!--deprecated_code_no_check-->

```ts
let webController: WebController = new WebController()
```

## constructor<sup>(deprecated)</sup>

constructor()

Constructs a **WebController** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [constructor<sup>11+</sup>](./arkts-apis-webview-WebviewController.md#constructor11) instead.

**System capability**: SystemCapability.Web.Webview.Core

## getCookieManager<sup>(deprecated)</sup>

getCookieManager(): WebCookie

Obtains the cookie management object of the **Web** component.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 9. You are advised to use [getCookie](./arkts-apis-webview-WebCookieManager.md#getcookiedeprecated) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type       | Description                                      |
| --------- | ---------------------------------------- |
| WebCookie | Cookie management object of the **Web** component. For details, see [WebCookie](./arkts-basic-components-web-WebCookie.md).|

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('getCookieManager')
          .onClick(() => {
            let cookieManager = this.controller.getCookieManager()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## requestFocus<sup>(deprecated)</sup>

requestFocus()

Makes the current web page obtain focus.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [requestFocus<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#requestfocus) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('requestFocus')
          .onClick(() => {
            this.controller.requestFocus()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## accessBackward<sup>(deprecated)</sup>

accessBackward(): boolean

Checks whether going to the previous page can be performed on the current page.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [accessBackward<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#accessbackward) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description                   |
| ------- | --------------------- |
| boolean | **true** is returned if going to the previous page can be performed on the current page; otherwise, **false** is returned.|

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('accessBackward')
          .onClick(() => {
            let result = this.controller.accessBackward()
            console.info('result:' + result)
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## accessForward<sup>(deprecated)</sup>

accessForward(): boolean

Checks whether going to the next page can be performed on the current page.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [accessForward<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#accessforward) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type     | Description                   |
| ------- | --------------------- |
| boolean | If going to the next page can be performed on the current page, **true** is returned; otherwise, **false** is returned.|

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('accessForward')
          .onClick(() => {
            let result = this.controller.accessForward()
            console.info('result:' + result)
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## accessStep<sup>(deprecated)</sup>

accessStep(step: number): boolean

Checks whether the current page can move forward or backward by the given step.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [accessStep<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#accessstep) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory | Description                 |
| ---- | ------ | ---- | --------------------- |
| step | number | Yes  | Number of the steps to take. A positive number means to go forward, and a negative number means to go backward.|

**Return value**

| Type     | Description       |
| ------- | --------- |
| boolean | Whether the page can go forward or backward by the given step. The value **true** means it can, and **false** means it cannot. |

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()
    @State steps: number = 2

    build() {
      Column() {
        Button('accessStep')
          .onClick(() => {
            let result = this.controller.accessStep(this.steps)
            console.info('result:' + result)
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## backward<sup>(deprecated)</sup>

backward()

Goes backward by one page in the history stack. You are advised to call [accessBackward<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#accessbackward) to check whether the current page can go backward before calling **backward**.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [backward<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#backward) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('backward')
          .onClick(() => {
            this.controller.backward()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## forward<sup>(deprecated)</sup>

forward()

Goes forward by one page in the history stack. You are advised to call [accessForward<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#accessforward) to check whether the current page can go forward before calling **forward**.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [forward<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#forward) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('forward')
          .onClick(() => {
            this.controller.forward()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## deleteJavaScriptRegister<sup>(deprecated)</sup>

deleteJavaScriptRegister(name: string)

Deletes a specific application JavaScript object that is registered with the window through **registerJavaScriptProxy**. The deletion takes effect immediately, with no need for invoking the [refresh](#refreshdeprecated) API.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [deleteJavaScriptRegister<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#deletejavascriptregister) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory | Description                                    |
| ---- | ------ | ---- | ---------------------------------------- |
| name | string | Yes  | Name of the registered JavaScript object, which can be used to invoke the corresponding object on the application side from the web side.|

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()
    @State name: string = 'Object'

    build() {
      Column() {
        Button('deleteJavaScriptRegister')
          .onClick(() => {
            this.controller.deleteJavaScriptRegister(this.name)
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## getHitTest<sup>(deprecated)</sup>

getHitTest(): HitTestType

Obtains the element type of the area being clicked.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [getHitTest<sup>(deprecated)</sup>](./arkts-apis-webview-WebviewController.md#gethittestdeprecated) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                             | Description         |
| ------------------------------- | ----------- |
| [HitTestType](./arkts-basic-components-web-e.md#hittesttypedeprecated) | Element type of the area being clicked.|

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('getHitTest')
          .onClick(() => {
            let hitType = this.controller.getHitTest()
            console.info("hitType: " + hitType)
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## loadData<sup>(deprecated)</sup>

loadData(options: { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string })

If **baseUrl** is empty, the specified character string will be loaded using the data protocol.

If **baseUrl** is set to a data URL, the encoded data string will be loaded by the Web component using the data protocol.

If **baseUrl** is set to an HTTP or HTTPS URL, the encoded data string will be processed by the Web component as a non-encoded string in a manner similar to **loadUrl**.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [loadData<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#loaddata) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type  | Mandatory  | Description                                    |
| ---------- | ------ | ---- | ---------------------------------------- |
| data       | string | Yes   | String data to load. The processing method is related to the baseUrl protocol: when baseUrl is empty or uses the "data" protocol, the data is decoded and loaded using "Base64" or "URL" encoding; when baseUrl uses the "http/https" protocol, the data is directly loaded as an unencoded plain HTML string.              |
| mimeType   | string | Yes  | Media type (MIME).                             |
| encoding   | string | Yes   | Encoding type. Supported values include "Base64", "URL", or a character set encoding (such as "UTF-8"). When the data parameter is an unencoded HTML string, use a character set encoding; when the data parameter is an encoded string, use "Base64" or "URL".                |
| baseUrl    | string | No   | Specified URL path (using the "http"/"https"/"data" protocol), which is assigned to `window.origin` by the Web component. When empty, the string is loaded using the "data" protocol. The default value is an empty string. |
| historyUrl | string | No   | History record URL. The default value is an empty string. When not empty, it can be managed by the history record to implement forward and backward navigation. When baseUrl is empty, this attribute is invalid. |

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('loadData')
          .onClick(() => {
            this.controller.loadData({
              data: "<html><body bgcolor=\"white\">Source:<pre>source</pre></body></html>",
              mimeType: "text/html",
              encoding: "UTF-8"
            })
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## loadUrl<sup>(deprecated)</sup>

loadUrl(options: { url: string | Resource, headers?: Array\<Header\> })

Loads the specified URL with the given HTTP headers.

The object injected through **loadUrl** is valid only in the current document. It will be invalid on a new page navigated to through **loadUrl**.

The object injected through **registerJavaScriptProxy** is still valid on a new page redirected through **loadUrl**.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [loadUrl<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#loadurl) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                      | Mandatory | Description          |
| -------- | -------------------------- | ---- | -------------- |
| url      | string \| Resource                     | Yes | URL to load.    |
| headers  | Array\<[Header](./arkts-basic-components-web-i.md#header)\> | No    | Additional HTTP request headers for the URL, used to customize request behavior (such as setting authentication information, specifying content types, and adding user agents). Pass this parameter when additional information needs to be carried in the request. If not passed, the default value (empty array) is used, and no additional HTTP request headers are carried. |

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('loadUrl')
          .onClick(() => {
            this.controller.loadUrl({ url: 'www.example.com' })
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## onActive<sup>(deprecated)</sup>

onActive(): void

Called when the **Web** component enters the active state.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [onActive<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#onactive) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('onActive')
          .onClick(() => {
            this.controller.onActive()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## onInactive<sup>(deprecated)</sup>

onInactive(): void

Called when the **Web** component enters the inactive state.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [onInactive<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#oninactive) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('onInactive')
          .onClick(() => {
            this.controller.onInactive()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## zoom<sup>(deprecated)</sup>

zoom(factor: number): void

Sets a zoom factor for the current web page.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [zoom<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#zoom) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                          |
| ------ | ------ | ---- | ------------------------------ |
| factor | number | Mandatory | Zoom factor. The value **1** indicates that the current zoom ratio remains unchanged. A value less than **1** indicates zooming out, and a value greater than **1** indicates zooming in. The value ranges from (0, 100]. |

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()
    @State factor: number = 1

    build() {
      Column() {
        Button('zoom')
          .onClick(() => {
            this.controller.zoom(this.factor)
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## refresh<sup>(deprecated)</sup>

refresh()

Called when the **Web** component refreshes the web page.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [refresh<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#refresh) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('refresh')
          .onClick(() => {
            this.controller.refresh()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## registerJavaScriptProxy<sup>(deprecated)</sup>

registerJavaScriptProxy(options: { object: object, name: string, methodList: Array\<string\> })

Injects a JavaScript object into the window object and calls the methods of the object in the window object. The injected object does not appear in JavaScript until the next (re)load of the page.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [registerJavaScriptProxy<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#registerjavascriptproxy) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type           | Mandatory | Description                                    |
| ---------- | --------------- | ---- | ---------------------------------------- |
| object     | object          | Yes    | JavaScript object on the app side that participates in the registration. It can declare methods and attributes. However, direct calling from H5 is not supported. The parameters and return types of the methods can only be string, number, or boolean. |
| name       | string          | Yes   | Name of the object to be registered, which is the same as that invoked in the window. After registration, the window can use this name to access the JavaScript object at the application side.|
| methodList | Array\<string\> | Yes   | Methods of the JavaScript object to be registered at the application side.                |

**Example**

  ```ts
  // xxx.ets
  class TestObj {
    constructor() {
    }

    test(): string {
      return "ArkUI Web Component"
    }

    toString(): void {
      console.info('Web Component toString')
    }
  }

  @Entry
  @Component
  struct Index {
    controller: WebController = new WebController()
    testObj = new TestObj();
    build() {
      Column() {
        Row() {
          Button('Register JavaScript To Window').onClick(() => {
            this.controller.registerJavaScriptProxy({
              object: this.testObj,
              name: "objName",
              methodList: ["test", "toString"],
            })
          })
        }
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .javaScriptAccess(true)
      }
    }
  }
  ```

Loaded HTML file.

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
      <head>
          <meta charset="utf-8">
      </head>
      <body>
          Hello world!
          <script type="text/javascript">
              function htmlTest() {
                  str = objName.test("test function")
                  console.info('objName.test result:'+ str)
              }
          </script>
      </body>
  </html>

  ```

## runJavaScript<sup>(deprecated)</sup>

runJavaScript(options: { script: string, callback?: (result: string) => void })

Executes a JavaScript script. This API uses an asynchronous callback to return the script execution result. **runJavaScript** can be invoked only after **loadUrl** is executed. For example, it can be invoked in **onPageEnd**.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [runJavaScript<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#runjavascript) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name     | Type                    | Mandatory| Description                                    |
| -------- | ------------------------ | ---- | ---------------------------------------- |
| script   | string                   | Yes  | JavaScript script.                           |
| callback | (result: string) => void | Optional | Callback invoked to return the result of JavaScript script execution. If the JavaScript script fails to execute or returns no value, **null** is returned. No callback is performed when this parameter is not passed. |

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()
    @State webResult: string = ''
    build() {
      Column() {
        Text(this.webResult).fontSize(20)
        Web({ src: $rawfile('index.html'), controller: this.controller })
        .javaScriptAccess(true)
        .onPageEnd((event) => {
          this.controller.runJavaScript({
            script: 'test()',
            callback: (result: string) => {
              this.webResult = result
              console.info(`The test() return value is: ${result}`)
            }})
          if (event) {
            console.info('url: ', event.url)
          }
        })
      }
    }
  }
  ```

Loaded HTML file.

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        Hello world!
        <script type="text/javascript">
            function test() {
                console.info('Ark WebComponent')
                return "This value is from index.html"
            }
        </script>
    </body>
  </html>
  ```

## stop<sup>(deprecated)</sup>

stop()

Stops page loading.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [stop<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#stop) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('stop')
          .onClick(() => {
            this.controller.stop()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```

## clearHistory<sup>(deprecated)</sup>

clearHistory(): void

Clears the browsing history.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [clearHistory<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#clearhistory) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()

    build() {
      Column() {
        Button('clearHistory')
          .onClick(() => {
            this.controller.clearHistory()
          })
        Web({ src: 'www.example.com', controller: this.controller })
      }
    }
  }
  ```