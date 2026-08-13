# NavDestination

作为子页面的根容器，用于显示Navigation的内容区。 > **说明：** > - 该组件从API version 11开始默认支持安全区避让特性(默认值为：expandSafeArea([SafeAreaType.SYSTEM], > [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]))，开发者可以重写该属性覆盖默认行为，API version 11之前的版本需配合expandSafeArea属性实现 > 安全区避让。 > > - NavDestination组件必须配合Navigation使用，作为Navigation目的页面的根节点，单独使用只能作为普通容器组件，不具备路由相关属性能力。 > > - 如果路由栈中间页面的生命周期发生变化，跳转之前的栈顶NavDestination的生命周期(onWillShow, onShown, onHidden, onWillDisappear)与跳转之后的栈顶 > NavDestination的生命周期(onWillShow, onShown, onHidden, onWillDisappear)均在最后触发。 > > - NavDestination未设置主副标题并且没有返回键时，不显示标题栏。 > > - 不建议设置位置、大小等布局相关属性，可能会造成页面显示异常。例如在NavDestination上添加zIndex属性时，会覆盖掉系统设置的层级，可能导致出现显示异常。

## 子组件 > **说明：** > > - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。 > > - 子组件个数：多个。

## NavDestination

```TypeScript
NavDestination()
```

创建Navigation子页面的根容器。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInterface-(): NavDestinationAttribute--><!--Device-NavDestinationInterface-(): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

- [NavDestinationCommonTitle](arkts-arkui-navdestinationcommontitle-i.md)
- [NavDestinationContext](arkts-arkui-navdestinationcontext-i.md)
- [NavDestinationCustomTitle](arkts-arkui-navdestinationcustomtitle-i.md)
- [NavDestinationTransition](arkts-arkui-navdestinationtransition-i.md)
- [NestedScrollInfo](arkts-arkui-nestedscrollinfo-i.md)
- [RouteMapConfig](arkts-arkui-routemapconfig-i.md)
- [NavDestinationTransitionDelegate](arkts-arkui-navdestinationtransitiondelegate-t.md)
- [Orientation](arkts-arkui-orientation-t.md)
- [RestoreStateCallback](arkts-arkui-restorestatecallback-t.md)
- [SaveStateCallback](arkts-arkui-savestatecallback-t.md)
- [NavDestinationActiveReason](arkts-arkui-navdestinationactivereason-e.md)
- [NavDestinationMode](arkts-arkui-navdestinationmode-e.md)
- [NavigationSystemTransitionType](arkts-arkui-navigationsystemtransitiontype-e.md)
- [VisibilityChangeReason](arkts-arkui-visibilitychangereason-e.md)
