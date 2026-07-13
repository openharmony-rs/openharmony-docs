# TabsOptions

Tabs组件参数，设置Tabs的页签位置，当前显示页签的索引，Tabs控制器和TabBar的[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**起始版本：** 15

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barModifier

```TypeScript
barModifier?: CommonModifier
```

设置TabBar的[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**说明：**

动态置为undefined时会保持当前状态不变，不会重置各通用属性。

由一个CommonModifier切换为另一个CommonModifier时，重复属性会进行覆盖，非重复属性会同时生效，不会重置前一个CommonModifier的通用属性。

Tabs的[barWidth](TabsAttribute#barWidth)、[barHeight](TabsAttribute#barHeight(value: Length))、
[barBackgroundColor](TabsAttribute#barBackgroundColor)、
[barBackgroundBlurStyle](TabsAttribute#barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions))
、[barBackgroundEffect](TabsAttribute#barBackgroundEffect)属性会覆盖CommonModifier的
[width](arkts-arkui-commonmethod-c.md#width-1)、[height](arkts-arkui-commonmethod-c.md#height-1)、
[backgroundColor](arkts-arkui-commonmethod-c.md#backgroundcolor-2)、
[backgroundBlurStyle](arkts-arkui-commonmethod-c.md#backgroundblurstyle-2)
、[backgroundEffect](arkts-arkui-commonmethod-c.md#backgroundeffect-2)属性。

[align](arkts-arkui-commonmethod-c.md#align-1)属性仅在
[BarMode.Scrollable](TabsAttribute#barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions))模式下生
效，且Tabs为横向时还需[nonScrollableLayoutStyle](arkts-arkui-scrollablebarmodeoptions-i.md)未设置或设置为异常值时才能生效。

[TabContent](arkts-arkui-tabcontent.md)组件的
[tabBar](TabContentAttribute#tabBar(content: ComponentContent | SubTabBarStyle | BottomTabBarStyle | string | Resource | CustomBuilder | TabBarOptions))
属性为底部页签样式时不支持拖拽功能。

**类型：** CommonModifier

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barPosition

```TypeScript
barPosition?: BarPosition
```

设置Tabs的页签位置。

默认值：BarPosition.Start。

**类型：** BarPosition

**默认值：** BarPosition.Start [since 11]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TabsController
```

设置Tabs控制器。

**类型：** TabsController

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index?: number
```

设置当前显示页签的索引。

默认值：0

**说明：**

设置为小于0的值时按默认值显示。

可选值为[0, TabContent子节点数量-1]。

直接修改index跳页时，切换动效不生效。 使用TabController的[changeIndex](arkts-arkui-tabscontroller-c.md#changeindex-1)时，默认生效切换动效，可以设置
[animationDuration](TabsAttribute#animationDuration)为0关闭动画。

从API version 10开始，该参数支持[$$](../../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

Tabs重建、系统资源切换（如系统字体切换、系统深浅色切换）或者组件属性变化时，会跳转到index对应的页面。若需要在上述情况下不跳转，建议使用双向绑定。

**类型：** number

**默认值：** 0 [since 11]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

