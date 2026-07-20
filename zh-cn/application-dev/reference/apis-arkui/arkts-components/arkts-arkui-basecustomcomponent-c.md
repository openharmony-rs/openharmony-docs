# BaseCustomComponent

自定义组件基类，它是从类CustomComponent迁移过来的。

**继承/实现关系：** BaseCustomComponent extends [CommonAttribute](arkts-arkui-common-attribute.md)

**起始版本：** 18

<!--Device-unnamed-declare class BaseCustomComponent extends CommonAttribute--><!--Device-unnamed-declare class BaseCustomComponent extends CommonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="abouttoappear"></a>
## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

aboutToAppear方法

aboutToAppear函数在创建自定义组件的新实例之后，在执行其构建（）函数之前执行。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-BaseCustomComponent-aboutToAppear?(): void--><!--Device-BaseCustomComponent-aboutToAppear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="abouttodisappear"></a>
## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

aboutToDisappear 方法

在自定义组件被销毁之前，aboutToDisappear 函数会执行。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-BaseCustomComponent-aboutToDisappear?(): void--><!--Device-BaseCustomComponent-aboutToDisappear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="abouttorecycle"></a>
## aboutToRecycle

```TypeScript
aboutToRecycle?(): void
```

aboutToRecycle Method and it is migrated from class CustomComponent.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-aboutToRecycle?(): void--><!--Device-BaseCustomComponent-aboutToRecycle?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="build"></a>
## build

```TypeScript
build(): void
```

Customize the pop-up content constructor and it is migrated from class CustomComponent.

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-BaseCustomComponent-build(): void--><!--Device-BaseCustomComponent-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="getdialogcontroller"></a>
## getDialogController

```TypeScript
getDialogController(): PromptActionDialogController | undefined
```

The dialog controller of the custom component.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-getDialogController(): PromptActionDialogController | undefined--><!--Device-BaseCustomComponent-getDialogController(): PromptActionDialogController | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PromptActionDialogController](arkts-arkui-promptactiondialogcontroller-t.md) | The controller of dialog, or undefined if it is not available |

<a id="getuicontext"></a>
## getUIContext

```TypeScript
getUIContext(): UIContext
```

Get current UIContext and it is migrated from class CustomComponent.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-getUIContext(): UIContext--><!--Device-BaseCustomComponent-getUIContext(): UIContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIContext](arkts-arkui-uicontext-t.md) | The UIContext that the custom component belongs to. |

<a id="getuniqueid"></a>
## getUniqueId

```TypeScript
getUniqueId(): number
```

Get uniqueId of the custom component and it is migrated from class CustomComponent.This unique ID is assigned by the system to each component.If this API is called before the component's corresponding node is created or after it has been destroyed, an invalid unique ID, which is -1, will be returned.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-getUniqueId(): number--><!--Device-BaseCustomComponent-getUniqueId(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - The uniqueId of the custom component. |

<a id="onbackpress"></a>
## onBackPress

```TypeScript
onBackPress?(): void | boolean
```

在router路由页面（即[\@Entry](docroot://ui/state-management/arkts-create-custom-components.md#entry)装饰的自定义组件）生效，当用户点击返回按钮时触发。返回true表示页面自己处理返回逻辑，不进行页面路由；返回false表示使用默认的路由返回逻辑，不设置返回值按照false处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-onBackPress?(): void | boolean--><!--Device-BaseCustomComponent-onBackPress?(): void | boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="ondidbuild"></a>
## onDidBuild

```TypeScript
onDidBuild?(): void
```

The callback method after the custom component is built and it is migrated from class CustomComponent.

Triggered when the custom component has been built.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-onDidBuild?(): void--><!--Device-BaseCustomComponent-onDidBuild?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="onformrecover"></a>
## onFormRecover

```TypeScript
onFormRecover?(statusData: string): void
```

onFormRecover Method, this is only for ArkTS form, it is migrated from class CustomComponent.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-BaseCustomComponent-onFormRecover?(statusData: string): void--><!--Device-BaseCustomComponent-onFormRecover?(statusData: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| statusData | string | 是 | indicate status data of ArkTS form UI, which is acquired by calling onFormRecycle, it is used to recover form |

<a id="onformrecycle"></a>
## onFormRecycle

```TypeScript
onFormRecycle?(): string
```

onFormRecycle Method, this is only for ArkTS form, if form was marked recyclable by form user, when system memory is low,it will be recycled after calling this method, you should return a string of params that you wish to be saved, it will be passed back as params in onFormRecover, in which you can recover the form, it is migrated from class CustomComponent.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-BaseCustomComponent-onFormRecycle?(): string--><!--Device-BaseCustomComponent-onFormRecycle?(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | status data of ArkTS form UI, this data will be passed in when recover form later |

<a id="onmeasuresize"></a>
## onMeasureSize

```TypeScript
onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions): SizeResult
```

ArkUI框架会在自定义组件确定尺寸时，将该自定义组件的节点信息和尺寸范围通过onMeasureSize传递给该开发者。不允许在onMeasureSize函数中改变状态变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions): SizeResult--><!--Device-BaseCustomComponent-onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions): SizeResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selfLayoutInfo | [GeometryInfo](arkts-arkui-geometryinfo-i.md) | 是 | 计算自定义组件大小后的自身布局信息。 <br/>**说明：** <br/>第一次布局时以自身设置的属性为准。 |
| children | Array&lt;Measurable&gt; | 是 | 计算子组件大小后的子组件布局信息。<br/>**说明：**<br/>如果没有设置子组件的布局信息，子组件会维持上一次的布局信息，当子组件从来没有设置过尺寸时，尺寸默认为0。 |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | 自定义组件的布局约束信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeResult](arkts-arkui-sizeresult-i.md) | Component size information. |

<a id="onnewparam"></a>
## onNewParam

```TypeScript
onNewParam?(param: ESObject): void
```

该回调仅生效于由[\@Entry](docroot://ui/state-management/arkts-create-custom-components.md#entry)装饰的、作为[router](**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-onNewParam?(param: ESObject): void--><!--Device-BaseCustomComponent-onNewParam?(param: ESObject): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | ESObject | 是 | 路由跳转时传递到目标页面的数据。 |

<a id="onpagehide"></a>
## onPageHide

```TypeScript
onPageHide?(): void
```

router路由页面（即[\@Entry](docroot://ui/state-management/arkts-create-custom-components.md#entry)装饰的自定义组件）每次隐藏时触发一次，包括路由跳转、应用进入后台等场景。  
> **说明：**  
> 在该回调函数内，建议避免执行高耗时操作阻塞主线程造成卡顿。对于高耗时操作例如相机资源释放，推荐使用异步方案替代。最佳实践请参考  
>[优化应用时延问题-延迟执行资源释放操作](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-application-latency-optimization-cases#section8783201923819)。

It is triggered once each time the page is hidden, including scenarios such as the routing process and the application entering the background

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-onPageHide?(): void--><!--Device-BaseCustomComponent-onPageHide?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="onpageshow"></a>
## onPageShow

```TypeScript
onPageShow?(): void
```

router路由页面（即[\@Entry](docroot://ui/state-management/arkts-create-custom-components.md#entry)装饰的自定义组件）每次显示时触发一次，包括路由跳转、应用进入前台等场景。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-onPageShow?(): void--><!--Device-BaseCustomComponent-onPageShow?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="onplacechildren"></a>
## onPlaceChildren

```TypeScript
onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void
```

ArkUI框架会在自定义组件确定位置时，将该自定义组件的子节点自身的尺寸范围通过onPlaceChildren传递给该自定义组件。不允许在onPlaceChildren函数中改变状态变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void--><!--Device-BaseCustomComponent-onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selfLayoutInfo | [GeometryInfo](arkts-arkui-geometryinfo-i.md) | 是 | 计算自定义组件大小后的自身布局信息。 |
| children | Array&lt;Layoutable&gt; | 是 | 计算子组件大小后的子组件布局信息。 |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | 自定义组件的布局约束信息。 |

<a id="onwillapplytheme"></a>
## onWillApplyTheme

```TypeScript
onWillApplyTheme?(theme: Theme): void
```

onWillApplyTheme函数用于获取当前组件上下文的Theme对象，在创建自定义组件的新实例后，在执行其build()函数之前执行。允许在onWillApplyTheme函数中改变状态变量，更改将在后续执行build()函数中生效。

> **说明：**  
> 从API version 18开始，该接口支持在状态管理V2组件中使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-onWillApplyTheme?(theme: Theme): void--><!--Device-BaseCustomComponent-onWillApplyTheme?(theme: Theme): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| theme | [Theme](arkts-arkui-theme-t.md) | 是 | 自定义组件当前生效的Theme对象。 |

<a id="pagetransition"></a>
## pageTransition

```TypeScript
pageTransition?(): void
```

PageTransition Method and it is migrated from class CustomComponent.Implement Animation when enter this page or move to other pages.

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-pageTransition?(): void--><!--Device-BaseCustomComponent-pageTransition?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="querynavdestinationinfo"></a>
## queryNavDestinationInfo

```TypeScript
queryNavDestinationInfo(): NavDestinationInfo | undefined
```

查询自定义组件所属的[NavDestination]{@link nav_destination)信息，仅当自定义组件在NavDestination的内部时才生效。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-queryNavDestinationInfo(): NavDestinationInfo | undefined--><!--Device-BaseCustomComponent-queryNavDestinationInfo(): NavDestinationInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavDestinationInfo](../arkts-apis/arkts-arkui-uiobserver-navdestinationinfo-i.md) | **NavDestinationInfo** instance obtained. |

<a id="querynavdestinationinfo-1"></a>
## queryNavDestinationInfo

```TypeScript
queryNavDestinationInfo(isInner: Optional<boolean>): NavDestinationInfo | undefined
```

查询当前自定义组件距离最近的NavDestination信息（要求该NavDestination是Navigation的导航页或子页），isInner为true表示向内查找，false表示向外查找。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-queryNavDestinationInfo(isInner: Optional<boolean>): NavDestinationInfo | undefined--><!--Device-BaseCustomComponent-queryNavDestinationInfo(isInner: Optional<boolean>): NavDestinationInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isInner | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | -true：向内查询最近的，且在栈内的NavDestinationInfo的详细信息。<br/>false：向外查询最近的，且在栈内的NavDestinationInfo的详细信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavDestinationInfo](../arkts-apis/arkts-arkui-uiobserver-navdestinationinfo-i.md) | **NavDestinationInfo** instance obtained. |

<a id="querynavigationinfo"></a>
## queryNavigationInfo

```TypeScript
queryNavigationInfo(): NavigationInfo | undefined
```

查询自定义组件所属的[Navigation](arkts-arkui-navigation.md)信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-queryNavigationInfo(): NavigationInfo | undefined--><!--Device-BaseCustomComponent-queryNavigationInfo(): NavigationInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationInfo](arkts-arkui-navigationinfo-t.md) | **NavigationInfo** instance obtained. |

<a id="queryrouterpageinfo"></a>
## queryRouterPageInfo

```TypeScript
queryRouterPageInfo(): RouterPageInfo | undefined
```

获取RouterPageInfo实例对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaseCustomComponent-queryRouterPageInfo(): RouterPageInfo | undefined--><!--Device-BaseCustomComponent-queryRouterPageInfo(): RouterPageInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouterPageInfo](arkts-arkui-routerpageinfo-t.md) | **RouterPageInfo** instance obtained. |

