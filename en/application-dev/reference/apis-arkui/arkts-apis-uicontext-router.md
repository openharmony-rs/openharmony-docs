# Class (Router)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d04563276400e6bf6dde4f753c5b0383bf91013a translatedAt=2026-08-05T03:17:56.292Z pushedAt=2026-08-06T05:56:19.288Z -->

The Router class provides page navigation capabilities, including navigating to a specified page within the app, replacing the current page with another page in the same app, and returning to the previous page or a specified page. It also supports named route navigation, page stack management, parameter passing, and return confirmation dialog boxes. It is suitable for scenarios that require unified management of page navigation flows and handling data transfer between pages. When integrated with UIContext, it enables flexible routing control.

The router class manages page navigation based on the page stack mechanism, which supports a maximum capacity of 32 pages. When pushUrl is called, the target page is pushed onto the top of the stack. When replaceUrl is called, the current page is popped from the stack and destroyed, and the target page is pushed onto the top of the stack. When back is called, the top page of the stack is popped.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 10.
>
> - The APIs of this module can be used only in the stage model.
>
> - For the following APIs, you must first use the [getRouter()](arkts-apis-uicontext-uicontext.md#getrouter) method in UIContext to obtain a Router object, and then call the corresponding method through this object.
>
> - Router provides the following two routing modes:
>
>   - **Standard routing** ([pushUrl](#pushurl)/[replaceUrl](#replaceurl)): Identifies the target oage by a URL path. This mode is suitable for simple page navigation scenarios.
>
>   - **Named routing** ([pushNamedRoute](#pushnamedroute)/[replaceNamedRoute](#replacenamedroute)): Identifies the target page by a name. Before navigation, the target page must be loaded through import. This mode is suitable for cross-package navigation scenarios.
>
>   It is recommended to use name routing in scenarios where page paths may change or unified routing management is required, and use standard routing in other scenarios. Select the method based on whether you need to return to the previous page.

## pushUrl

pushUrl(options: router.RouterOptions): Promise&lt;void&gt;

Navigates to a specified page in the application. This API uses a promise to return the result.

> **NOTE**
>
> pushUrl() adds a new page to the top of the page stack, increasing the page stack depth by 1 (the maximum is 32 pages; error code 100003 is reported if the limit is exceeded). You can subsequently call back() to return to the previous page or call replaceUrl() to replace the current page.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | Yes    | Redirect page description, including fields such as **url** (target page path) and **params** (parameters passed). |

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100002 | Uri error. The URI of the page to redirect is incorrect or does not exist.           |
| 100003 | Page stack error. Too many pages are pushed.  |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Define the internal class for passing parameters.
class InnerParams {
  array: number[];

  constructor(tuple: number[]) {
    this.array = tuple;
  }
}

// Define the route parameter class.
class RouterParams {
  data: InnerParams;

  constructor(tuple: number[]) {
    this.data = new InnerParams(tuple);
  }
}

@Entry
@Component
struct Index {
  async routePage() {
    let options: router.RouterOptions = {
      url: 'pages/second',  // Path of the target page to navigate to.
      params: new RouterParams([12, 45, 78])  // Page parameters to pass.
    }
    this.getUIContext()
      .getRouter()
      .pushUrl(options)
      .then(() => {
        console.info('pushUrl success');
      })
      .catch((err: ESObject) => {
        console.error(`pushUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
      });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text('First Page')
      Button('Next page')
        .type(ButtonType.Capsule)
        .margin({ top: 20 })
        .onClick(() => {
          this.routePage()
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

```ts
// Receive the passed parameters on the second page.
class InnerParams {
  array: number[];

  constructor(tuple: number[]) {
    this.array = tuple;
  }
}

class RouterParams {
  data: InnerParams;

  constructor(tuple: number[]) {
    this.data = new InnerParams(tuple);
  }
}

@Entry
@Component
struct Second {
  @State data: object = (this.getUIContext().getRouter().getParams() as RouterParams).data;
  @State secondData: string = '';

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text('Second Page')
      Button('Back')
        .fontSize(30)
        .onClick(() => {
          try {
            // Enable the back confirmation dialog box.
            this.getUIContext().getRouter().showAlertBeforeBackPage({ message: 'Are you sure to return?' })
          } catch (error) {
            // TODO: Implement error handling.
          }
          this.getUIContext().getRouter().back()
        })
        .margin({ top: 20 })
      Button(`The value on the first page: ${this.secondData}`)
        .margin({ top: 20 })
        .onClick(()=> {
          this.secondData = (this.data['array'][1]).toString();
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## pushUrl

pushUrl(options: router.RouterOptions, callback: AsyncCallback&lt;void&gt;): void

Navigates to a specified page in the application. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description       |
| -------- | ---------------------------------------- | ---- | --------- |
| options  | [router.RouterOptions](js-apis-router.md#routeroptions) | Yes   | Page routing parameters.|
| callback | AsyncCallback&lt;void&gt;                | Yes    | Callback invoked to return the page navigation result.<br/>On successful page navigation, **error** is **undefined**. On failed page navigation, **error** is the error object returned by the system.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100002 | Uri error. The URI of the page to redirect is incorrect or does not exist.           |
| 100003 | Page stack error. Too many pages are pushed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    // Call the pushUrl API to navigate to a page.
    this.getUIContext().getRouter().pushUrl({
      url: 'pages/routerpage2',  // Target page path for navigation.
      params: {  // Page parameters to pass.
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
        }
      }
    }, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`pushUrl failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('pushUrl success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## pushUrl

pushUrl(options: router.RouterOptions, mode: router.RouterMode): Promise&lt;void&gt;

Navigates to a specified page in the application. This API uses a promise to return the result. Compared with [pushUrl](#pushurl), this API supports the **mode** parameter, which enables you to set the routing mode.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description        |
| ------- | ---------------------------------------- | ---- | ---------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | Yes   | Page routing parameters. |
| mode    | [router.RouterMode](js-apis-router.md#routermode9) | Yes    | Mode used for page navigation. The options are **Standard** (standard mode) and **Single** (singleton mode). Select based on page stack management requirements. The standard mode is suitable for regular page navigation, and the single mode can avoid duplicate pages in the stack, making it ideal for singleton scenarios such as the sign-in page and home page. |

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100002 | Uri error. The URI of the page to redirect is incorrect or does not exist.           |
| 100003 | Page stack error. Too many pages are pushed.  |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Define the routing mode class.
class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;  // Standard routing mode.
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushUrl({
        url: 'pages/routerpage2',
        params: {  // Page parameters to pass.
          data1: 'message',
          data2: {
            data3: [123, 456, 789]
          }
        }
      }, rtm.Standard)  // Use the standard routing mode.
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## pushUrl

pushUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void

Navigates to a specified page in the application. This API uses an asynchronous callback to return the result. Compared with [pushUrl](#pushurl-1), this API supports the **mode** parameter, which enables you to set the routing mode.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description        |
| -------- | ---------------------------------------- | ---- | ---------- |
| options  | [router.RouterOptions](js-apis-router.md#routeroptions) | Yes   | Page routing parameters. |
| mode     | [router.RouterMode](js-apis-router.md#routermode9) | Yes    | Mode used for page navigation. The options are Standard (Standard Mode) or Single (Singleton Mode). Select based on page stack management requirements. The standard mode is suitable for regular page navigation, and the single mode can avoid duplicate pages in the stack, suitable for singleton scenarios such as the sign-in pages and home page. |
| callback | AsyncCallback&lt;void&gt;                | Yes    | Callback for the page navigation result.<br/>On successful page navigation, **error** is **undefined**. On failed page navigation, **error** is the error object returned by the system.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100002 | Uri error. The URI of the page to redirect is incorrect or does not exist.           |
| 100003 | Page stack error. Too many pages are pushed.  |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushUrl({
      url: 'pages/routerpage2',
      params: {
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
        }
      }
    }, rtm.Standard, (err) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`pushUrl failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('pushUrl success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## replaceUrl

replaceUrl(options: router.RouterOptions): Promise&lt;void&gt;

Replaces the current page with another one in the application and destroys the current page. This API uses a promise to return the result.

> **NOTE**
>
> replaceUrl() replaces the top page of the page stack, and the page stack depth remains unchanged. The key difference from pushUrl() is that pushUrl() pushes a new page onto the stack and increases the stack depth by 1, whereas replaceUrl() does not change the stack depth. The replaced page is directly destroyed and cannot be accessed again through back(). Applicable scenarios include: navigating to the home page after a successful sign-in (to prevent returning to the login page), page redirection, and temporary transit page navigation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | Yes   | Description of the new page.|

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                                    |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002 | Uri error. The URI of the page to be used for replacement is incorrect or does not exist.                 |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    // Call the replaceUrl API to replace the page.
    this.getUIContext().getRouter().replaceUrl({
        url: 'pages/detail',  // Path of the target page to replace.
        params: {  // Page parameters to pass.
          data1: 'message'
        }
      })
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`replaceUrl failed, code is ${error.code}, message is ${error.message}`);
      });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## replaceUrl

replaceUrl(options: router.RouterOptions, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another one in the application and destroys the current page. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description       |
| -------- | ---------------------------------------- | ---- | --------- |
| options  | [router.RouterOptions](js-apis-router.md#routeroptions) | Yes   | Description of the new page.|
| callback | AsyncCallback&lt;void&gt;                | Yes    | Callback used to return the page replacement result.<br/>If the page replacement is successful, **error** is **undefined**. If the page replacement fails, **error** is the error object returned by the system.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                                    |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002 | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceUrl({
      url: 'pages/detail',
      params: {  // Page parameters to pass.
        data1: 'message'
      }
    }, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`replaceUrl failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('replaceUrl success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## replaceUrl

replaceUrl(options: router.RouterOptions, mode: router.RouterMode): Promise&lt;void&gt;

Replaces the current page with another page in the app and destroys the replaced page. This API uses a promise to return the result. Compared with [replaceUrl](#replaceurl), this API adds the **mode** parameter, which supports setting the mode used for page replacement.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description        |
| ------- | ---------------------------------------- | ---- | ---------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | Yes   | Description of the new page. |
| mode    | [router.RouterMode](js-apis-router.md#routermode9) | Yes    | Mode used for page replacement. The options are Standard (Standard Mode) or Single (Singleton Mode). Select based on page stack management requirements. The standard mode is suitable for regular page navigation, and the singleton mode can avoid duplicate pages in the stack, making it suitable for singleton scenarios such as the sign-in page and home page. |

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                                    |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Failed to get the delegate. This error code is thrown only in the standard system. |
| 200002 | Uri error. The URI of the page to be used for replacement is incorrect or does not exist.                 |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceUrl({
        url: 'pages/detail',
        params: {
          data1: 'message'
        }
      }, rtm.Standard)
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`replaceUrl failed, code is ${error.code}, message is ${error.message}`);
      });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## replaceUrl

replaceUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another page in the app and destroys the replaced page. This API uses an asynchronous callback to return the result. Compared with [replaceUrl](#replaceurl-1), this API adds the **mode** parameter, which supports setting the mode used for page replacement.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description        |
| -------- | ---------------------------------------- | ---- | ---------- |
| options  | [router.RouterOptions](js-apis-router.md#routeroptions) | Yes   | Description of the new page. |
| mode | [router.RouterMode](js-apis-router.md#routermode9) | Yes | Mode used for page replacement. The options are Standard (Standard Mode) or Single (Singleton Mode). Select based on page stack management requirements. The standard mode is suitable for regular page navigation, and the singleton mode can avoid duplicate pages in the stack, making it suitable for singleton scenarios such as the sign-in page and home page. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback for the page replacement result.<br/>If the page replacement is successful, **error** is **undefined**. If the page replacement fails, **error** is the error object returned by the system. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                                    |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002 | Uri error. The URI of the page to be used for replacement is incorrect or does not exist.               |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceUrl({
      url: 'pages/detail',
      params: {
        data1: 'message'
      }
    }, rtm.Standard, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`replaceUrl failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('replaceUrl success');
    });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## pushNamedRoute

pushNamedRoute(options: router.NamedRouterOptions): Promise&lt;void&gt;

Navigates to a page using the named route. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | Yes | Redirect page description, including fields such as **name** (named route name) and **params** (parameters to pass). |

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100003 | Page stack error. Too many pages are pushed.  |
| 100004 | Named route error. The named route does not exist.   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    // Call the pushNamedRoute API to navigate to the named route page.
    this.getUIContext().getRouter().pushNamedRoute({
        name: 'myPage',  // Named route name.
        params: {  // Page parameters to pass.
          data1: 'message',
          data2: {
            data3: [123, 456, 789]
          }
        }
      })
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushNamedRoute failed, code is ${error.code}, message is ${error.message}`);
      });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## pushNamedRoute

pushNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback&lt;void&gt;): void

Navigates to a page using the named route. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description       |
| -------- | ---------------------------------------- | ---- | --------- |
| options  | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | Yes   | Page routing parameters.|
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the page navigation result.<br/>If the page navigation is successful, **error** is **undefined**. If the page navigation fails, **error** is the error object returned by the system. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100003 | Page stack error. Too many pages are pushed.  |
| 100004 | Named route error. The named route does not exist.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushNamedRoute({
      name: 'myPage',
      params: {
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
        }
      }
    }, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`pushNamedRoute failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('pushNamedRoute success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## pushNamedRoute

pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise&lt;void&gt;

Navigates to a page using the named route. This API uses a promise to return the result. Compared with [pushNamedRoute](#pushnamedroute), this API supports the **mode** parameter, which enables you to set the routing mode.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description        |
| ------- | ---------------------------------------- | ---- | ---------- |
| options | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | Yes   | Page routing parameters. |
| mode    | [router.RouterMode](js-apis-router.md#routermode9) | Yes    | Mode used for page navigation. The options are Standard (Standard Mode) and Single (Singleton Mode). Select based on page stack management requirements. The standard mode is suitable for regular page navigation, and the singleton mode can avoid duplicate pages in the stack, making it ideal for singleton scenarios such as the sign-in page and home page. |

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100003 | Page stack error. Too many pages are pushed.  |
| 100004 | Named route error. The named route does not exist.  |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp{
  Standard:router.RouterMode = router.RouterMode.Standard;
}
let rtm:RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushNamedRoute({
      name: 'myPage',
      params: {  // Page parameters passed.
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
          }
        }
      }, rtm.Standard)
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushNamedRoute failed, code is ${error.code}, message is ${error.message}`);
      });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## pushNamedRoute

pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void

Navigates to a page using the named route. This API uses an asynchronous callback to return the result. Compared with [pushNamedRoute](#pushnamedroute-1), this API supports the **mode** parameter, which enables you to set the routing mode.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description        |
| -------- | ---------------------------------------- | ---- | ---------- |
| options  | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | Yes   | Page routing parameters. |
| mode     | [router.RouterMode](js-apis-router.md#routermode9) | Yes    | Mode used for page navigation. The options are Standard (Standard Mode) and Single (Singleton Mode). Select based on page stack management requirements. The standard mode is suitable for regular page navigation, and the singleton mode can avoid duplicate pages being pushed to the stack, making it ideal for singleton scenarios such as the sign-in page and home page. |
| callback | AsyncCallback&lt;void&gt;                | Yes    | Callback invoked to return the page navigation result.<br/>On successful page navigation, **error** is **undefined**. On failed page navigation, **error** is the system-returned error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100003 | Page stack error. Too many pages are pushed.  |
| 100004 | Named route error. The named route does not exist.   |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushNamedRoute({
      name: 'myPage',
      params: {
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
        }
      }
    }, rtm.Standard, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`pushNamedRoute failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('pushNamedRoute success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## replaceNamedRoute

replaceNamedRoute(options: router.NamedRouterOptions): Promise&lt;void&gt;

Replaces the current page with a specified Named Route page and destroys the replaced page. This API uses a promise to return the result. This API is suitable for scenarios such as managing pages with named routes in large applications, avoiding hard-coded URLs when routing paths may change, and enabling each module to manage its own named routes independently in modular development.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | Yes   | Description of the new page.|

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                                    |
| ------ | ---------------------------------------- |
| 401      | if the number of parameters is less than 1 or the type of the url parameter is not string. |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004 | Named route error. The named route does not exist.        |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    // Call the replaceNamedRoute API to replace the Named Route page.
    this.getUIContext().getRouter().replaceNamedRoute({
        name: 'myPage',
        params: {  // Page parameters to pass.
          data1: 'message'
        }
      })
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`replaceNamedRoute failed, code is ${error.code}, message is ${error.message}`);
      });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## replaceNamedRoute

replaceNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another one using the named route and destroys the current page. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description       |
| -------- | ---------------------------------------- | ---- | --------- |
| options  | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | Yes   | Description of the new page.|
| callback | AsyncCallback&lt;void&gt;                | Mandatory    | Callback used to return the page replacement result.<br/>If the page replacement is successful, **error** is **undefined**. If the page replacement fails, **error** is the error object returned by the system.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                                    |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004 | Named route error. The named route does not exist.         |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceNamedRoute({
      name: 'myPage',
      params: {  // Page parameters to pass.
        data1: 'message'
      }
    }, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`replaceNamedRoute failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('replaceNamedRoute success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## replaceNamedRoute

replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise&lt;void&gt;

Replaces the current page with a specified named route page and destroys the replaced page. This API uses a promise to return the result. Compared with [replaceNamedRoute](#replacenamedroute), this API adds the **mode** parameter, which supports setting the mode used for page replacement.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description        |
| ------- | ---------------------------------------- | ---- | ---------- |
| options | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | Yes   | Description of the new page. |
| mode    | [router.RouterMode](js-apis-router.md#routermode9) | Yes    | Mode used for page replacement. The options are Standard and Single. Select based on page stack management requirements. The standard mode is suitable for regular page navigation, and the single mode can avoid duplicate pages in the stack and is suitable for singleton scenarios such as the sign-in page and home page. |

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                                    |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Failed to get the delegate. This error code is thrown only in the standard system. |
| 100004 | Named route error. The named route does not exist.       |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceNamedRoute({
        name: 'myPage',
        params: {
          data1: 'message'
        }
      }, rtm.Standard)
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`replaceNamedRoute failed, code is ${error.code}, message is ${error.message}`);
      });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## replaceNamedRoute

replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with a specified named route page and destroys the replaced page. This API uses an asynchronous callback to return the result. Compared with [replaceNamedRoute](#replacenamedroute-1), this API adds the **mode** parameter, which supports setting the mode used for page replacement.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description        |
| -------- | ---------------------------------------- | ---- | ---------- |
| options  | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | Yes   | Description of the new page. |
| mode | [router.RouterMode](js-apis-router.md#routermode9) | Yes | Mode used for page replacement. The options are Standard (Standard Mode) or Single (Singleton Mode). Select based on page stack management requirements. The standard mode is suitable for regular page navigation, and the singleton mode can avoid duplicate pages from being pushed onto the stack, suitable for singleton scenarios such as sign-in pages and home pages. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback for the page replacement result.<br/>If the page replacement is successful, **error** is **undefined**. When the page replacement fails, **error** is the error object returned by the system. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                                    |
| ------ | ---------------------------------------- |
| 401      | if the number of parameters is less than 1 or the type of the url parameter is not string. |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004 | Named route error. The named route does not exist.        |

**Example**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceNamedRoute({
      name: 'myPage',
      params: {
        data1: 'message'
      }
    }, rtm.Standard, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`replaceNamedRoute failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('replaceNamedRoute success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## back

back(options?: router.RouterOptions ): void

Returns to the previous page or a specified page.

> **NOTE**
>
> If showAlertBeforeBackPage() was previously called to enable the return confirmation dialog box, calling back() will display a confirmation dialog box: if the user selects "Cancel", back() will not be executed; if the user selects "Confirm", back() will proceed. You can disable the return confirmation dialog box by calling hideAlertBeforeBackPage().

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description                                      |
| ------- | ---------------------------------------- | ---- | ---------------------------------------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | No | Description of the page to return to. This parameter is passed when you need to return to a specified page (specify the target page via the **url** field in **options**); it can be omitted when you only need to return to the previous page. The **url** field specifies the target page to return to: if the URL exists in the page stack, the system returns to the page with the same URL that has the largest index; if the URL does not exist, no operation is performed. If **url** is not set, the system returns to the previous page (the page will not be rebuilt and will be reclaimed after being popped from the stack). |

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();
let router: Router = uiContext.getRouter();
router.back({url:'pages/detail'});
```

## back<sup>12+</sup>

back(index: number, params?: Object): void

Returns to the specified page.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| index | number | Yes | Index of the target page to return, starting from 0. Note: This differs from the index parameter of [getStateByIndex](#getstatebyindex12), which starts from 1. <br/> Value range: [0, +∞). If the index is out of the page stack range or no corresponding page exists, the user operation is not responded to. |
| params | Object | No | Parameters carried when returning from the page. No parameters are carried if not passed. The carried parameters can be received through the [getParams](#getparams) method of the target page. |

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
router.back(1);
```

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();
let router: Router = uiContext.getRouter();
router.back(1, {info:'From the home page'}); // Returning with parameters.
```

## clear

clear(): void

Clears all historical pages in the stack and retains only the current page at the top of the stack.

> **NOTE**
>
> Calling clear() clears all historical page stacks, retaining only the current page, and the page stack depth becomes 1. At this point, there is no history in the stack, and the back() method becomes ineffective, but methods such as pushUrl() and replaceUrl() can still be used normally. This operation is irreversible. After execution, the user cannot revisit any historical pages. It is recommended to use this method only in scenarios such as signing out or switching accounts. Before calling this method, be sure to persist critical page state data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
router.clear();    
```

## getLength<sup>(deprecated)</sup>

getLength(): string

Obtains the number of pages in the current stack.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 23. You are advised to use [getStackSize](#getstacksize23) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                |
| ------ | ------------------ |
| string | Number of pages in the stack. The maximum value is **32**.|

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
let size = router.getLength();        
console.info('pages stack size = ' + size);    
```

## getStackSize<sup>23+</sup>

getStackSize(): number

Obtains the number of pages in the current stack.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                |
| ------ | ------------------ |
| number | Number of pages in the stack. The maximum value is **32**.|

**Example**

```ts
@Entry
@Component
struct Index {

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('stack size')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        console.info(`get stack size: ${this.getUIContext().getRouter().getStackSize()}`)
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## getState

getState(): router.RouterState

Obtains state information about the current page.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| router.[RouterState](js-apis-router.md#routerstate) | Page routing state.|

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
let page = router.getState();
if (page != undefined) {
  console.info('current index = ' + page.index);
  console.info('current name = ' + page.name);
  console.info('current path = ' + page.path);
}
```

## getStateByIndex<sup>12+</sup>

getStateByIndex(index: number): router.RouterState | undefined

Obtains the status information about a page by its index.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| index    | number | Yes  | Index of the page to obtain. The index starts from 1. Note: This is different from the index parameter of [back](#back12), which starts from 0. <br/> Value range: [1, +∞). **undefined** is returned when the index does not exist. |

**Return value**

| Type                         | Description     |
| --------------------------- | ------- |
| router.[RouterState](js-apis-router.md#routerstate) \| undefined | State information about the target page. **undefined** if the specified index does not exist.|

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
let options: router.RouterState | undefined = router.getStateByIndex(1);
if (options != undefined) {
  console.info('index = ' + options.index);
  console.info('name = ' + options.name);
  console.info('path = ' + options.path);
  console.info('params = ' + options.params);
}
```

## getStateByUrl<sup>12+</sup>

getStateByUrl(url: string): Array\<router.RouterState>

Obtains the state information of the page that matches the specified URL.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| url    | string | Yes   | URL used to obtain the page information. It must use the in-app page path format. If no page corresponding to the URL exists in the page stack, an empty array is returned.  |

**Return value**

| Type                         | Description     |
| --------------------------- | ------- |
| Array<router.[RouterState](js-apis-router.md#routerstate)> | Page routing state.|

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();
let router: Router = uiContext.getRouter();
let options:Array<router.RouterState> = router.getStateByUrl('pages/index');
for (let i: number = 0; i < options.length; i++) {
  console.info('index = ' + options[i].index);
  console.info('name = ' + options[i].name);
  console.info('path = ' + options[i].path);
  console.info('params = ' + options[i].params);
}
```

## showAlertBeforeBackPage

showAlertBeforeBackPage(options: router.EnableAlertOptions): void

Enables the page return confirmation dialog box. After this method is called, when the user triggers a return operation (such as tapping the back key or calling the back method), the system will first display a confirmation dialog box asking the user whether to return. The return operation is executed only after the user confirms; if the user cancels, the current page is retained. This is suitable for scenarios such as form filling pages (to prevent accidental returns that cause data loss), important operation confirmation pages (such as payment or order submission), and content editing pages (when the user may have unsaved changes). This method is used in pair with hideAlertBeforeBackPage(): after calling this method to enable the dialog box, it is recommended to call hideAlertBeforeBackPage() to disable the dialog box at an appropriate time.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.EnableAlertOptions](js-apis-router.md#enablealertoptions) | Yes | Text dialog box information, including parameters such as **message** (dialog box prompt content). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [API Call Error Codes](errorcode-internal.md).

| ID | Error Message                              |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let uiContext: UIContext = this.getUIContext();
let router: Router = uiContext.getRouter();
try {
  router.showAlertBeforeBackPage({            
    message: 'Message Info'        
  });
} catch(error) {
  let message = (error as BusinessError).message;
  let code = (error as BusinessError).code;
  console.error(`showAlertBeforeBackPage failed, code is ${code}, message is ${message}`);
}
```

## hideAlertBeforeBackPage

hideAlertBeforeBackPage(): void

Disables the page return confirmation dialog box. This is suitable for scenarios such as when the user has completed a save operation and can safely return, when the return confirmation is no longer needed after a page state change, and when dynamic control of the return behavior is required. This method is used in pair with showAlertBeforeBackPage(): after calling showAlertBeforeBackPage() to enable the dialog box, you can call this method to disable the dialog box at an appropriate time.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
router.hideAlertBeforeBackPage();    
```

## getParams

getParams(): Object

Obtains the parameters passed from the initiating page to the current page. The parameters are passed through the **params** field of RouterOptions or NamedRouterOptions during page navigation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description               |
| ------ | ----------------- |
| Object | Parameter object returned by the previous page through the **params** field. You can use this object to obtain the specific data passed during page navigation. |

**Example**

See the example for [PushUrl](#pushurl).

<!--code_no_check-->

```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();
let router: Router = uiContext.getRouter();
router.getParams();
```