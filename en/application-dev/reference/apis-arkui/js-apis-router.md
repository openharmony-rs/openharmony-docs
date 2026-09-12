# @ohos.router (Page Routing) (Not Recommended)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @huangxiaolinabc-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=6e65e5ab1f4f5d9b7a30f0ce59276e478113d638 translatedAt=2026-09-01T03:27:14.780Z pushedAt=2026-09-02T03:13:46.070Z -->

This module provides page routing capabilities, including supporting page navigation and replacement via URLs or named routes, returning to the previous page or a specified page, managing the page stack, obtaining page states and navigation parameters, and setting page return confirm dialog boxes. It is applicable to scenarios where page navigation and flow are required within an application.

For routing management, it is recommended that you use the [Navigation](../../ui/arkts-navigation-architecture.md) component instead as your application routing framework.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Page routing APIs can be invoked only after page rendering is complete. Do not call these APIs in **onInit** and **onReady** when the page is still in the rendering phase.
>
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - When using [pushUrl](arkts-apis-uicontext-router.md#pushurl-1) or [pushNamedRoute](arkts-apis-uicontext-router.md#pushnamedroute-1) with a callback to return the result, be aware that the stack information obtained through the callback using APIs such as [getStackSize](arkts-apis-uicontext-router.md#getstacksize23) represents an intermediate state during the navigation operation. This temporary state might differ from the final stack information obtained through [getStackSize](arkts-apis-uicontext-router.md#getstacksize23) after the stack operation is complete.

## Modules to Import

```ts
import { router } from '@kit.ArkUI';
```

## router.pushUrl<sup>(deprecated)</sup>

pushUrl(options: RouterOptions): Promise&lt;void&gt;

Navigates to a specified page in the application.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [pushUrl(options: router.RouterOptions)](arkts-apis-uicontext-router.md#pushurl) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

import { BusinessError } from '@kit.BasicServicesKit';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
})
  .then(() => {
    console.info(`pushUrl finish`);
  })
  .catch((err: BusinessError) => {
    console.error(`pushUrl failed. Code: ${err.code}, message: ${err.message}`);
  });
```

## router.pushUrl<sup>(deprecated)</sup>

pushUrl(options: RouterOptions, callback: AsyncCallback&lt;void&gt;): void

Navigates to a specified page in the application.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [pushUrl(options: router.RouterOptions, callback: AsyncCallback&lt;void&gt;)](arkts-apis-uicontext-router.md#pushurl-1) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the page routing result.<br>When the page redirection is successful, the value of **error** is **undefined**. When the page redirection fails, the value of **error** is the error object returned by the system.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
}, (err) => {
  if (err) {
    console.error(`pushUrl failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('pushUrl success');
});
```
## router.pushUrl<sup>(deprecated)</sup>

pushUrl(options: RouterOptions, mode: RouterMode): Promise&lt;void&gt;

Navigates to a specified page in the application.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [pushUrl(options: router.RouterOptions, mode: router.RouterMode)](arkts-apis-uicontext-router.md#pushurl-2) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

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
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

import { BusinessError } from '@kit.BasicServicesKit';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
}, router.RouterMode.Standard)
  .then(() => {
    console.info(`pushUrl finish`);
  })
  .catch((err: BusinessError) => {
    console.error(`pushUrl failed. Code: ${err.code}, message: ${err.message}`);
  })
```

## router.pushUrl<sup>(deprecated)</sup>

pushUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void

Navigates to a specified page in the application.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [pushUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;)](arkts-apis-uicontext-router.md#pushurl-3) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|
| callback | AsyncCallback&lt;void&gt;      | Yes   | Callback used to return the page navigation result.<br/>When the page navigation is successful, **error** is **undefined**. When the page navigation fails, **error** is the error object returned by the system.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`pushUrl failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('pushUrl success');
})
```

## router.replaceUrl<sup>(deprecated)</sup>

replaceUrl(options: RouterOptions): Promise&lt;void&gt;

Replaces the current page with another one in the application and destroys the current page. This API cannot be used to configure page transition effects. To configure page transition effects, use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18 except for lite wearables. You are advised to use [replaceUrl(options: router.RouterOptions)](arkts-apis-uicontext-router.md#replaceurl) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [RouterOptions](#routeroptions) | Yes  | Description of the new page.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

import { BusinessError } from '@kit.BasicServicesKit';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new RouterParams('message')
})
  .then(() => {
    console.info(`replaceUrl finish`);
  })
  .catch((err: BusinessError) => {
    console.error(`replaceUrl failed. Code: ${err.code}, message: ${err.message}`);
  })
```

## router.replaceUrl<sup>(deprecated)</sup>

replaceUrl(options: RouterOptions, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another one in the application and destroys the current page. This API cannot be used to configure page transition effects. To configure page transition effects, use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18 except for lite wearables. You are advised to use [replaceUrl(options: router.RouterOptions, callback: AsyncCallback&lt;void&gt;)](arkts-apis-uicontext-router.md#replaceurl-1) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [RouterOptions](#routeroptions) | Yes  | Description of the new page.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the page replacement result.<br>When the page replacement is successful, the value of **error** is **undefined**. When the page replacement fails, the value of **error** is the error object returned by the system.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new RouterParams('message')
}, (err) => {
  if (err) {
    console.error(`replaceUrl failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('replaceUrl success');
})
```

## router.replaceUrl<sup>(deprecated)</sup>

replaceUrl(options: RouterOptions, mode: RouterMode): Promise&lt;void&gt;

Replaces the current page with another one in the application and destroys the current page. This API cannot be used to configure page transition effects. To configure page transition effects, use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18 except for lite wearables. You are advised to use [replaceUrl(options: router.RouterOptions, mode: router.RouterMode)](arkts-apis-uicontext-router.md#replaceurl-2) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [RouterOptions](#routeroptions) | Yes   | Description of the new page. |
| mode    | [RouterMode](#routermode9)      | Yes   | Mode for page replacement.|


**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

import { BusinessError } from '@kit.BasicServicesKit';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new RouterParams('message')
}, router.RouterMode.Standard)
  .then(() => {
    console.info(`replaceUrl finish`);
  })
  .catch((err: BusinessError) => {
    console.error(`replaceUrl failed. Code: ${err.code}, message: ${err.message}`);
  })
```

## router.replaceUrl<sup>(deprecated)</sup>

replaceUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with another one in the application and destroys the current page. This API cannot be used to configure page transition effects. To configure page transition effects, use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18 except for lite wearables. You are advised to use [replaceUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;)](arkts-apis-uicontext-router.md#replaceurl-3) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [RouterOptions](#routeroptions) | Yes   | Description of the new page. |
| mode    | [RouterMode](#routermode9)      | Yes    | Mode used for replacing the page. |
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the page replacement result.<br>When the page replacement is successful, the value of **error** is **undefined**. When the page replacement fails, the value of **error** is the error object returned by the system.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new RouterParams('message')
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`replaceUrl failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('replaceUrl success');
});
```

## router.pushNamedRoute<sup>(deprecated)</sup>

pushNamedRoute(options: NamedRouterOptions): Promise&lt;void&gt;

Navigates to a page using the named route.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [pushNamedRoute(options: router.NamedRouterOptions)](arkts-apis-uicontext-router.md#pushnamedroute) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Page routing parameters.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

import { BusinessError } from '@kit.BasicServicesKit';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.pushNamedRoute({
  name: 'myPage',
  params: new RouterParams('message', [123, 456, 789])
})
  .then(() => {
    console.info(`pushNamedRoute finish`);
  })
  .catch((err: BusinessError) => {
    console.error(`pushNamedRoute failed. Code: ${err.code}, message: ${err.message}`);
  })
```

For details, see [Named Route](../../ui/arkts-routing.md#named-route).

## router.pushNamedRoute<sup>(deprecated)</sup>

pushNamedRoute(options: NamedRouterOptions, callback: AsyncCallback&lt;void&gt;): void

Navigates to a page using the named route.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [pushNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback&lt;void&gt;)](arkts-apis-uicontext-router.md#pushnamedroute-1) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Page routing parameters.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the page routing result.<br>When the page redirection is successful, the value of **error** is **undefined**. When the page redirection fails, the value of **error** is the error object returned by the system. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.pushNamedRoute({
  name: 'myPage',
  params: new RouterParams('message', [123, 456, 789])
}, (err) => {
  if (err) {
    console.error(`pushNamedRoute failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('pushNamedRoute success');
})
```
## router.pushNamedRoute<sup>(deprecated)</sup>

pushNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise&lt;void&gt;

Navigates to a page using the named route.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode)](arkts-apis-uicontext-router.md#pushnamedroute-2) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Page routing parameters. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

import { BusinessError } from '@kit.BasicServicesKit';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.pushNamedRoute({
  name: 'myPage',
  params: new RouterParams('message', [123, 456, 789])
}, router.RouterMode.Standard)
  .then(() => {
    console.info(`pushNamedRoute finish`);
  })
  .catch((err: BusinessError) => {
    console.error(`pushNamedRoute failed. Code: ${err.code}, message: ${err.message}`);
  })
```

## router.pushNamedRoute<sup>(deprecated)</sup>

pushNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void

Navigates to a page using the named route.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;)](arkts-apis-uicontext-router.md#pushnamedroute-3) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Page routing parameters. |
| mode    | [RouterMode](#routermode9)      | Yes   | Routing mode.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the page routing result.<br>When the page redirection is successful, the value of **error** is **undefined**. When the page redirection fails, the value of **error** is the error object returned by the system.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.pushNamedRoute({
  name: 'myPage',
  params: new RouterParams('message', [123, 456, 789])
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`pushNamedRoute failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('pushNamedRoute success');
})
```

## router.replaceNamedRoute<sup>(deprecated)</sup>

replaceNamedRoute(options: NamedRouterOptions): Promise&lt;void&gt;

Replaces the current page with the specified named route page and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [replaceNamedRoute(options: router.NamedRouterOptions)](arkts-apis-uicontext-router.md#replacenamedroute) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes  | Description of the new page.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

import { BusinessError } from '@kit.BasicServicesKit';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new RouterParams('message')
})
  .then(() => {
    console.info(`replaceNamedRoute finish`);
  })
  .catch((err: BusinessError) => {
    console.error(`replaceNamedRoute failed. Code: ${err.code}, message: ${err.message}`);
  })
```

## router.replaceNamedRoute<sup>(deprecated)</sup>

replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with the specified named route page and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [replaceNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback&lt;void&gt;)](arkts-apis-uicontext-router.md#replacenamedroute-1) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes  | Description of the new page.|
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the page replacement result.<br>When the page replacement is successful, the value of **error** is **undefined**. When the page replacement fails, the value of **error** is the error object returned by the system.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new RouterParams('message')
}, (err) => {
  if (err) {
    console.error(`replaceNamedRoute failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('replaceNamedRoute success');
})
```

## router.replaceNamedRoute<sup>(deprecated)</sup>

replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise&lt;void&gt;

Replaces the current page with the specified named route page and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode)](arkts-apis-uicontext-router.md#replacenamedroute-2) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Description of the new page. |
| mode    | [RouterMode](#routermode9)      | Yes   | Mode for page replacement.|


**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

import { BusinessError } from '@kit.BasicServicesKit';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new RouterParams('message')
}, router.RouterMode.Standard)
  .then(() => {
    console.info(`replaceNamedRoute finish`);
  })
  .catch((err: BusinessError) => {
    console.error(`replaceNamedRoute failed. Code: ${err.code}, message: ${err.message}`);
  })
```

## router.replaceNamedRoute<sup>(deprecated)</sup>

replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void

Replaces the current page with the specified named route page and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;)](arkts-apis-uicontext-router.md#replacenamedroute-3) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| options | [NamedRouterOptions](#namedrouteroptions10) | Yes   | Description of the new page. |
| mode    | [RouterMode](#routermode9)      | Yes    | Mode used for replacing the page. |
| callback | AsyncCallback&lt;void&gt;      | Yes  | Callback used to return the page replacement result.<br>When the page replacement is successful, the value of **error** is **undefined**. When the page replacement fails, the value of **error** is the error object returned by the system.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Router Error Codes](errorcode-router.md), and [API Call Error Codes](errorcode-internal.md).
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
import { router } from '@kit.ArkUI';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new RouterParams('message')
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`replaceNamedRoute failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('replaceNamedRoute success');
});
```

## router.back<sup>(deprecated)</sup>

back(options?: RouterOptions ): void

Returns to the previous page or a specified page, and removes all pages between the current page and the specified page. If [showAlertBeforeBackPage](#routershowalertbeforebackpagedeprecated) has been called to enable the return confirm dialog box, a confirm dialog box will be displayed before the return operation is executed. The return is performed only after the user confirms; if the user cancels, the return is not performed.

> **NOTE**
>
> - This API is supported since API version 8 and deprecated since API version 18. You are advised to use [back](arkts-apis-uicontext-router.md#back)(options?: router.RouterOptions) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                           | Mandatory| Description                                                        |
| ------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| options | [RouterOptions](#routeroptions) | No | Description of the target page, where **url** indicates the route address of the target page to return to. If the page with the specified URL does not exist in the page stack, the current back request will not be responded to. If **url** is not set, the previous page is returned, the page will not be rebuilt, and the page in the page stack will not be reclaimed, but will be reclaimed after being popped out of the stack. **back** indicates the back API, and setting **url** to the special value **"/"** does not take effect. If the page is navigated to using a named route, the **url** passed in must be the name of the named route. |

**Example**

```ts
this.getUIContext().getRouter().back({ url: 'pages/detail' });
```

## router.back<sup>(deprecated)</sup>

back(index: number, params?: Object): void;

Returns to a specified page, and removes all pages between the current page and the specified page. If [showAlertBeforeBackPage](#routershowalertbeforebackpagedeprecated) has been called to enable the return confirm dialog box, a confirm dialog box will be displayed before the return operation is executed. The return is performed only after the user confirms; if the user cancels, the return is not performed.

> **NOTE**
>
> - This API is supported since API version 12 and deprecated since API version 18. You are advised to use [back(index: number, params?: Object)](arkts-apis-uicontext-router.md#back12) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 12, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| index | number | Yes    | Index of the target page to return to. The value range is [1, Page stack size], and the maximum page stack size is 32. The index starts from 1 from the bottom to the top of the stack. No response is returned if the index does not exist or exceeds the valid range of the page stack. |
| params    | Object      | No    | Parameters carried when returning to the page.<br/>**NOTE**<br/>The **params** parameter can only pass serializable parameters. It cannot pass methods or objects returned by system APIs (for example, the **PixelMap** object defined and returned by media APIs). You are advised to extract the basic-type attributes that need to be passed from the objects returned by system APIs, and construct an object-type object for passing. |

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
> - This API is supported since API version 8 and deprecated since API version 18. You are advised to use [clear](arkts-apis-uicontext-router.md#clear) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

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
> - This API is supported since API version 8 and deprecated since API version 18. You are advised to use [getLength](arkts-apis-uicontext-router.md#getlengthdeprecated) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                |
| ------ | ------------------ |
| string | Number of pages in the stack. The maximum value is **32**.|

**Example**

```ts
let size = this.getUIContext().getRouter().getLength();
console.info('pages stack size = ' + size);
```

## router.getState<sup>(deprecated)</sup>

getState(): RouterState

Obtains state information about the page at the top of the navigation stack.

> **NOTE**
>
> - This API is supported since API version 8 and deprecated since API version 18. You are advised to use [getState](arkts-apis-uicontext-router.md#getstate) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                         | Description     |
| --------------------------- | ------- |
| [RouterState](#routerstate) | State of the page at the top of the stack, including the page index, name, path, and parameters. |

**Example**

```ts
let page = this.getUIContext().getRouter().getState();
console.info('current index = ' + page.index);
console.info('current name = ' + page.name);
console.info('current path = ' + page.path);
```

## router.getStateByIndex<sup>(deprecated)</sup>

getStateByIndex(index: number): RouterState | undefined

Obtains the status information about a page by its index.

> **NOTE**
>
> - This API is supported since API version 12 and deprecated since API version 18. You are advised to use [getStateByIndex](arkts-apis-uicontext-router.md#getstatebyindex12) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 12, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| index    | number | Yes   | Index of the page to obtain. The value range is [1, Page stack size], and the maximum page stack size is 32. The index starts from 1 from the bottom to the top of the stack. If the index does not exist, **undefined** is returned. |

**Return value**

| Type                         | Description     |
| --------------------------- | ------- |
| [RouterState](#routerstate) \| undefined | State of the page at the corresponding index, including the page index, name, path, and parameters. **undefined** is returned if the index does not exist. |

**Example**

```ts
import { router } from '@kit.ArkUI';

let options: router.RouterState | undefined = router.getStateByIndex(1);
if (options != undefined) {
  console.info('index = ' + options.index);
  console.info('name = ' + options.name);
  console.info('path = ' + options.path);
  console.info(`params = ${JSON.stringify(options.params)}`);
}
```
## router.getStateByUrl<sup>(deprecated)</sup>

getStateByUrl(url: string): Array&lt;RouterState&gt;

Obtains the status information about a page by its URL.

> **NOTE**
>
> - This API is supported since API version 12 and deprecated since API version 18. You are advised to use [getStateByUrl](arkts-apis-uicontext-router.md#getstatebyurl12) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 12, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description        |
| ------- | ------------------------------- | ---- | ---------- |
| url    | string | Yes  | URL of the page whose information is to be obtained. The URL is an absolute page path provided in the **pages** list of the configuration file, for example, **pages/index/index**.  |

**Return value**

| Type                         | Description     |
| --------------------------- | ------- |
| Array<[RouterState](#routerstate)> | Array of page state information matching the specified URL. Each element contains the page index, name, path, and parameters. |

**Example**

```ts
import { router } from '@kit.ArkUI';

let options: Array<router.RouterState> = router.getStateByUrl('pages/index');
for (let i: number = 0; i < options.length; i++) {
  console.info('index = ' + options[i].index);
  console.info('name = ' + options[i].name);
  console.info('path = ' + options[i].path);
  console.info('params = ' + options[i].params);
}
```

## RouterState

Describes the page routing state.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type  | Read-Only| Optional| Description                                                        |
| ----- | ------ | ---- | ---- | ------------------------------------------------------------ |
| index | number | No  | No  | Index of the current page in the stack. The index starts from 1 from the bottom to the top of the stack.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| name  | string | No  | No  | Name of the current page, that is, the file name.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| path  | string | No  | No  | Path of the current page.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| params<sup>12+</sup>  | Object | No   | No   | Parameters carried by the current page.<br/>**Note** <br/>The **params** parameter can only pass serializable parameters. It cannot pass methods or objects returned by system APIs (for example, the **PixelMap** object defined and returned by media APIs). You are advised to extract the basic-type attributes that need to be passed from the objects returned by system APIs, and construct an object for passing.<br/>**Atomic service API**: This API can be used in atomic services since API version 12.<br/>**Model restriction**: This API can be used only in the stage model.                                         |

## router.showAlertBeforeBackPage<sup>(deprecated)</sup>

showAlertBeforeBackPage(options: EnableAlertOptions): void

Enables the display of a confirm dialog box before returning to the previous page. After this API is called, a confirm dialog box will be displayed when [back](#routerbackdeprecated) is executed to return to a page. The page return operation is performed only after the user confirms. This is applicable to scenarios where you need to prevent data loss caused by accidental return operations, for example, when the user is filling in a form, editing a document, or making a payment, a confirm dialog box is displayed to avoid accidental exit.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [showAlertBeforeBackPage](arkts-apis-uicontext-router.md#showalertbeforebackpage) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [EnableAlertOptions](#enablealertoptions) | Yes   | Description of the dialog box.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [API Call Error Codes](errorcode-internal.md).

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
  console.error(`showAlertBeforeBackPage failed. Code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}
```
## EnableAlertOptions

Describes the confirm dialog box.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type    | Read-Only| Optional| Description      |
| ------- | ------ | ---- | ---- | -------- |
| message | string | No   | No   | Content displayed in the confirm dialog box.|

## router.hideAlertBeforeBackPage<sup>(deprecated)</sup>

hideAlertBeforeBackPage(): void

Disables the display of a confirm dialog box before returning to the previous page. After this API is called, the return confirm dialog box enabled by [showAlertBeforeBackPage](#routershowalertbeforebackpagedeprecated) will be closed, and the [back](#routerbackdeprecated) operation will no longer display a confirm dialog box but will directly perform the page return.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [hideAlertBeforeBackPage](arkts-apis-uicontext-router.md#hidealertbeforebackpage) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.

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
> - This API is supported since API version 8 and deprecated since API version 18. You are advised to use [getParams](arkts-apis-uicontext-router.md#getparams) instead. Before calling this API, you need to obtain the [Router](arkts-apis-uicontext-router.md) instance using [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getRouter](arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Router](arkts-apis-uicontext-router.md) object associated with the current UI context.
>
> **getParams** obtains only the parameters of the current page and does not clear the parameters associated with the page.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type  | Description                              |
| ------ | ---------------------------------- |
| Object | Parameters passed from the page that initiates redirection to the current page.|

**Example**

```ts
this.getUIContext().getRouter().getParams();
```

## RouterOptions

Describes the page routing options.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

| Name  | Type  | Read-Only| Optional| Description                                                        |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| url    | string | No   | No   | URL of the target page, which can be in either of the following formats:<br/>-&nbsp;Absolute page path, provided by the **pages** list in the configuration file, for example:<br/>&nbsp;&nbsp;-&nbsp;pages/index/index<br/>&nbsp;&nbsp;-&nbsp;pages/detail/detail<br/>-&nbsp;Special value. If the value of **url** is **"/"**, the home page is redirected to. The home page defaults to the first data item in the **src** array of the page navigation configuration.<br/>If a nonexistent or invalid URL path is passed in, the navigation fails. For details about the error codes, see the error code description of each API.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| params | Object | No | Yes | Data that needs to be passed to the target page during redirection. The received data becomes invalid when the page is switched to another page. After navigation to the target page, use **router.getParams()** to obtain the passed parameters. In addition, in the web-like paradigm, parameters can also be used directly on the page, for example, **this.keyValue** (where **keyValue** is the value of a key in the **params** parameter during navigation). If the target page already has this parameter, its value will be overwritten by the passed parameter value.<br/>**NOTE**<br/>The **params** parameter can only pass serializable parameters. It cannot pass methods or objects returned by system APIs (for example, the **PixelMap** object defined and returned by media APIs). Passing non-serializable parameters may cause parameter transfer failure or application running exceptions. You are advised to extract the basic-type attributes that need to be passed from the objects returned by system APIs, and construct an object-type object for passing.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| recoverable<sup>14+</sup> | boolean | No  | Yes  | Whether the corresponding page is recoverable.<br>Default value: **true**. <br>**true**: The corresponding page is recoverable.<br>**false**: The corresponding page is not recoverable.<br>**NOTE**<br> If an application is switched to the background and is later closed by the system due to resource constraints or other reasons, a page marked as recoverable can be restored by the system when the application is brought back to the foreground. For more details, see [UIAbility Backup and Restore](../../application-models/ability-recover-guideline.md).|

  > **NOTE**
  > The page routing stack supports a maximum of 32 pages.

## RouterMode<sup>9+</sup>

Enumerates the routing modes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                                                        |
| -------- | --- | ------------------------------------------------------------ |
| Standard | 0 | Multi-instance mode, which is also the default page navigation mode. <br/>The target page is added to the top of the page stack, regardless of whether a page with the same URL already exists in the stack. This mode is suitable for scenarios where multiple identical pages need to be retained, for example, when product detail pages are browsed, each product requires an independent page instance.<br/>**NOTE**<br/>If no routing mode is specified, the default multi-instance mode is used for page navigation. |
| Single   | 1 | Singleton mode.<br/>If the URL of the target page already exists in the page stack, the page with that URL is moved to the top of the stack.<br/>If the URL of the target page has no matching page in the page stack, the default multi-instance mode is used for page navigation. This mode is suitable for scenarios where a unique page instance needs to be maintained, for example, pages such as the home page and login page that should not appear repeatedly in the stack. |

## NamedRouterOptions<sup>10+</sup>

Describes the named route options.

| Name  | Type  | Read-Only| Optional| Description                                                        |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| name   | string | No  | No  | Name of the target named route page, which must be a registered named route name. <br/>**Atomic service API:** This API can be used in atomic services since API version 11. <br/>**Model restriction:** This API can be used only in the stage model.<br/>**System capability:** SystemCapability.ArkUI.ArkUI.Full|
| params | Object | No | Yes | Data that needs to be passed to the target page during redirection. The received data becomes invalid when the page is switched to another page. After navigating to the target page, use **router.getParams()** to obtain the passed parameters. In addition, in the web-like paradigm, parameters can also be used directly on the page, for example, **this.keyValue** (where **keyValue** is the value of a key in the **params** parameter during navigation). If the target page already has this parameter, its value will be overwritten by the passed parameter value. <br/>**NOTE**<br/>The **params** parameter can only pass serializable parameters. It cannot pass methods or objects returned by system APIs (for example, the **PixelMap** object defined and returned by media APIs). Passing non-serializable parameters may cause parameter transfer failure or application running exceptions. You are advised to extract the basic-type attributes that need to be passed from objects returned by system APIs, and construct an object-type object for passing.<br/>**Atomic service API:** This API can be used in atomic services since API version 11.<br/>**Model restriction:** This API can be used only in the stage model.<br/>**System capability:** SystemCapability.ArkUI.ArkUI.Full |
| recoverable<sup>14+</sup> | boolean | No  | Yes  | Whether the corresponding page is recoverable.<br>Default value: **true**. <br>**true**: The corresponding page is recoverable.<br>**false**: The corresponding page is not recoverable.<br>**NOTE**<br> If an application is switched to the background and is later closed by the system due to resource constraints or other reasons, a page marked as recoverable can be restored by the system when the application is brought back to the foreground. For more details, see [UIAbility Backup and Restore](../../application-models/ability-recover-guideline.md).<br>**System capability**: SystemCapability.ArkUI.ArkUI.Lite|

## Examples

### JavaScript-based Web-like Development Paradigm

The following sample code applies only to JavaScript files, not ArkTS files.

<!--deprecated_code_no_check-->
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
<!--deprecated_code_no_check-->
<!--code_no_check-->

```js
// detail page
export default {
  onInit() {
    console.info('showData1:' + router.getParams()['data1']);
  }
}
```

### TypeScript-based Declarative Development Paradigm

> **NOTE**
> 
> Directly using **router** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain a [UIContext](arkts-apis-uicontext-uicontext.md) instance using **getUIContext**, and then obtain the associated **router** object using [getRouter](arkts-apis-uicontext-uicontext.md#getrouter).

```ts
// Navigate to the target page through router.pushUrl with the params parameter carried.
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Define the class for passing parameters.
class InnerParams {
  array: number[];

  constructor(tuple: number[]) {
    this.array = tuple;
  }
}

class RouterParams {
  text: string;
  data: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.text = str;
    this.data = new InnerParams(tuple);
  }
}

@Entry
@Component
struct Index {
  async routePage() {
    let options: router.RouterOptions = {
      url: 'pages/second',
      params: new RouterParams('This is the value on the first page', [12, 45, 78])
    };
    // You are advised to use this.getUIContext().getRouter().pushUrl().
    this.getUIContext().getRouter().pushUrl(options)
      .then(() => {
        console.info(`pushUrl finish`);
      })
      .catch((err: BusinessError) => {
        console.error(`pushUrl failed. Code: ${err.code}, message: ${err.message}`);
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

class InnerParams {
  array: number[];

  constructor(tuple: number[]) {
    this.array = tuple;
  }
}

class RouterParams {
  text: string;
  data: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.text = str;
    this.data = new InnerParams(tuple);
  }
}

@Entry
@Component
struct Second {
  private content: string = 'This is the second page.';
  // You are advised to use this.getUIContext().getRouter().getParams().
  @State text: string = (this.getUIContext().getRouter().getParams() as RouterParams).text;
  @State data: InnerParams = (this.getUIContext().getRouter().getParams() as RouterParams).data;
  @State secondData: string = '';

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text(`${this.content}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      Text(this.text)
        .fontSize(30)
        .onClick(() => {
          this.secondData = (this.data.array[1]).toString();
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

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [pushUrl(options: router.RouterOptions)](arkts-apis-uicontext-router.md#pushurl) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                             | Mandatory  | Description       |
| ------- | ------------------------------- | ---- | --------- |
| options | [RouterOptions](#routeroptions) | Yes   | Page routing parameters.|


**Example**

```ts
import { router } from '@kit.ArkUI';

class InnerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new InnerParams(tuple);
  }
}

router.push({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
});
```

## router.replace<sup>(deprecated)</sup>

replace(options: RouterOptions): void

Replaces the current page with a page within the application and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../ui/arkts-navigation-architecture.md) component.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [replaceUrl(options: router.RouterOptions)](arkts-apis-uicontext-router.md#replaceurl) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Parameters**

| Name | Type                           | Mandatory| Description              |
| ------- | ------------------------------- | ---- | ------------------ |
| options | [RouterOptions](#routeroptions) | Yes  | Description of the new page.|

**Example**

```ts
import { router } from '@kit.ArkUI';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replace({
  url: 'pages/detail',
  params: new RouterParams('message')
});
```

## router.enableAlertBeforeBackPage<sup>(deprecated)</sup>

enableAlertBeforeBackPage(options: EnableAlertOptions): void

Enables the display of a confirm dialog box before returning to the previous page. After this API is called, a confirm dialog box will be displayed when [back](#routerbackdeprecated) is executed to return to a page. The page return operation is performed only after the user confirms; if the user cancels, the return is not performed. This is applicable to scenarios where you need to prevent data loss caused by accidental return operations, for example, when the user is filling in a form, editing a document, or making a payment, a confirm dialog box is displayed to avoid accidental exit.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [showAlertBeforeBackPage](arkts-apis-uicontext-router.md#showalertbeforebackpage) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description       |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [EnableAlertOptions](#enablealertoptions) | Yes   | Description of the dialog box.|

**Example**

```ts
import { router } from '@kit.ArkUI';

router.enableAlertBeforeBackPage({
  message: 'Message Info'
});
```

## router.disableAlertBeforeBackPage<sup>(deprecated)</sup>

disableAlertBeforeBackPage(): void

Disables the display of a confirm dialog box before returning to the previous page. After this API is called, the return confirm dialog box enabled by [enableAlertBeforeBackPage](#routerenablealertbeforebackpagedeprecated) will be closed, and the [back](#routerbackdeprecated) operation will no longer display a confirm dialog box but will directly perform the page return.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [hideAlertBeforeBackPage](arkts-apis-uicontext-router.md#hidealertbeforebackpage) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { router } from '@kit.ArkUI';

router.disableAlertBeforeBackPage();
```

## Example

This example shows the redirection features of the router.[replace](#routerreplacedeprecated) and router.[replaceUrl](#routerreplaceurldeprecated) APIs in the web-like paradigm.

The following describes the tree structure:
```text
pages
├─ index
│  ├─ index.css
│  ├─ index.hml
│  └─ index.js
└─ routerPages
   ├─ routerPage.css
   ├─ routerPage.hml
   └─ routerPage.js
```

<!--code_no_check-->
```css
/* index.css */
.page {
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  background-color: #050816;
}

.page-name {
  width: 78%;
  margin-top: 10px;
  font-size: 14px;
  text-align: center;
  color: #f8fafc;
}

.tips {
  width: 82%;
  margin-top: 12px;
  font-size: 12px;
  text-align: center;
  color: #cbd5e1;
}

.status {
  width: 82%;
  margin-top: 8px;
  font-size: 12px;
  text-align: center;
  color: #94a3b8;
}

.action-button {
  width: 190px;
  height: 42px;
  border-radius: 21px;
  color: #ffffff;
  font-size: 14px;
  text-align: center;
}

.action-button-primary {
  margin-top: 22px;
  background-color: #2563eb;
}

.action-button-secondary {
  margin-top: 10px;
  background-color: #16a34a;
}
```

<!--code_no_check-->
```html
<!--index.hml-->
<div class="page">
    <text class="page-name">{{ pageName }}</text>
    <text class="tips">{{ tips }}</text>
    <text class="status">{{ statusText }}</text>
    <input class="action-button action-button-primary" type="button" value="replace to routerPage" onclick="replaceToRouterPage"></input>
    <input class="action-button action-button-secondary" type="button" value="replaceUrl to routerPage" onclick="replaceUrlToRouterPage"></input>
</div>
```

<!--deprecated_code_no_check-->
<!--code_no_check-->
```js
// index.js
import { router } from '@kit.ArkUI';

export default {
    data: {
        pageName: 'Index Page',
        tips: 'Use replace or replaceUrl to open routerPage.',
        statusText: 'Current page: index'
    },
    replaceToRouterPage: function() {
        router.replace({
            url: 'pages/routerPages/routerPage',
            params: {
                statusText: 'Opened by router.replace.'
            }
        });
    },
    replaceUrlToRouterPage: function() {
        router.replaceUrl({
            url: 'pages/routerPages/routerPage',
            params: {
                statusText: 'Opened by router.replaceUrl.'
            }
        });
    }
}
```

<!--code_no_check-->
```css
/* routerPage.css */
.page {
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  background-color: #050816;
}

.page-name {
  width: 78%;
  margin-top: 10px;
  font-size: 14px;
  text-align: center;
  color: #f8fafc;
}

.tips {
  width: 82%;
  margin-top: 12px;
  font-size: 12px;
  text-align: center;
  color: #cbd5e1;
}

.status {
  width: 82%;
  margin-top: 8px;
  font-size: 12px;
  text-align: center;
  color: #94a3b8;
}

.action-button {
  width: 190px;
  height: 42px;
  border-radius: 21px;
  color: #ffffff;
  font-size: 14px;
  text-align: center;
}

.action-button-primary {
  margin-top: 22px;
  background-color: #2563eb;
}

.action-button-secondary {
  margin-top: 10px;
  background-color: #16a34a;
}
```

<!--code_no_check-->
```html
<!--routerPage.hml-->
<div class="page">
    <text class="page-name">{{ pageName }}</text>
    <text class="tips">{{ tips }}</text>
    <text class="status">{{ statusText }}</text>
    <input class="action-button action-button-primary" type="button" value="replace to index" onclick="replaceToIndex"></input>
    <input class="action-button action-button-secondary" type="button" value="replaceUrl to index" onclick="replaceUrlToIndex"></input>
</div>
```

<!--deprecated_code_no_check-->
<!--code_no_check-->
```js
// routerPage.js
import { router } from '@kit.ArkUI';

export default {
    data: {
        pageName: 'Router Page',
        tips: 'Use replace or replaceUrl to return to index.',
        statusText: 'Current page: routerPage'
    },
    replaceToIndex: function() {
        router.replace({
            url: 'pages/index/index',
            params: {
                statusText: 'Returned by router.replace.'
            }
        });
    },
    replaceUrlToIndex: function() {
        router.replaceUrl({
            url: 'pages/index/index',
            params: {
                statusText: 'Returned by router.replaceUrl.'
            }
        });
    }
}
```

![ohos_router_web_like.gif](figures/ohosRouterWebLikeDemo.gif)
