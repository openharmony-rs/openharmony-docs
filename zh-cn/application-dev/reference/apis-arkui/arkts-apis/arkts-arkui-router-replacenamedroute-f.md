# replaceNamedRoute

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

<a id="replacenamedroute"></a>
## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void
```

用指定的命名路由页面替换当前页面，并销毁被替换的页面。

> **说明：**  
>  
> - 从API version 10开始支持，从API version 18开始废弃，建议使用  
> [replaceNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute-1)  
> 替代。replaceNamedRoute需先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** [replaceNamedRoute(options:](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void--><!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 替换页面描述信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异常响应回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

**示例：**

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


<a id="replacenamedroute-1"></a>
## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions): Promise<void>
```

用指定的命名路由页面替换当前页面，并销毁被替换的页面。

> **说明：**  
>  
> - 从API version 10开始支持，从API version 18开始废弃，建议使用  
> [replaceNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute-1)替代。  
> replaceNamedRoute需先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** [replaceNamedRoute(options:](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function replaceNamedRoute(options: NamedRouterOptions): Promise<void>--><!--Device-router-function replaceNamedRoute(options: NamedRouterOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 替换页面描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

**示例：**

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


<a id="replacenamedroute-2"></a>
## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void
```

用指定的命名路由页面替换当前页面，并销毁被替换的页面。

> **说明：**  
>  
> - 从API version 10开始支持，从API version 18开始废弃，建议使用  
> [replaceNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute-1)  
> 替代。replaceNamedRoute需先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** [replaceNamedRoute(options:](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void--><!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 替换页面描述信息。 |
| mode | [RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 跳转页面使用的模式。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异常响应回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

**示例：**

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


<a id="replacenamedroute-3"></a>
## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>
```

用指定的命名路由页面替换当前页面，并销毁被替换的页面。

> **说明：**  
>  
> - 从API version 10开始支持，从API version 18开始废弃，建议使用  
> [replaceNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute-1)  
> 替代。replaceNamedRoute需先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** [replaceNamedRoute(options:](arkts-arkui-arkui-uicontext-router-c.md#replacenamedroute-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>--><!--Device-router-function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 替换页面描述信息。 |
| mode | [RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 跳转页面使用的模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Failed to get the delegate. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

**示例：**

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

