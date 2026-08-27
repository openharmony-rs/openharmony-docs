# AtomicServiceTabs

AtomicServiceTabs高级组件，对Tabs组件中不需要暴露给用户进行自定义的属性进行简化，限制最多显示5个页签，固定页签的样式、位置和大小。

> **说明：**
> 
> 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceTabs, TabBarOptions, TabBarPosition, TabContentBuilder, OnContentWillChangeCallback } from '@kit.ArkUI';
```

## onContentWillChange

```TypeScript
onContentWillChange?: OnContentWillChangeCallback
```

Tabs页面切换拦截事件，新页面即将显示时触发该回调。当回调返回false拦截页面切换时，onChange事件不会被触发。默认值为空。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barBackgroundColor

```TypeScript
barBackgroundColor?: ResourceColor
```

设置TabBar的背景颜色，默认值为透明。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barOverlap

```TypeScript
barOverlap?: boolean
```

设置TabBar是否背景变模糊并叠加在TabContent之上。 true表示TabBar背景变模糊并叠加在TabContent之上，false表示TabBar背景不变模糊且不叠加在TabContent之上。默认值为true。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TabsController
```

Tabs组件的控制器，用于控制页签切换。默认值为new TabsController()。

**类型：** [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index?: number
```

设置当前显示页签的索引，索引值从0开始，取值范围为[0, 页签数-1]，最大不超过4。默认值为0。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutMode

```TypeScript
layoutMode?: LayoutMode
```

设置底部页签的图片、文字排布的方式，默认值为LayoutMode.VERTICAL。

**类型：** [LayoutMode](../arkts-components/arkts-arkui-layoutmode-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<number>
```

Tabs页签切换后触发的事件，回调参数为切换后的页签索引，索引值从0开始。 当onContentWillChange回调返回false拦截页面切换时，该事件不会被触发。默认值为空。

**类型：** Callback&lt;number&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTabBarClick

```TypeScript
onTabBarClick?: Callback<number>
```

Tabs页签点击后触发的事件，回调参数为被点击页签的索引值，索引值从0开始。默认值为空。

**类型：** Callback&lt;number&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabBarOptionsArray

```TypeScript
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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabBarPosition

```TypeScript
tabBarPosition?: TabBarPosition
```

设置页签栏位置，默认值为TabBarPosition.BOTTOM。

**类型：** [TabBarPosition](arkts-arkui-atomicservice-atomicservicetabs-tabbarposition-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabContents

```TypeScript
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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
