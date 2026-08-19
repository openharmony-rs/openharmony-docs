# NavDestination

作为子页面的根容器，用于显示Navigation的内容区。 > **说明：** > - 该组件从API version 11开始默认支持安全区避让特性(默认值为：expandSafeArea([SafeAreaType.SYSTEM], > [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]))，开发者可以重写该属性覆盖默认行为，API version 11之前的版本需配合expandSafeArea属性实现 > 安全区避让。 > > - NavDestination组件必须配合Navigation使用，作为Navigation目的页面的根节点，单独使用只能作为普通容器组件，不具备路由相关属性能力。 > > - 如果路由栈中间页面的生命周期发生变化，跳转之前的栈顶NavDestination的生命周期(onWillShow, onShown, onHidden, onWillDisappear)与跳转之后的栈顶 > NavDestination的生命周期(onWillShow, onShown, onHidden, onWillDisappear)均在最后触发。 > > - NavDestination未设置主副标题并且没有返回键时，不显示标题栏。 > > - 不建议设置位置、大小等布局相关属性，可能会造成页面显示异常。例如在NavDestination上添加zIndex属性时，会覆盖掉系统设置的层级，可能导致出现显示异常。

## 子组件 > **说明：** > > - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。 > > - 子组件个数：多个。

## NavDestination

```TypeScript
NavDestination()
```

创建Navigation子页面的根容器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInterface-(): NavDestinationAttribute--><!--Device-NavDestinationInterface-(): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [NavDestinationCommonTitle](arkts-arkui-navdestinationcommontitle-i.md) | NavDestination通用标题。 |
| [NavDestinationContext](arkts-arkui-navdestinationcontext-i.md) | NavDestination上下文信息。 |
| [NavDestinationCustomTitle](arkts-arkui-navdestinationcustomtitle-i.md) | NavDestination自定义标题。 |
| [NavDestinationTransition](arkts-arkui-navdestinationtransition-i.md) | NavDestination自定义动画接口。 |
| [NestedScrollInfo](arkts-arkui-nestedscrollinfo-i.md) | 嵌套可滚动容器组件信息。 |
| [RouteMapConfig](arkts-arkui-routemapconfig-i.md) | 路由配置信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NavDestinationTransitionDelegate](arkts-arkui-navdestinationtransitiondelegate-t.md) | NavDestination自定义转场动画的代理函数。 |
| [Orientation](arkts-arkui-orientation-t.md) | 页面显示方向的枚举类型。 |
| [RestoreStateCallback](arkts-arkui-restorestatecallback-t.md) | 自定义页面状态恢复回调。 |
| [SaveStateCallback](arkts-arkui-savestatecallback-t.md) | 自定义页面状态保存回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NavDestinationActiveReason](arkts-arkui-navdestinationactivereason-e.md) | NavDestination激活态或者非激活态变化的原因。 |
| [NavDestinationMode](arkts-arkui-navdestinationmode-e.md) | NavDestination类型。 |
| [NavigationSystemTransitionType](arkts-arkui-navigationsystemtransitiontype-e.md) | 系统转场动画类型。 |
| [VisibilityChangeReason](arkts-arkui-visibilitychangereason-e.md) | NavDestination可见性发生变化的原因。 |

