# 自定义组件内置方法（静态）
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
> - 本模块首批接口从API version 23开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。

## queryNavDestinationInfo

queryNavDestinationInfo(): NavDestinationInfo | undefined;

查询自定义组件所属的NavDestination信息，仅当自定义组件在NavDestination的内部时才生效。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavDestinationInfo](ts-custom-component-api.md#navdestinationinfo) \| undefined | 返回NavDestinationInfo实例对象。 |

## queryNavDestinationInfo

queryNavDestinationInfo(isInner: Optional\<boolean>): NavDestinationInfo | undefined

查询当前自定义组件距离最近的NavDestination信息（要求该NavDestination是Navigation的导航页或子页），isInner为true表示向内查找，false表示向外查找。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                          | 必填 | 说明                                          |
| ------ | --------------------------------------------- | ---- | --------------------------------------------- |
| isInner  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | 是   | true：向内查询最近的，且在栈内的NavDestinationInfo的详细信息。<br/>false：向外查询最近的，且在栈内的NavDestinationInfo的详细信息。|

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavDestinationInfo](ts-custom-component-api.md#navdestinationinfo) \| undefined | 返回NavDestinationInfo实例对象。|

## queryNavigationInfo

queryNavigationInfo(): NavigationInfo | undefined

查询自定义组件所属的Navigation信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavigationInfo](ts-custom-component-api.md#navigationinfo12) \| undefined | 返回NavigationInfo实例对象。 |

## queryRouterPageInfo

queryRouterPageInfo(): RouterPageInfo | undefined;

获取RouterPageInfo实例对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [RouterPageInfo](ts-custom-component-api.md#routerpageinfo12) \| undefined | 返回RouterPageInfo实例对象。 |

## onWillApplyTheme

onWillApplyTheme(theme: Theme): void

onWillApplyTheme函数用于获取当前组件上下文的Theme对象，在创建自定义组件的新实例后，在执行其build()函数之前执行。允许在onWillApplyTheme函数中改变状态变量，更改将在后续执行build()函数中生效。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型                                       | 必填    | 说明         |
|--------|------------------------------------------|------------|-------------------------|
| theme | [Theme](../js-apis-arkui-theme.md#theme) | 是 | 自定义组件当前生效的Theme对象。 |

