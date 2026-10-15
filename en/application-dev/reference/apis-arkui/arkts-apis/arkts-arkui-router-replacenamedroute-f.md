# replaceNamedRoute

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

<a id="replacenamedroute1"></a>

## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void
```

Replaces the current page with the specified named route page and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../../ui/arkts-navigation-architecture.md) component.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [replaceNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute1)(options: router.NamedRouterOptions, callback: AsyncCallback&lt;void&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void--><!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | Yes | Description of the new page. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the page replacement result.<br>When the page replacement is successful, the value of **error** is **undefined**. When the page replacement fails, the value of **error** is the error object returned by the system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Named route error. The named route does not exist. |

**Examples**

```TypeScript
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


<a id="replacenamedroute2"></a>

## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions): Promise<void>
```

Replaces the current page with the specified named route page and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../../ui/arkts-navigation-architecture.md) component.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [replaceNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute2)(options: router.NamedRouterOptions)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-router-function replaceNamedRoute(options: NamedRouterOptions): Promise<void>--><!--Device-router-function replaceNamedRoute(options: NamedRouterOptions): Promise<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | Yes | Description of the new page. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Named route error. The named route does not exist. |

**Examples**

```TypeScript
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


<a id="replacenamedroute3"></a>

## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void
```

Replaces the current page with the specified named route page and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../../ui/arkts-navigation-architecture.md) component.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [replaceNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute3)(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void--><!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | Yes | Description of the new page. |
| mode | [RouterMode](arkts-arkui-router-routermode-e.md) | Yes | Mode used for replacing the page. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the page replacement result.<br>When the page replacement is successful, the value of **error** is **undefined**. When the page replacement fails, the value of **error** is the error object returned by the system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Named route error. The named route does not exist. |

**Examples**

```TypeScript
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


<a id="replacenamedroute4"></a>

## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>
```

Replaces the current page with the specified named route page and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../../ui/arkts-navigation-architecture.md) component.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [replaceNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute4)(options: router.NamedRouterOptions, mode: router.RouterMode)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>--><!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | Yes | Description of the new page. |
| mode | [RouterMode](arkts-arkui-router-routermode-e.md) | Yes | Mode for page replacement. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Failed to get the delegate. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Named route error. The named route does not exist. |

**Examples**

```TypeScript
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
