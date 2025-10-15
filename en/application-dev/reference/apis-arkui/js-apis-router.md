# @ohos.router (Page Routing) (Not Recommended)

The **Router** module provides APIs to access pages through URLs. You can use the APIs to navigate to a specified page in an application, replace the current page with another one in the same application, and return to the previous page or a specified page.

For routing management, it is recommended that you use the [Navigation](../../ui/arkts-navigation-navigation.md) component instead as your application routing framework.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Page routing APIs can be invoked only after page rendering is complete. Do not call these APIs in **onInit** and **onReady** when the page is still in the rendering phase.
>
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is unclear](../../ui/arkts-global-interface.md). For details, see [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - When using [pushUrl](arkts-apis-uicontext-router.md#pushurl-1) or [pushNamedRoute](arkts-apis-uicontext-router.md#pushnamedroute-1) with a callback to return the result, be aware that the stack information obtained through the callback using APIs such as [getLength](arkts-apis-uicontext-router.md#getlength) represents an intermediate state during the navigation operation. This temporary state might differ from the final stack information available after the stack operation is complete.

## Modules to Import

```
import { router } from '@kit.ArkUI';
```

## router.pushUrl<sup>(deprecated)</sup>

pushUrl(options: RouterOptions): Promise&lt;void&gt;

Navigates to a specified page in the application.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [pushUrl](arkts-apis-uicontext-router.md#pushurl) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |
| 100002    | Uri error. The URI of the page to redirect is incorrect or does not exist. |
| 100003    | Page stack error. Too many pages are pushed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new routerParams('message', [123, 456, 789])
})
  .then(() => {
    console.error(`pushUrl finish`);
  })
  .catch((err: ESObject) => {
    console.error(`pushUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })
```

## router.pushUrl<sup>(deprecated)</sup>

pushUrl(options: RouterOptions, callback: AsyncCallback&lt;void&gt;): void

Navigates to a specified page in the application.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [[pushUrl](arkts-apis-uicontext-router.md#pushurl-1) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |
| 100002    | Uri error. The URI of the page to redirect is incorrect or does not exist. |
| 100003    | Page stack error. Too many pages are pushed. |

**Example**

```ts
class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new routerParams('message', [123, 456, 789])
}, (err) => {
  if (err) {
    console.error(`pushUrl failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('pushUrl success');
})
```
## router.pushUrl<sup>(deprecated)</sup>

pushUrl(options: RouterOptions, mode: RouterMode): Promise&lt;void&gt;

Navigates to a specified page in the application.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [pushUrl](arkts-apis-uicontext-router.md#pushurl-2) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |
| 100002    | Uri error. The URI of the page to redirect is incorrect or does not exist. |
| 100003    | Page stack error. Too many pages are pushed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new routerParams('message', [123, 456, 789])
}, router.RouterMode.Standard)
  .then(() => {
    console.error(`pushUrl finish`);
  })
  .catch((err: ESObject) => {
    console.error(`pushUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })
```

## router.pushUrl<sup>(deprecated)</sup>

pushUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void

Navigates to a specified page in the application.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [pushUrl](arkts-apis-uicontext-router.md#pushurl-3) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |
| 100002    | Uri error. The URI of the page to redirect is incorrect or does not exist. |
| 100003    | Page stack error. Too many pages are pushed. |

**Example**

```ts
class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new routerParams('message', [123, 456, 789])
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`pushUrl failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('pushUrl success');
})
```

## router.replaceUrl<sup>(deprecated)</sup>

replaceUrl(options: RouterOptions): Promise&lt;void&gt;

Replaces the current page with another one in the application and destroys the current page. This API cannot be used to configure page transition effects. To configure page transition effects, use the [Navigation](../../ui/arkts-navigation-navigation.md) component.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [replaceUrl](arkts-apis-uicontext-router.md#replaceurl) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [RouterOptions](#routeroptions) | Yes  | Description of the new page.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002    | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class routerParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new routerParams('message')
})
  .then(() => {
    console.error(`replaceUrl finish`);
  })
  .catch((err: ESObject) => {
    console.error(`replaceUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })
```

## router.replaceUrl<sup>(deprecated)</sup>

replaceUrl(options: RouterOptions, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another one in the application and destroys the current page.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [replaceUrl](arkts-apis-uicontext-router.md#replaceurl-1) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [RouterOptions](#routeroptions) | Yes  | Description of the new page.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002    | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

**Example**

```ts
class routerParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new routerParams('message')
}, (err) => {
  if (err) {
    console.error(`replaceUrl failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('replaceUrl success');
})
```

## router.replaceUrl<sup>(deprecated)</sup>

replaceUrl(options: RouterOptions, mode: RouterMode): Promise&lt;void&gt;

Replaces the current page with another one in the application and destroys the current page.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [replaceUrl](arkts-apis-uicontext-router.md#replaceurl-2) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [RouterOptions](#routeroptions) | Yes   | Description of the new page. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|


**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Failed to get the delegate. This error code is thrown only in the standard system. |
| 200002    | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class routerParams {
  data1:string;

  constructor(str:string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new routerParams('message')
}, router.RouterMode.Standard)
  .then(() => {
    console.error(`replaceUrl finish`);
  })
  .catch((err: ESObject) => {
    console.error(`replaceUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })
```

## router.replaceUrl<sup>(deprecated)</sup>

replaceUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another one in the application and destroys the current page.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [replaceUrl](arkts-apis-uicontext-router.md#replaceurl-3) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [RouterOptions](#routeroptions) | Yes   | Description of the new page. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002    | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

**Example**

```ts
class routerParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new routerParams('message')
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`replaceUrl failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('replaceUrl success');
});
```

## router.pushNamedRoute<sup>(deprecated)</sup>

pushNamedRoute(options: NamedRouterOptions): Promise&lt;void&gt;

Navigates to a page using the named route. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [pushNamedRoute](arkts-apis-uicontext-router.md#pushnamedroute) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Page routing parameters.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |
| 100003    | Page stack error. Too many pages are pushed. |
| 100004    | Named route error. The named route does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushNamedRoute({
  name: 'myPage',
  params: new routerParams('message', [123, 456, 789])
})
  .then(() => {
    console.error(`pushNamedRoute finish`);
  })
  .catch((err: ESObject) => {
    console.error(`pushNamedRoute failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })
```

For details, see [UI Development-Named Route](../../ui/arkts-routing.md#named-route).

## router.pushNamedRoute<sup>(deprecated)</sup>

pushNamedRoute(options: NamedRouterOptions, callback: AsyncCallback&lt;void&gt;): void

Navigates to a page using the named route. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [pushNamedRoute](arkts-apis-uicontext-router.md#pushnamedroute-1) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Page routing parameters.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |
| 100003    | Page stack error. Too many pages are pushed. |
| 100004    | Named route error. The named route does not exist. |

**Example**

```ts
class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushNamedRoute({
  name: 'myPage',
  params: new routerParams('message', [123, 456, 789])
}, (err) => {
  if (err) {
    console.error(`pushNamedRoute failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('pushNamedRoute success');
})
```
## router.pushNamedRoute<sup>(deprecated)</sup>

pushNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise&lt;void&gt;

Navigates to a page using the named route. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [pushNamedRoute](arkts-apis-uicontext-router.md#pushnamedroute-2) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Page routing parameters. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |
| 100003    | Page stack error. Too many pages are pushed. |
| 100004    | Named route error. The named route does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str
    this.data2 = new innerParams(tuple)
  }
}

router.pushNamedRoute({
  name: 'myPage',
  params: new routerParams('message', [123, 456, 789])
}, router.RouterMode.Standard)
  .then(() => {
    console.error(`pushNamedRoute finish`);
  })
  .catch((err: ESObject) => {
    console.error(`pushNamedRoute failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })
```

## router.pushNamedRoute<sup>(deprecated)</sup>

pushNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void

Navigates to a page using the named route. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [pushNamedRoute](arkts-apis-uicontext-router.md#pushnamedroute-3) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Page routing parameters. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |
| 100003    | Page stack error. Too many pages are pushed. |
| 100004    | Named route error. The named route does not exist. |

**Example**

```ts
class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushNamedRoute({
  name: 'myPage',
  params: new routerParams('message', [123, 456, 789])
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`pushNamedRoute failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('pushNamedRoute success');
})
```

## router.replaceNamedRoute<sup>(deprecated)</sup>

replaceNamedRoute(options: NamedRouterOptions): Promise&lt;void&gt;

Replaces the current page with another one using the named route and destroys the current page. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [replaceNamedRoute](arkts-apis-uicontext-router.md#replacenamedroute) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes  | Description of the new page.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004    | Named route error. The named route does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class routerParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new routerParams('message')
})
  .then(() => {
    console.error(`replaceNamedRoute finish`);
  })
  .catch((err: ESObject) => {
    console.error(`replaceNamedRoute failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })
```

## router.replaceNamedRoute<sup>(deprecated)</sup>

replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another one using the named route and destroys the current page. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [replaceNamedRoute](arkts-apis-uicontext-router.md#replacenamedroute-1) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes  | Description of the new page.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004    | Named route error. The named route does not exist. |

**Example**

```ts
class routerParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new routerParams('message')
}, (err) => {
  if (err) {
    console.error(`replaceNamedRoute failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('replaceNamedRoute success');
})
```

## router.replaceNamedRoute<sup>(deprecated)</sup>

replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise&lt;void&gt;

Replaces the current page with another one using the named route and destroys the current page. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [replaceNamedRoute](arkts-apis-uicontext-router.md#replacenamedroute-2) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Description of the new page. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|


**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Failed to get the delegate. This error code is thrown only in the standard system. |
| 100004    | Named route error. The named route does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class routerParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new routerParams('message')
}, router.RouterMode.Standard)
  .then(() => {
    console.error(`replaceNamedRoute finish`);
  })
  .catch((err: ESObject) => {
    console.error(`replaceNamedRoute failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })
```

## router.replaceNamedRoute<sup>(deprecated)</sup>

replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another one using the named route and destroys the current page. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [replaceNamedRoute](arkts-apis-uicontext-router.md#replacenamedroute-3) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Description of the new page. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).
> **NOTE**
>
> The following error codes returned by this API are all of the string type.

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004    | Named route error. The named route does not exist. |

**Example**

```ts
class routerParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new routerParams('message')
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`replaceNamedRoute failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('replaceNamedRoute success');
});
```

## router.back<sup>(deprecated)</sup>

back(options?: RouterOptions ): void

Returns to the previous page or a specified page, which deletes all pages between the current page and the target page.

> **NOTE**
>
> This API is deprecated since API version 18. You are advised to use [back](arkts-apis-uicontext-router.md#back) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                           | Mandatory| Description                                                        |
| ------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| options | [RouterOptions](#routeroptions) | No  | Description of the target page. The **url** parameter indicates the URL of the page to return to. If the specified page does not exist in the navigation stack, no action is taken. If no URL is set, the application returns to the previous page, and the page is not rebuilt. Pages are only reclaimed after being popped from the navigation stack. Setting **url** to the special value **"/"** has no effect. If the named route is used, the provided URL must be the name of the named route.|

**Example**

```ts
this.getUIContext().getRouter().back({ url: 'pages/detail' });
```

## router.back<sup>(deprecated)</sup>

back(index: number, params?: Object): void;

Returns to the specified page, which deletes all pages between the current page and the target page.

> **NOTE**
>
> This API is supported since API version 12 and deprecated since API version 18. You are advised to use [back](arkts-apis-uicontext-router.md#back12) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 12, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| index | number | Yes   | Index of the target page to navigate to. The index starts from 1 from the bottom to the top of the stack.|
| params    | Object      | No   | Parameters carried when returning to the page.|

**Example**

```ts
this.getUIContext().getRouter().back(1);
```
```ts
this.getUIContext().getRouter().back(1, { info: 'From Home' }); // Returning with parameters.
```

## router.clear<sup>(deprecated)</sup>

clear(): void

Clears all historical pages in the stack and retains only the current page at the top of the stack.

> **NOTE**
>
> This API is deprecated since API version 18. You are advised to use [clear](arkts-apis-uicontext-router.md#clear) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
this.getUIContext().getRouter().clear();
```

## router.getLength<sup>(deprecated)</sup>

getLength(): string

Obtains the number of pages in the current stack.

> **NOTE**
>
> This API is deprecated since API version 18. You are advised to use [getLength](arkts-apis-uicontext-router.md#getlength) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                |
| ------ | ------------------ |
| string | Number of pages in the stack. The maximum value is **32**.|

**Example**

```ts
let size = this.getUIContext().getRouter().getLength();
console.log('pages stack size = ' + size);
```

## router.getState<sup>(deprecated)</sup>

getState(): RouterState

Obtains state information about the page at the top of the navigation stack.

> **NOTE**
>
> This API is deprecated since API version 18. You are advised to use [getState](arkts-apis-uicontext-router.md#getstate) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                         | Description     |
| --------------------------- | ------- |
| [RouterState](#routerstate) | Page routing state.|

**Example**

```ts
let page = this.getUIContext().getRouter().getState();
console.log('current index = ' + page.index);
console.log('current name = ' + page.name);
console.log('current path = ' + page.path);
```

## router.getStateByIndex<sup>(deprecated)</sup>

getStateByIndex(index: number): RouterState | undefined

Obtains the status information about a page by its index.

> **NOTE**
>
> This API is supported since API version 12 and deprecated since API version 18. You are advised to use [getStateByIndex](arkts-apis-uicontext-router.md#getstatebyindex12) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 12, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| index    | number | Yes  | Index of the target page. The index starts from 1 from the bottom to the top of the stack.|

**Return value**

| Type                         | Description     |
| --------------------------- | ------- |
| [RouterState](#routerstate) \| undefined | State information about the target page; **undefined** if the specified index does not exist.|

**Example**

```ts
let options: router.RouterState | undefined = router.getStateByIndex(1);
if (options != undefined) {
  console.log('index = ' + options.index);
  console.log('name = ' + options.name);
  console.log('path = ' + options.path);
  console.log('params = ' + options.params);
}
```
## router.getStateByUrl<sup>(deprecated)</sup>

getStateByUrl(url: string): Array&lt;RouterState&gt;

Obtains the status information about a page by its URL.

> **NOTE**
>
> This API is supported since API version 12 and deprecated since API version 18. You are advised to use [getStateByUrl](arkts-apis-uicontext-router.md#getstatebyurl12) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 12, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| url    | string | Yes  | URL of the target page. |

**Return value**

| Type                         | Description     |
| --------------------------- | ------- |
| Array<[RouterState](#routerstate)> | Page routing state.|

**Example**

```ts
let options: Array<router.RouterState> = router.getStateByUrl('pages/index');
for (let i: number = 0; i < options.length; i++) {
  console.log('index = ' + options[i].index);
  console.log('name = ' + options[i].name);
  console.log('path = ' + options[i].path);
  console.log('params = ' + options[i].params);
}
```

## RouterState

Describes the page routing state.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type  | Mandatory| Description                                                        |
| ----- | ------ | ---- | ------------------------------------------------------------ |
| index | number | Yes  | Index of the current page in the stack. The index starts from 1 from the bottom to the top of the stack.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| name  | string | Yes | Name of the current page, that is, the file name.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| path  | string | Yes  | Path of the current page.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| params<sup>12+</sup>  | Object |  Yes | Parameters carried on the current page.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                        |

## router.showAlertBeforeBackPage<sup>(deprecated)</sup>

showAlertBeforeBackPage(options: EnableAlertOptions): void

Enables the display of a confirm dialog box before returning to the previous page.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [showAlertBeforeBackPage](arkts-apis-uicontext-router.md#showalertbeforebackpage) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [EnableAlertOptions](#enablealertoptions) | Yes   | Description of the dialog box.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Router Error Codes](errorcode-router.md).

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | Internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  this.getUIContext().getRouter().showAlertBeforeBackPage({
    message: 'Message Info'
  });
} catch (err) {
  console.error(`showAlertBeforeBackPage failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
}
```
## EnableAlertOptions

Describes the confirm dialog box.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type    | Mandatory  | Description      |
| ------- | ------ | ---- | -------- |
| message | string | Yes   | Content displayed in the confirm dialog box.|

## router.hideAlertBeforeBackPage<sup>(deprecated)</sup>

hideAlertBeforeBackPage(): void

Disables the display of a confirm dialog box before returning to the previous page.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [hideAlertBeforeBackPage](arkts-apis-uicontext-router.md#hidealertbeforebackpage) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
this.getUIContext().getRouter().hideAlertBeforeBackPage();   
```

##  router.getParams<sup>(deprecated)</sup>

getParams(): Object

Obtains the parameters passed from the page that initiates redirection to the current page.

> **NOTE**
>
> This API is deprecated since API version 18. You are advised to use [getParams](arkts-apis-uicontext-router.md#getparams) instead on the obtained [Router](arkts-apis-uicontext-router.md) object.
>
> Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type  | Description                              |
| ------ | ---------------------------------- |
| object | Parameters passed from the page that initiates redirection to the current page.|

**Example**

```ts
this.getUIContext().getRouter().getParams();
```

## RouterOptions

Describes the page routing options.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

| Name  | Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| url    | string | Yes  | URL of the target page, in either of the following formats:<br>- Absolute path of the page. The value is available in the pages list in the **config.json** file, for example:<br>- pages/index/index<br>- pages/detail/detail<br>- special value. If the value of url is **"/"**, the application navigates to the home page. By default, the home page is set to the first item in the **src** value array.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| params | Object | No  | Data that needs to be passed to the target page during redirection. The received data becomes invalid when the page is switched to another page. The target page can use **router.getParams()** to obtain the passed parameters, for example, **this.keyValue** (**keyValue** is the value of a key in **params**). In the web-like paradigm, these parameters can be directly used on the target page. If the field specified by **key** already exists on the target page, the passed value of the key will be displayed.<br>**NOTE**<br>The **params** parameter cannot pass objects returned by methods and system APIs, for example, **PixelMap** objects defined and returned by media APIs. To pass such objects, extract from them the basic type attributes to be passed, and then construct objects of the object type.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| recoverable<sup>14+</sup> | boolean | No  | Whether the corresponding page is recoverable.<br>Default value: **true**, indicating that the page is recoverable<br><br>**NOTE**<br> If an application is switched to the background and is later closed by the system due to resource constraints or other reasons, a page marked as recoverable can be restored by the system when the application is brought back to the foreground. For more details, see [UIAbility Backup and Restore](../../application-models/ability-recover-guideline.md).|

  > **NOTE**
  > The page routing stack supports a maximum of 32 pages.

## RouterMode<sup>9+</sup>

Enumerates the routing modes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                                                        |
| -------- | --- | ------------------------------------------------------------ |
| Standard | 0 | Multi-instance mode. It is the default routing mode.<br>The target page is added to the top of the page stack, regardless of whether a page with the same URL exists in the stack.<br>**NOTE**<br>If no routing mode is used, the navigation will be carried out according to the default multi-instance mode.|
| Single   | 1 | Singleton mode.<br>If the URL of the target page already exists in the page stack, the page is moved to the top of the stack.<br>If the URL of the target page does not exist in the page stack, the page is redirected to in multi-instance mode.|

## NamedRouterOptions<sup>10+</sup>

Describes the named route options.

| Name  | Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| name   | string | Yes  | Name of the target named route.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full|
| params | Object | No  | Data that needs to be passed to the target page during redirection. The target page can use **router.getParams()** to obtain the passed parameters, for example, **this.keyValue** (**keyValue** is the value of a key in **params**). In the web-like paradigm, these parameters can be directly used on the target page. If the field specified by **key** already exists on the target page, the passed value of the key will be displayed.<br>**NOTE**<br>The **params** parameter cannot pass objects returned by methods and system APIs, for example, **PixelMap** objects defined and returned by media APIs. To pass such objects, extract from them the basic type attributes to be passed, and then construct objects of the object type.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| recoverable<sup>14+</sup> | boolean | No  | Whether the corresponding page is recoverable.<br>Default value: **true**, indicating that the page is recoverable<br><br>**NOTE**<br> If an application is switched to the background and is later closed by the system due to resource constraints or other reasons, a page marked as recoverable can be restored by the system when the application is brought back to the foreground. For more details, see [UIAbility Backup and Restore](../../application-models/ability-recover-guideline.md).<br>**System capability**: SystemCapability.ArkUI.ArkUI.Lite|

## Examples

### JavaScript-based Web-like Development Paradigm

The following sample code applies only to JavaScript files, not ArkTS files.

<!--code_no_check-->

```js
// Current page
export default {
  pushPage() {
    router.pushUrl({
      url: 'pages/detail/detail',
      params: {
        data1: 'message'
      }
    });
  }
}
```
<!--code_no_check-->

```js
// detail page
export default {
  onInit() {
    console.info('showData1:' + this.getUIContext().getRouter().getParams()['data1']);
  }
}
```

### TypeScript-based Declarative Development Paradigm

> **NOTE**
> 
> Directly using **router** can lead to [ambiguous instance issues](../../ui/arkts-global-interface.md). To avoid this, obtain a **UIContext** instance using **getUIContext**, and then obtain the associated **Router** object using [getRouter](arkts-apis-uicontext-uicontext.md#getrouter).

<!--deperecated_code_no_check-->
```ts
// Navigate to the target page through router.pushUrl with the params parameter carried.
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit'

// Define the class for passing parameters.
class innerParams {
  array: number[];

  constructor(tuple: number[]) {
    this.array = tuple;
  }
}

class routerParams {
  text: string;
  data: innerParams;

  constructor(str: string, tuple: number[]) {
    this.text = str;
    this.data = new innerParams(tuple);
  }
}

@Entry
@Component
struct Index {
  async routePage() {
    let options: router.RouterOptions = {
      url: 'pages/second',
      params: new routerParams('This is the value on the first page', [12, 45, 78])
    }
    // You are advised to use this.getUIContext().getRouter().pushUrl().
    router.pushUrl(options)
      .then(() => {
        console.error(`pushUrl finish`);
      })
      .catch((err: ESObject) => {
        console.error(`pushUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
      })
    }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text('This is the first page.')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
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
// Receive the transferred parameters on the second page.
import { router } from '@kit.ArkUI';

class innerParams {
  array: number[];

  constructor(tuple: number[]) {
    this.array = tuple;
  }
}

class routerParams {
  text: string;
  data: innerParams;

  constructor(str: string, tuple: number[]) {
    this.text = str;
    this.data = new innerParams(tuple);
  }
}

@Entry
@Component
struct Second {
  private content: string = "This is the second page.";
  // You are advised to use this.getUIContext().getRouter().getParams().
  @State text: string = (this.getUIContext().getRouter().getParams() as routerParams).text;
  @State data: object = (this.getUIContext().getRouter().getParams() as routerParams).data;
  @State secondData: string = '';

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text(`${this.content}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      Text(this.text)
        .fontSize(30)
        .onClick(() => {
          this.secondData = (this.data['array'][1]).toString();
        })
        .margin({ top: 20 })
      Text(`This is the data passed from the first page: ${this.secondData}`)
        .fontSize(20)
        .margin({ top: 20 })
        .backgroundColor('red')
    }
    .width('100%')
    .height('100%')
  }
}
```

## router.push<sup>(deprecated)</sup>

push(options: RouterOptions): void

Navigates to a specified page in the application.

This API is deprecated since API version 9. You are advised to use [pushUrl](arkts-apis-uicontext-router.md#pushurl) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters.|


**Example**

```ts
class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class routerParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.push({
  url: 'pages/routerpage2',
  params: new routerParams('message', [123, 456, 789])
});
```

## router.replace<sup>(deprecated)</sup>

replace(options: RouterOptions): void

Replaces the current page with another one in the application and destroys the current page.

This API is deprecated since API version 9. You are advised to use [replaceUrl](arkts-apis-uicontext-router.md#replaceurl) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [RouterOptions](#routeroptions) | Yes  | Description of the new page.|

**Example**

```ts
class routerParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replace({
  url: 'pages/detail',
  params: new routerParams('message')
});
```

## router.enableAlertBeforeBackPage<sup>(deprecated)</sup>

enableAlertBeforeBackPage(options: EnableAlertOptions): void

Enables the display of a confirm dialog box before returning to the previous page.

This API is deprecated since API version 9. You are advised to use [showAlertBeforeBackPage](arkts-apis-uicontext-router.md#showalertbeforebackpage) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [EnableAlertOptions](#enablealertoptions) | Yes   | Description of the dialog box.|

**Example**

```ts
router.enableAlertBeforeBackPage({
  message: 'Message Info'
});
```

## router.disableAlertBeforeBackPage<sup>(deprecated)</sup>

disableAlertBeforeBackPage(): void

Disables the display of a confirm dialog box before returning to the previous page.

This API is deprecated since API version 9. You are advised to use [hideAlertBeforeBackPage](arkts-apis-uicontext-router.md#hidealertbeforebackpage) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
router.disableAlertBeforeBackPage();
```
