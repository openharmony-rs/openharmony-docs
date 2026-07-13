# MultiNavigation

MultiNavigation用于在大尺寸设备上分栏显示、进行路由跳转。

> **说明：**

> 由于MultiNavigation存在多重栈嵌套，调用本文档明确说明的不支持接口或不在本文档支持接口列表中的接口(例如[getParent](../arkts-components/arkts-arkui-navpathstack-c.md#getparent-1)、
> [setInterception](../arkts-components/arkts-arkui-navpathstack-c.md#setinterception-1)、
> [pushDestination](../arkts-components/arkts-arkui-navpathstack-c.md#pushdestination-1)等)，可能会发生无法预期的问题。

> MultiNavigation在深层嵌套场景下，可能存在路由动效异常的问题。

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiStack

```TypeScript
multiStack: MultiNavPathStack
```

设置路由栈。

**类型：** MultiNavPathStack

**起始版本：** 14

**装饰器类型：** @State

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestination

```TypeScript
navDestination: NavDestinationBuildFunction
```

设置加载目标页面的路由规则。

**类型：** NavDestinationBuildFunction

**起始版本：** 14

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHomeShowOnTop

```TypeScript
onHomeShowOnTop?: OnHomeShowOnTopCallback
```

设置主页处于栈顶时的回调。

**类型：** OnHomeShowOnTopCallback

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onNavigationModeChange

```TypeScript
onNavigationModeChange?: OnNavigationModeChangeCallback
```

设置MultiNavigation模式变更时的回调。

**类型：** OnNavigationModeChangeCallback

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

