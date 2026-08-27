# TabsOptions

Tabs组件参数，设置Tabs的页签位置，当前显示页签的索引，Tabs控制器和页签栏（TabBar）的通用属性。

**起始版本：** 15

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## barModifier

```TypeScript
barModifier?: CommonModifier
```

设置TabBar的通用属性，用于通过CommonModifier统一管理TabBar的样式、布局等通用属性。 当需要动态修改TabBar的通用属性或实现属性的状态管理时传入此参数，不传入时TabBar使用默认样式和布局，无额外通用属性设置。  
**说明：**动态置为undefined时会保持当前状态不变，不会重置各通用属性。由一个CommonModifier切换为另一个CommonModifier时，重复属性会进行覆盖，非重复属性会同时生效，不会重置前一个CommonModifier的通用属性。Tabs的[barWidth](arkts-arkui-tabs-attribute.md#barwidth)、[barHeight](arkts-arkui-tabs-attribute.md#barheight)、 [barBackgroundColor](arkts-arkui-tabs-attribute.md#barbackgroundcolor)、 [barBackgroundBlurStyle](arkts-arkui-tabs-attribute.md#barbackgroundblurstyle) 、[barBackgroundEffect](arkts-arkui-tabs-attribute.md#barbackgroundeffect)属性会覆盖CommonModifier的 width、height、 backgroundColor、 backgroundBlurStyle 、backgroundEffect属性。
align属性仅在 [BarMode.Scrollable](arkts-arkui-tabs-attribute.md#barmode)模式下生 效，且Tabs为横向时还需[nonScrollableLayoutStyle](arkts-arkui-scrollablebarmodeoptions-i.md)未设置或设置为异常值时才能生效。  
TabContent组件的 [tabBar](arkts-arkui-tabcontent-attribute.md#tabbar) 属性为底部页签样式时不支持拖拽功能。

**类型：** [CommonModifier](arkts-arkui-commonmodifier-t.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barPosition

```TypeScript
barPosition?: BarPosition
```

设置Tabs的页签位置。默认值：BarPosition.Start。

**类型：** [BarPosition](arkts-arkui-barposition-e.md)

**默认值：** BarPosition.Start [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TabsController
```

设置Tabs控制器。

**类型：** [TabsController](arkts-arkui-tabscontroller-c.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index?: number
```

设置当前显示页签的索引。默认值：0  
**说明：**设置为小于0的值时按默认值显示。可选值为[0, TabContent子节点数量-1]。直接修改index跳页时，切换动效不生效。 使用TabController的[changeIndex](arkts-arkui-tabscontroller-c.md#changeindex)时，默认生效切换动效，可以设置 [animationDuration](arkts-arkui-tabs-attribute.md#animationduration)为0关闭动画。从API version 10开始，该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。Tabs重建、系统资源切换（如系统字体切换、系统深浅色切换）或者组件属性变化时，会跳转到index对应的页面。若需要在上述情况下不跳转，建议使用双向绑定。

**类型：** number

**默认值：** 0 [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
