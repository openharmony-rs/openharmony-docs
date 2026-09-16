# BaseCustomComponent

自定义组件基类，它是从类CustomComponent迁移过来的。

**继承/实现关系：** BaseCustomComponent extends [CommonAttribute](arkts-arkui-common-comp-attribute.md)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

aboutToAppear函数在创建自定义组件的新实例后，在其build()函数执行前调用。允许在aboutToAppear函数中改变[状态变量](../../../ui/state-management/arkts-state-management-glossary.md#state-variables状态变量)，更改将在后续执行build()函数中生效。实现[自定义布局](arkts-arkui-layoutable-i.md)的自定义组件的aboutToAppear生命周期在布局过程中触发。具体使用说明，详见[自定义组件生命周期指南](../../../ui/state-management/arkts-page-custom-components-lifecycle.md)。

> **说明：** 
> 
> * 在该回调函数内，建议仅执行当前节点组件的初始化逻辑，避免高耗时操作阻塞主线程。对于高耗时操作，推荐采用缓存或异步方案替代。最佳实践请参考[UI组件性能优化-避免在自定义组件的生命周期内执行高耗时操作](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-ui-component-performance-optimization#section18755173594714)。
> 
> * 在需要频繁创建和销毁组件的场景中，将会频繁调用该回调函数。最佳实践请参考[主线程耗时操作优化指导-组件生命周期回调](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-time-optimization-of-the-main-thread#section418843713435)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

aboutToDisappear函数在自定义组件析构销毁时执行。不允许在aboutToDisappear函数中改变状态变量，特别是\@Link变量的修改可能会导致应用行为不稳定。具体使用说明，详见[自定义组件生命周期指南](../../../ui/state-management/arkts-page-custom-components-lifecycle.md)。不建议在aboutToDisappear函数调用后再触发例如自定义弹窗的创建等逻辑，这可能会因为组件树信息丢失导致应用行为异常，例如[@Consume](../../../ui/state-management/arkts-provide-and-consume.md)找不到对应的[@Provide](../../../ui/state-management/arkts-provide-and-consume.md)、弹窗内白屏不显示组件等。

> **说明：** 
> 
> 在需要频繁创建和销毁组件的场景中，将会频繁调用该回调函数。最佳实践请参考
> [主线程耗时操作优化指导-组件生命周期回调](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-time-optimization-of-the-main-thread#section418843713435)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToRecycle

```TypeScript
aboutToRecycle?(): void
```

组件的生命周期回调，在可复用组件从节点树上被加入到复用缓存之前调用。当该组件后续从复用缓存中被重新复用时，将触发aboutToReuse生命周期回调。在频繁调用场景下，应避免在其中执行耗时操作，否则可能导致丢帧卡顿。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

build()函数用于定义自定义组件的声明式UI描述，自定义组件必须定义build()函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getDialogController

```TypeScript
getDialogController(): PromptActionDialogController | undefined
```

The dialog controller of the custom component.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PromptActionDialogController](arkts-arkui-promptactiondialogcontroller-t.md) &#124; undefined | The controller of dialog, or undefined if it is not available |

## getUIContext

```TypeScript
getUIContext(): UIContext
```

Get current UIContext

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIContext](arkts-arkui-uicontext-t.md) | The UIContext that the custom component belongs to. |

## getUniqueId

```TypeScript
getUniqueId(): number
```

Get uniqueId of the custom component.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | The uniqueId of the custom component. |

## onBackPress

```TypeScript
onBackPress?(): void | boolean
```

在router路由页面（即[\@Entry](../../../ui/state-management/arkts-create-custom-components.md#entry)装饰的自定义组件）生效，当用户点击返回按钮时触发。返回true表示页面自己处理返回逻辑，不进行页面路由；返回false表示使用默认的路由返回逻辑，不设置返回值按照false处理。典型使用场景包括：页面有未保存的编辑内容时阻止返回以提示用户保存、弹出自定义确认对话框替代系统默认返回行为等。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidBuild

```TypeScript
onDidBuild?(): void
```

onDidBuild函数在自定义组件的build()函数执行后调用，开发者可以在这个阶段实现埋点数据上报等不影响实际UI的功能。具体使用说明，详见[自定义组件生命周期指南](../../../ui/state-management/arkts-page-custom-components-lifecycle.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFormRecover

```TypeScript
onFormRecover?(statusData: string): void
```

onFormRecover回调函数在卡片恢复时执行，卡片提供方可以拿到卡片回收时卡片管理服务代保存的数据，该数据可以通过[onFormRecycle](#onformrecycle)卡片回收回调函数保存到卡片管理服务。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| statusData | string | 是 | 卡片回收时卡片管理服务代保存的数据。 |

## onFormRecycle

```TypeScript
onFormRecycle?(): string
```

onFormRecycle回调函数在卡片回收时执行，卡片提供方可以返回需要卡片管理服务代保存的数据，在卡片恢复时通过[onFormRecover](#onformrecover)接口传给卡片提供方。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回卡片提供方需要卡片管理服务代保存的数据。 |

## onMeasureSize

```TypeScript
onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions): SizeResult
```

ArkUI框架会在自定义组件确定尺寸时，将该自定义组件的节点信息和尺寸范围通过onMeasureSize传递给该开发者。不允许在onMeasureSize函数中改变状态变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selfLayoutInfo | [GeometryInfo](arkts-arkui-geometryinfo-i.md) | 是 | 计算自定义组件大小后的自身布局信息。<br>**说明：** <br>第一次布局时以自身设置的属性为准。 |
| children | Array&lt;[Measurable](arkts-arkui-measurable-i.md)&gt; | 是 | 计算子组件大小后的子组件布局信息。<br>**说明：** <br>如果没有设置子组件的布局信息，子组件会维持上一次的布局信息，当子组件从来没有设置过尺寸时，尺寸默认为0。 |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | 自定义组件的布局约束信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeResult](arkts-arkui-sizeresult-i.md) | Component size information. |

## onNewParam

```TypeScript
onNewParam?(param: ESObject): void
```

该回调仅生效于由[\@Entry](../../../ui/state-management/arkts-create-custom-components.md#entry)装饰的、作为[router](../arkts-apis/arkts-arkui-router.md)路由页面存在的自定义组件。当之前存在于路由栈中的页面，通过单实例模式[RouterMode](../arkts-apis/arkts-arkui-router-routermode-e.md)移动到栈顶时触发该回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | ESObject | 是 | 路由跳转时传递到目标页面的数据，与router.pushUrl()中params字段传递的数据一致，数据结构由开发者自定义。 |

## onPageHide

```TypeScript
onPageHide?(): void
```

router路由页面（即[\@Entry](../../../ui/state-management/arkts-create-custom-components.md#entry)装饰的自定义组件）每次隐藏时触发一次，包括路由跳转、应用进入后台等场景。

> **说明：** 
> 
> 在该回调函数内，建议避免执行高耗时操作阻塞主线程造成卡顿。对于高耗时操作例如相机资源释放，推荐使用异步方案替代。最佳实践请参考
> [优化应用时延问题-延迟执行资源释放操作](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-application-latency-optimization-cases#section8783201923819)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPageShow

```TypeScript
onPageShow?(): void
```

router路由页面（即[\@Entry](../../../ui/state-management/arkts-create-custom-components.md#entry)装饰的自定义组件）每次显示时触发一次，包括路由跳转、应用进入前台等场景。建议在该回调函数内避免执行高耗时操作阻塞主线程，以免影响页面显示性能。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPlaceChildren

```TypeScript
onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void
```

ArkUI框架会在自定义组件确定位置时，将该自定义组件的子节点自身的尺寸范围通过onPlaceChildren传递给该自定义组件。不允许在onPlaceChildren函数中改变状态变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selfLayoutInfo | [GeometryInfo](arkts-arkui-geometryinfo-i.md) | 是 | 计算自定义组件大小后的自身布局信息。 |
| children | Array&lt;[Layoutable](arkts-arkui-layoutable-i.md)&gt; | 是 | 计算子组件大小后的子组件布局信息。 |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | 自定义组件的布局约束信息。 |

## onWillApplyTheme

```TypeScript
onWillApplyTheme?(theme: Theme): void
```

onWillApplyTheme函数用于获取当前组件上下文的Theme对象，在创建自定义组件的新实例后，在执行其build()函数之前执行。与aboutToAppear不同，onWillApplyTheme用于基于Theme对象初始化状态变量，aboutToAppear用于通用初始化逻辑。允许在onWillApplyTheme函数中改变状态变量，更改将在后续执行build()函数中生效。

> **说明：** 
> 
> 从API version 18开始，该接口支持在状态管理V2组件中使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| theme | [Theme](arkts-arkui-theme-t.md) | 是 | 自定义组件当前生效的Theme对象，可在回调中通过该对象获取主题配色等资源，用于更新组件的样式变量。 |

## pageTransition

```TypeScript
pageTransition?(): void
```

pageTransition函数用于定义页面入场和页面退场的转场动效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## queryNavDestinationInfo

```TypeScript
queryNavDestinationInfo(): NavDestinationInfo | undefined
```

查询自定义组件所属的NavDestination信息，仅当自定义组件在NavDestination的内部时才生效。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavDestinationInfo](arkts-arkui-navdestinationinfo-t.md) &#124; undefined | **NavDestinationInfo** instance obtained. |

## queryNavDestinationInfo

```TypeScript
queryNavDestinationInfo(isInner: Optional<boolean>): NavDestinationInfo | undefined
```

查询当前自定义组件距离最近的NavDestination信息（要求该NavDestination是Navigation的导航页或子页），isInner为true表示向内查找，false表示向外查找。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isInner | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | true：向内查询最近的，且在栈内的NavDestinationInfo的详细信息。<br>false：向外查询最近的，且在栈内的NavDestinationInfo的详细信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavDestinationInfo](arkts-arkui-navdestinationinfo-t.md) &#124; undefined | **NavDestinationInfo** instance obtained. |

## queryNavigationInfo

```TypeScript
queryNavigationInfo(): NavigationInfo | undefined
```

查询自定义组件所属的Navigation信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationInfo](arkts-arkui-navigationinfo-t.md) &#124; undefined | **NavigationInfo** instance obtained. |

## queryRouterPageInfo

```TypeScript
queryRouterPageInfo(): RouterPageInfo | undefined
```

获取RouterPageInfo实例对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouterPageInfo](arkts-arkui-routerpageinfo-t.md) &#124; undefined | **RouterPageInfo** instance obtained. |
