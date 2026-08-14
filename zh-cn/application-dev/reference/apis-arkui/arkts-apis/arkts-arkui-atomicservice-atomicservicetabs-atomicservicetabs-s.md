# AtomicServiceTabs

AtomicServiceTabs高级组件，对Tabs组件中不需要暴露给用户进行自定义的属性进行简化，限制最多显示5个页签，固定页签的样式、位置和大小。 > **说明：** > > 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export declare struct AtomicServiceTabs--><!--Device-unnamed-export declare struct AtomicServiceTabs-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barBackgroundColor

```TypeScript
@Prop
  barBackgroundColor?: ResourceColor
```

设置TabBar的背景颜色，默认值为透明。

**类型：** ResourceColor

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-@Prop  barBackgroundColor?: ResourceColor--><!--Device-AtomicServiceTabs-@Prop  barBackgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barOverlap

```TypeScript
@Prop
  barOverlap?: boolean
```

设置TabBar是否背景变模糊并叠加在TabContent之上。 true表示TabBar背景变模糊并叠加在TabContent之上，false表示TabBar背景不变模糊且不叠加在TabContent之上。默认值为true。

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-@Prop  barOverlap?: boolean--><!--Device-AtomicServiceTabs-@Prop  barOverlap?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TabsController
```

Tabs组件的控制器，用于控制页签切换。默认值为new TabsController()。

**类型：** TabsController

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-controller?: TabsController--><!--Device-AtomicServiceTabs-controller?: TabsController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
@Prop
  index?: number
```

设置当前显示页签的索引，索引值从0开始，取值范围为[0, 页签数-1]，最大不超过4。默认值为0。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-@Prop  index?: number--><!--Device-AtomicServiceTabs-@Prop  index?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutMode

```TypeScript
@Prop
  layoutMode?: LayoutMode
```

设置底部页签的图片、文字排布的方式，默认值为LayoutMode.VERTICAL。

**类型：** LayoutMode

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-@Prop  layoutMode?: LayoutMode--><!--Device-AtomicServiceTabs-@Prop  layoutMode?: LayoutMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<number>
```

Tabs页签切换后触发的事件，回调参数为切换后的页签索引，索引值从0开始。 当onContentWillChange回调返回false拦截页面切换时，该事件不会被触发。默认值为空。

**类型：** Callback&lt;number&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-onChange?: Callback<number>--><!--Device-AtomicServiceTabs-onChange?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onContentWillChange

```TypeScript
onContentWillChange?: OnContentWillChangeCallback
```

Tabs页面切换拦截事件，新页面即将显示时触发该回调。当回调返回false拦截页面切换时，onChange事件不会被触发。默认值为空。

**类型：** [OnContentWillChangeCallback](arkts-arkui-oncontentwillchangecallback-t.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-onContentWillChange?: OnContentWillChangeCallback--><!--Device-AtomicServiceTabs-onContentWillChange?: OnContentWillChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTabBarClick

```TypeScript
onTabBarClick?: Callback<number>
```

Tabs页签点击后触发的事件，回调参数为被点击页签的索引值，索引值从0开始。默认值为空。

**类型：** Callback&lt;number&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-onTabBarClick?: Callback<number>--><!--Device-AtomicServiceTabs-onTabBarClick?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabBarOptionsArray

```TypeScript
@Prop
  tabBarOptionsArray: [
    TabBarOptions,
    TabBarOptions,
    TabBarOptions?,
    TabBarOptions?,
    TabBarOptions?
  ]
```

页签选项数组，最多支持5个页签。

**类型：** [     TabBarOptions,     TabBarOptions,     TabBarOptions?,     TabBarOptions?,     TabBarOptions?   ]

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-@Prop  tabBarOptionsArray: [    TabBarOptions,    TabBarOptions,    TabBarOptions?,    TabBarOptions?,    TabBarOptions?  ]--><!--Device-AtomicServiceTabs-@Prop  tabBarOptionsArray: [    TabBarOptions,    TabBarOptions,    TabBarOptions?,    TabBarOptions?,    TabBarOptions?  ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabBarPosition

```TypeScript
@Prop
  tabBarPosition?: TabBarPosition
```

设置页签栏位置，默认值为TabBarPosition.BOTTOM。

**类型：** [TabBarPosition](arkts-arkui-atomicservice-atomicservicetabs-tabbarposition-e.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-@Prop  tabBarPosition?: TabBarPosition--><!--Device-AtomicServiceTabs-@Prop  tabBarPosition?: TabBarPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabContents

```TypeScript
@BuilderParam
  tabContents?: [ 
    TabContentBuilder?,
    TabContentBuilder?,
    TabContentBuilder?,
    TabContentBuilder?,
    TabContentBuilder?
  ]
```

内容视图容器数组，最多支持5个页签，默认值为空。

**类型：** [      TabContentBuilder?,     TabContentBuilder?,     TabContentBuilder?,     TabContentBuilder?,     TabContentBuilder?   ]

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-@BuilderParam  tabContents?: [     TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?  ]--><!--Device-AtomicServiceTabs-@BuilderParam  tabContents?: [     TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?  ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

