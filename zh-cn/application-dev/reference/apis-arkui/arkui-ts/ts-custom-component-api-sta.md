# 自定义组件内置方法（ArkTS-Sta）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @tsj_20201-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->

自定义组件内置方法是由ArkUI开发框架提供给应用开发者的，定义在自定义组件基类上的API。应用开发者可以在自定义组件的实例上调用对应的API以获取当前自定义组件实例相关的信息。例如，查询当前自定义组件上下文的UIContext信息。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 该组件仅可在Stage模型下使用。
>
> - 本模块首批接口从API version 23开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。

## ExtendableComponent

可扩展组件，是自定义组件和自定义对话框的基类。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### getUIContext

getUIContext(): UIContext

获取UIContext对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                      | 说明                    |
| --------------------------------------------------------- | ----------------------- |
| [UIContext](../arkts-apis-uicontext-uicontext.md) | 返回UIContext实例对象。在异步调用的回调方法中使用该接口，或者该接口的起始调用不在当前页面时，可能导致接口调用发生在自定义组件销毁之后，返回undefined。 |

### getUniqueId

getUniqueId(): int

获取当前组件的UniqueId。UniqueId为系统为每个组件分配的Id，可保证当前应用中的唯一性。若在组件对应的节点未创建或已销毁时获取，返回无效UniqueId：-1。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| int | 返回当前Component的UniqueId。 |

### queryNavDestinationInfo

queryNavDestinationInfo(): NavDestinationInfo | undefined;

查询自定义组件所属的NavDestination信息，仅当自定义组件在NavDestination的内部时才生效。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavDestinationInfo](ts-custom-component-api.md#navdestinationinfo) \| undefined | 返回NavDestinationInfo实例对象。 |

### queryNavDestinationInfo

queryNavDestinationInfo(isInner: boolean | undefined): NavDestinationInfo | undefined

查询当前自定义组件距离最近的NavDestination信息（要求该NavDestination是Navigation的导航页或子页），isInner为true表示向内查找，false表示向外查找。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                          | 必填 | 说明                                          |
| ------ | --------------------------------------------- | ---- | --------------------------------------------- |
| isInner  | boolean \| undefined | 是   | true：向内查询最近的，且在栈内的NavDestinationInfo的详细信息。<br/>false：向外查询最近的，且在栈内的NavDestinationInfo的详细信息。|

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavDestinationInfo](ts-custom-component-api.md#navdestinationinfo) \| undefined | 返回NavDestinationInfo实例对象。|

### queryNavigationInfo

queryNavigationInfo(): NavigationInfo | undefined

查询自定义组件所属的Navigation信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavigationInfo](ts-custom-component-api.md#navigationinfo12) \| undefined | 返回NavigationInfo实例对象。 |

### queryRouterPageInfo

queryRouterPageInfo(): RouterPageInfo | undefined;

获取RouterPageInfo实例对象。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [RouterPageInfo](ts-custom-component-api.md#routerpageinfo12) \| undefined | 返回RouterPageInfo实例对象。 |

### onWillApplyTheme

onWillApplyTheme(theme: Theme): void

onWillApplyTheme函数用于获取当前组件上下文的Theme对象，在创建自定义组件的新实例后，在执行其build()函数之前执行。允许在onWillApplyTheme函数中改变状态变量，更改将在后续执行build()函数中生效。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                       | 必填    | 说明         |
|--------|------------------------------------------|------------|-------------------------|
| theme | [Theme](../js-apis-arkui-theme.md#theme) | 是 | 自定义组件当前生效的Theme对象。 |

## LifeCycle

自定义组件和自定义对话框的生命周期接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### onDidBuild

onDidBuild(): void

onDidBuild函数在执行自定义组件的build()函数之后执行，开发者可以在这个阶段进行埋点数据上报等不影响实际UI的功能。不建议在onDidBuild函数中更改状态变量、使用animateTo等功能，这可能会导致不稳定的UI表现。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

## ReuseObject

[aboutToReuse](./ts-custom-component-new-lifecycle.md#abouttoreuse)接收的入参类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### raw

get raw(): RecordData

获取ReuseObject的原始数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [RecordData](../../apis-arkdata/js-apis-data-preferences.md#recorddata23) | 返回ReuseObject的原始数据。 |

### $_get

native $_get(key: string): RecordData

根据索引获取ReuseObject的数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                       | 必填    | 说明         |
|--------|------------------------------------------|------------|-------------------------|
| key | string | 是 | 待获取数据的索引。 |

**返回值：**

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [RecordData](../../apis-arkdata/js-apis-data-preferences.md#recorddata23) | 返回ReuseObject的原始数据。 |

### has

has(key: string): boolean

返回当前索引是否在ReuseObject的数据范围内。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                       | 必填    | 说明         |
|--------|------------------------------------------|------------|-------------------------|
| key | string | 是 | 待获取数据的索引。 |

**返回值：**

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| boolean | 返回当前索引是否在ReuseObject的数据范围内。true表示在数据范围内，false表示不在数据范围内。 |

### keys

keys(): string[]

获取当前ReuseObject的所有数据索引。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| string[] | 返回当前ReuseObject的所有数据索引。 |