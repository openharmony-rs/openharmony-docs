# Router

提供通过不同的url访问不同的页面，包括跳转到应用内的指定页面、同应用内的某个页面替换当前页面、返回上一页面或指定的页面等。Router还支持命名路由跳转、页面栈管理、参数传递、返回确认对话框等能力，适用于需要统一管理页面导航流程、处理页面间数据传递的场景，与UIContext集成使用可实现灵活的路由控制。

Router基于页面栈机制管理页面导航，页面栈支持的最大容量为32个页面。当调用pushUrl时，目标页面会被压入栈顶；调用replaceUrl时，当前页面会被弹出栈并销毁，目标页面压入栈顶；调用back时，栈顶页面会被弹出。

> **说明：** 
> 
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> - 本Class首批接口从API version 10开始支持。
> 
> - 本模块接口仅可在Stage模型下使用。
> 
> - 以下API需先使用UIContext中的[getRouter()](arkts-arkui-arkui-uicontext-uicontext-c.md#getrouter)方法获取到Router对象，再通过该对象调用对应方法。
> 
> - Router提供了以下两种路由方式：
> 
> - **普通路由**（[pushUrl](#pushurl)/[replaceUrl](#replaceurl)）：通过url路径标识目标页面，适用于简单的页面跳转场景。
> 
> - **命名路由**（[pushNamedRoute](#pushnamedroute)/[replaceNamedRoute](#replacenamedroute)）：通过name标识目标页面，在跳转之前需要将目标跳转页面通过import将页面进行加载，适用于跨包跳转场景。
> 
> 建议在页面路径可能变化或需要统一管理路由的场景下使用命名路由，其他场景使用普通路由。根据是否需要返回上一页来选择使用哪个方法。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## back

```TypeScript
back(options?: router.RouterOptions): void
```

返回上一页面或指定的页面。

> **说明：** 
> 
> 如果之前调用了showAlertBeforeBackPage()开启了返回询问对话框，则调用back()时会弹出确认对话框：用户选择"取消"则back()不执行，选择"确认"则继续执行；
> 可通过hideAlertBeforeBackPage()关闭返回询问对话框。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 否 | 返回页面描述信息。当需要返回到指定的页面时传入此参数（通过url指定目标页面）；当只需返回上一页时可以不传入此参数。url指定返回的目标页面：若页面栈中存在该url，则返回至index最大的同名页面；若不存在则不响应操作。若url未设置，则返回上一页（页面不会重新构建，出栈后会被回收）。 |

## back

```TypeScript
back(index: number, params?: Object): void
```

返回指定的页面。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 返回目标页面的索引值，从0开始计数（注意：与[getStateByIndex](#getstatebyindex)的index参数不同，后者从1开始计数）。<br>取值范围：[0, +∞)。如果index超出页面栈范围或不存在对应页面，则不响应用户操作。 |
| params | Object | 否 | 页面返回时携带的参数。不传入时不携带参数。 |

## clear

```TypeScript
clear(): void
```

清空页面栈中的所有历史页面，仅保留当前页面作为栈顶页面。

> **说明：** 
> 
> 调用 clear()方法会清空全部历史页面栈，最终仅保留当前页面，页面栈深度变为1。此时栈内无历史记录，back()回退接口将失效；
> 但pushUrl()、replaceUrl()等跳转方法仍可正常使用，支持新增页面或替换当前页面。
> 该操作具备不可逆特性，执行完成后用户无法回访任何历史页面，建议仅在退出登录、切换账号等业务场景下使用，调用前务必持久化存储关键页面状态数据。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getLength

```TypeScript
getLength(): string
```

获取当前在页面栈内的页面数量。

> **说明：** 
> 
> 从API version 10开始支持，从 API version 23开始废弃，建议使用[getStackSize](#getstacksize)替代。

**起始版本：** 10

**废弃版本：** 23

**替代接口：** [getStackSize](#getstacksize)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 页面数量，页面栈支持最大数值是32。 |

## getParams

```TypeScript
getParams(): Object
```

获取发起跳转的页面往当前页传入的参数。参数在页面跳转时通过RouterOptions或NamedRouterOptions的params字段传递。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 发起跳转的页面往当前页传入的参数。 |

## getStackSize

```TypeScript
getStackSize(): number
```

获取当前页面栈内的页面数量。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 页面数量，页面栈支持最大数值是32。 |

## getState

```TypeScript
getState(): router.RouterState
```

获取当前页面的状态信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [router.RouterState](arkts-arkui-router-routerstate-i.md) | 页面状态信息。 |

## getStateByIndex

```TypeScript
getStateByIndex(index: number): router.RouterState | undefined
```

通过索引值获取对应页面的状态信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 表示要获取的页面索引，从1开始计数（注意：与[back](#back)的index参数不同，后者从0开始计数）。<br>取值范围：[1, +∞)。索引不存在时返回undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [router.RouterState](arkts-arkui-router-routerstate-i.md) &#124; undefined | 返回页面状态信息。索引不存在时返回undefined。 |

## getStateByUrl

```TypeScript
getStateByUrl(url: string): Array<router.RouterState>
```

通过url获取匹配指定url的页面的状态信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 表示要获取对应页面信息的url，需使用应用内页面路径格式。如果页面栈中没有对应url的页面，返回空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[router.RouterState](arkts-arkui-router-routerstate-i.md)&gt; | 页面状态信息。 |

## hideAlertBeforeBackPage

```TypeScript
hideAlertBeforeBackPage(): void
```

禁用页面返回询问对话框。适用于用户已完成保存操作可以安全返回、页面状态切换后不再需要返回确认、需要动态控制返回行为等场景。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pushNamedRoute

```TypeScript
pushNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback<void>): void
```

跳转到指定的命名路由页面。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 跳转页面描述信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 页面跳转结果回调函数。<br>当页面跳转成功时，error为undefined。当页面跳转失败时，error为系统返回的错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100003](../errorcode-router.md#100003-路由压入的page过多) | Page stack error. Too many pages are pushed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

## pushNamedRoute

```TypeScript
pushNamedRoute(options: router.NamedRouterOptions): Promise<void>
```

跳转到指定的命名路由页面，使用Promise异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 跳转页面描述信息，包含name（命名路由名称）和params（传递的参数）等字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100003](../errorcode-router.md#100003-路由压入的page过多) | Page stack error. Too many pages are pushed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

## pushNamedRoute

```TypeScript
pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback<void>): void
```

跳转到指定的命名路由页面。使用callback异步回调。与[pushNamedRoute](#pushnamedroute-1)相比，新增了mode参数，即支持设置跳转页面使用的模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 跳转页面描述信息。 |
| mode | [router.RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 跳转页面使用的模式，可选Standard（标准模式）或Single（单例模式）。建议根据页面栈管理需求选择：Standard模式适用于常规页面跳转；Single模式可避免相同页面重复入栈，适合登录页、主页等单例场景。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 页面跳转结果回调函数。<br>当页面跳转成功时，error为undefined。当页面跳转失败时，error为系统返回的错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100003](../errorcode-router.md#100003-路由压入的page过多) | Page stack error. Too many pages are pushed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

## pushNamedRoute

```TypeScript
pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise<void>
```

跳转到指定的命名路由页面，使用Promise异步回调。与[pushNamedRoute](#pushnamedroute)相比，新增了mode参数，即支持设置跳转页面使用的模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 跳转页面描述信息。 |
| mode | [router.RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 跳转页面使用的模式，可选Standard（标准模式）或Single（单例模式）。建议根据页面栈管理需求选择：Standard模式适用于常规页面跳转；Single模式可避免相同页面重复入栈，适合登录页、主页等单例场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100003](../errorcode-router.md#100003-路由压入的page过多) | Page stack error. Too many pages are pushed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

## pushUrl

```TypeScript
pushUrl(options: router.RouterOptions, callback: AsyncCallback<void>): void
```

跳转到应用内的指定页面。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 跳转页面描述信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 页面跳转结果回调函数。<br>当页面跳转成功时，error为undefined。当页面跳转失败时，error为系统返回的错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100002](../errorcode-router.md#100002-路由页面跳转时输入的uri错误) | Uri error. The URI of the page to redirect is incorrect or does not exist |
| [100003](../errorcode-router.md#100003-路由压入的page过多) | Page stack error. Too many pages are pushed. |

## pushUrl

```TypeScript
pushUrl(options: router.RouterOptions): Promise<void>
```

跳转到应用内的指定页面，使用Promise异步回调。

> **说明：** 
> 
> pushUrl()会在页面栈顶部添加新页面，页面栈深度+1（上限32页，超限报错误码100003），后续可调用back()返回到上一页面或调用replaceUrl()替换当前页面。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 跳转页面描述信息，包含url（目标页面路径）和params（传递的参数）等字段。**说明：** 页面栈最大支持32个页面，建议跳转前通过[getStackSize](#getstacksize)（从API version 23开始支持）检查当前栈大小，避免超出限制导致跳转失败（错误码100003）。API version 23之前可使用[getLength](#getlength)检查。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100002](../errorcode-router.md#100002-路由页面跳转时输入的uri错误) | Uri error. The URI of the page to redirect is incorrect or does not exist |
| [100003](../errorcode-router.md#100003-路由压入的page过多) | Page stack error. Too many pages are pushed. |

## pushUrl

```TypeScript
pushUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback<void>): void
```

跳转到应用内的指定页面。使用callback异步回调。与[pushUrl](#pushurl-1)相比，新增了mode参数，即支持设置跳转页面使用的模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 跳转页面描述信息。 |
| mode | [router.RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 跳转页面使用的模式，可选Standard（标准模式）或Single（单例模式）。建议根据页面栈管理需求选择：Standard模式适用于常规页面跳转；Single模式可避免相同页面重复入栈，适合登录页、主页等单例场景。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 页面跳转结果回调函数。<br>当页面跳转成功时，error为undefined。当页面跳转失败时，error为系统返回的错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100002](../errorcode-router.md#100002-路由页面跳转时输入的uri错误) | Uri error. The URI of the page to redirect is incorrect or does not exist |
| [100003](../errorcode-router.md#100003-路由压入的page过多) | Page stack error. Too many pages are pushed. |

## pushUrl

```TypeScript
pushUrl(options: router.RouterOptions, mode: router.RouterMode): Promise<void>
```

跳转到应用内的指定页面，使用Promise异步回调。与[pushUrl](#pushurl)相比，新增了mode参数，即支持设置跳转页面使用的模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 跳转页面描述信息。 |
| mode | [router.RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 跳转页面使用的模式，可选Standard（标准模式）或Single（单例模式）。建议根据页面栈管理需求选择：Standard模式适用于常规页面跳转；Single模式可避免相同页面重复入栈，适合登录页、主页等单例场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100002](../errorcode-router.md#100002-路由页面跳转时输入的uri错误) | Uri error. The URI of the page to redirect is incorrect or does not exist |
| [100003](../errorcode-router.md#100003-路由压入的page过多) | Page stack error. Too many pages are pushed. |

## replaceNamedRoute

```TypeScript
replaceNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback<void>): void
```

用指定的命名路由页面替换当前页面，并销毁被替换的页面。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 替换页面描述信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 页面替换结果回调函数。<br>当页面替换成功时，error为undefined。当页面替换失败时，error为系统返回的错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

## replaceNamedRoute

```TypeScript
replaceNamedRoute(options: router.NamedRouterOptions): Promise<void>
```

用指定的命名路由页面替换当前页面，并销毁被替换的页面，使用Promise异步回调。适用于大型应用中使用命名路由管理页面、路由路径可能变化时避免硬编码URL、模块化开发中各模块独立管理自己的命名路由等场景。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 替换页面描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | if the number of parameters is less than 1 or the type of the url parameter is not string. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

## replaceNamedRoute

```TypeScript
replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback<void>): void
```

用指定的命名路由页面替换当前页面，并销毁被替换的页面。使用callback异步回调。与[replaceNamedRoute](#replacenamedroute-1)相比，新增了mode参数，即支持设置替换页面使用的模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 替换页面描述信息。 |
| mode | [router.RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 替换页面使用的模式，可选Standard（标准模式）或Single（单例模式）。建议根据页面栈管理需求选择：Standard模式适用于常规页面跳转；Single模式可避免相同页面重复入栈，适合登录页、主页等单例场景。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 页面替换结果回调函数。<br>当页面替换成功时，error为undefined。当页面替换失败时，error为系统返回的错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | if the number of parameters is less than 1 or the type of the url parameter is not string. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

## replaceNamedRoute

```TypeScript
replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise<void>
```

用指定的命名路由页面替换当前页面，并销毁被替换的页面，使用Promise异步回调。与[replaceNamedRoute](#replacenamedroute-1)相比，新增了mode参数，即支持设置跳转页面使用的模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 是 | 替换页面描述信息。 |
| mode | [router.RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 跳转页面使用的模式，可选Standard（标准模式）或Single（单例模式）。建议根据页面栈管理需求选择：Standard模式适用于常规页面跳转；Single模式可避免相同页面重复入栈，适合登录页、主页等单例场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Failed to get the delegate. This error code is thrown only in the standard system. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Named route error. The named route does not exist. |

## replaceUrl

```TypeScript
replaceUrl(options: router.RouterOptions, callback: AsyncCallback<void>): void
```

用应用内的某个页面替换当前页面，并销毁被替换的页面。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 替换页面描述信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 页面替换结果回调函数。<br>当页面替换成功时，error为undefined。当页面替换失败时，error为系统返回的错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [200002](../errorcode-router.md#200002-路由页面替换时输入的uri错误) | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

## replaceUrl

```TypeScript
replaceUrl(options: router.RouterOptions): Promise<void>
```

用应用内的某个页面替换当前页面，并销毁被替换的页面，使用Promise异步回调。

> **说明：** 
> 
> replaceUrl()会替换页面栈栈顶页面，页面栈深度维持不变。与pushUrl()的核心差异：pushUrl()入栈新页面、栈深度 + 1，replaceUrl()不改变栈深度。
> 被替换的页面会直接销毁，无法通过back()回退访问。适用场景：登录成功跳转首页（避免回退至登录页）、页面重定向、临时中转页面跳转等。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 替换页面描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [200002](../errorcode-router.md#200002-路由页面替换时输入的uri错误) | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

## replaceUrl

```TypeScript
replaceUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback<void>): void
```

用应用内的某个页面替换当前页面，并销毁被替换的页面。使用callback异步回调。与[replaceUrl](#replaceurl-1)相比，新增了mode参数，即支持设置替换页面使用的模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 替换页面描述信息。 |
| mode | [router.RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 替换页面使用的模式，可选Standard（标准模式）或Single（单例模式）。建议根据页面栈管理需求选择：Standard模式适用于常规页面跳转；Single模式可避免相同页面重复入栈，适合登录页、主页等单例场景。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 页面替换结果回调函数。<br>当页面替换成功时，error为undefined。当页面替换失败时，error为系统返回的错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The UI execution context is not found. This error code is thrown only in the standard system. |
| [200002](../errorcode-router.md#200002-路由页面替换时输入的uri错误) | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

## replaceUrl

```TypeScript
replaceUrl(options: router.RouterOptions, mode: router.RouterMode): Promise<void>
```

用应用内的某个页面替换当前页面，并销毁被替换的页面，使用Promise异步回调。与[replaceUrl](#replaceurl)相比，新增了mode参数，即支持设置替换页面使用的模式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 替换页面描述信息。 |
| mode | [router.RouterMode](arkts-arkui-router-routermode-e.md) | 是 | 替换页面使用的模式，可选Standard（标准模式）或Single（单例模式）。建议根据页面栈管理需求选择：Standard模式适用于常规页面跳转；Single模式可避免相同页面重复入栈，适合登录页、主页等单例场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Failed to get the delegate. This error code is thrown only in the standard system. |
| [200002](../errorcode-router.md#200002-路由页面替换时输入的uri错误) | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

## showAlertBeforeBackPage

```TypeScript
showAlertBeforeBackPage(options: router.EnableAlertOptions): void
```

开启页面返回询问对话框。调用此方法后，当用户触发返回操作（如点击返回键、调用back方法）时，系统会先弹出确认对话框询问用户是否返回；用户确认后才会执行返回操作，取消则留在当前页面。适用于表单填写页面（防止用户误触返回导致内容丢失）、重要操作确认页面（如支付、提交订单等）、内容编辑页面（用户可能有未保存的修改时）等场景。与hideAlertBeforeBackPage()方法成对使用：调用本方法开启对话框后，建议在适当时机调用hideAlertBeforeBackPage()关闭对话框。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [router.EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md) | 是 | 文本弹窗信息描述，包含message（弹窗提示内容）等参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
