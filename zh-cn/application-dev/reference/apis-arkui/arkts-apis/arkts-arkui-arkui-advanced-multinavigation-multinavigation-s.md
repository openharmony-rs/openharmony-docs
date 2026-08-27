# MultiNavigation

MultiNavigation是一个支持分栏导航的组件，提供多层页面栈管理能力，通过MultiNavPathStack统一管理主页、详情页、全屏页等不同类型页面的导航栈。 支持左起右清栈等智能路由策略，适用于平板、折叠屏等大尺寸设备的复杂导航场景，能够优化页面跳转体验、提升用户操作效率。

> **说明：**

> 由于MultiNavigation存在多层次的页面栈结构（主页、详情页、全屏页各自维护子栈，并由MultiNavPathStack统一管理），
> 调用本文档明确说明的不支持接口或不在本文档支持接口列表中的接口(例如[getParent](ts-basic-components-navigation.md#getparent11)、
> [setInterception](ts-basic-components-navigation.md#setinterception12)
> [pushDestination](ts-basic-components-navigation.md#pushdestination11)等)，可能会发生无法预期的问题。

> MultiNavigation在深层嵌套场景下，可能存在路由动效异常的问题。
@struct { MultiNavigation }

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SplitPolicy, MultiNavigation, MultiNavPathStack } from '@kit.ArkUI';
```

## navDestination

```TypeScript
navDestination: NavDestinationBuildFunction
```

设置加载目标页面的路由规则。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHomeShowOnTop

```TypeScript
onHomeShowOnTop?: OnHomeShowOnTopCallback
```

设置主页处于栈顶时的回调。不传入时不监听主页栈顶状态变化。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onNavigationModeChange

```TypeScript
onNavigationModeChange?: OnNavigationModeChangeCallback
```

设置MultiNavigation模式变更时的回调。当需要在导航模式变化时执行特定业务逻辑（如调整页面布局、更新UI状态等）时传入此回调。不传入时不监听导航模式变更事件，导航模式变更时无回调触发。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiStack

```TypeScript
multiStack: MultiNavPathStack
```

设置路由栈。

**类型：** [MultiNavPathStack](arkts-arkui-arkui-advanced-multinavigation-multinavpathstack-c.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
