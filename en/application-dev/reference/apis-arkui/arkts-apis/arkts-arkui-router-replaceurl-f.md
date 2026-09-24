# replaceUrl

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## replaceUrl

```TypeScript
function replaceUrl(options: RouterOptions, callback: AsyncCallback<void>): void
```

Replaces the current page with another one in the application and destroys the current page.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [replaceUrl](arkts-arkui-arkui-uicontext-router-c.md#replaceurl)(options: router.RouterOptions, callback: AsyncCallback&lt;void&gt;)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | Yes | Description of the new page. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [200002](../errorcode-router.md#200002-incorrect-uri-during-page-replacement) | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

**Examples**

```TypeScript
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


<a id="replaceurl-1"></a>

## replaceUrl

```TypeScript
function replaceUrl(options: RouterOptions): Promise<void>
```

Replaces the current page with another one in the application and destroys the current page. This API cannot be used to configure page transition effects. To configure page transition effects, use the [Navigation](../../../ui/arkts-navigation-architecture.md) component.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [replaceUrl](arkts-arkui-arkui-uicontext-router-c.md#replaceurl-1)(options: router.RouterOptions)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | Yes | Description of the new page. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [200002](../errorcode-router.md#200002-incorrect-uri-during-page-replacement) | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

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


<a id="replaceurl-2"></a>

## replaceUrl

```TypeScript
function replaceUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void
```

Replaces the current page with another one in the application and destroys the current page.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [replaceUrl](arkts-arkui-arkui-uicontext-router-c.md#replaceurl-2)(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | Yes | Description of the new page. |
| mode | [RouterMode](arkts-arkui-router-routermode-e.md) | Yes | Routing mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [200002](../errorcode-router.md#200002-incorrect-uri-during-page-replacement) | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

**Examples**

```TypeScript
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


<a id="replaceurl-3"></a>

## replaceUrl

```TypeScript
function replaceUrl(options: RouterOptions, mode: RouterMode): Promise<void>
```

Replaces the current page with another one in the application and destroys the current page.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [replaceUrl](arkts-arkui-arkui-uicontext-router-c.md#replaceurl-3)(options: router.RouterOptions, mode: router.RouterMode)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | Yes | Description of the new page. |
| mode | [RouterMode](arkts-arkui-router-routermode-e.md) | Yes | Routing mode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Failed to get the delegate. This error code is thrown only in the standard system. |
| [200002](../errorcode-router.md#200002-incorrect-uri-during-page-replacement) | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

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
