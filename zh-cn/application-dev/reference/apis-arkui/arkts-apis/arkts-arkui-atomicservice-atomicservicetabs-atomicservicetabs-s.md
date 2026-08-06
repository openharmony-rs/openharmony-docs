# AtomicServiceTabs

AtomicServiceTabs高级组件，对Tabs组件一些不需提供给用户自定义设计的属性进行简化，限制最多显示5个页签，固定页签样式，位置和大小。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Component

<!--Device-unnamed-/** Copyright (C) 2024 Huawei Device Co., Ltd.* Licensed under the Apache License, Version 2.0 (the "License");* you may not use this file except in compliance with the License.* You may obtain a copy of the License at** http://www.apache.org/licenses/LICENSE-2.0** Unless required by applicable law or agreed to in writing, software* distributed under the License is distributed on an "AS IS" BASIS,* WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.* See the License for the specific language governing permissions and* limitations under the License.*/export declare struct AtomicServiceTabs--><!--Device-unnamed-/** Copyright (C) 2024 Huawei Device Co., Ltd.* Licensed under the Apache License, Version 2.0 (the "License");* you may not use this file except in compliance with the License.* You may obtain a copy of the License at** http://www.apache.org/licenses/LICENSE-2.0** Unless required by applicable law or agreed to in writing, software* distributed under the License is distributed on an "AS IS" BASIS,* WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.* See the License for the specific language governing permissions and* limitations under the License.*/export declare struct AtomicServiceTabs-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barBackgroundColor

```TypeScript
barBackgroundColor?: ResourceColor
```

Sets the barBackgroundColor of tabs.

**类型：** ResourceColor

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-barBackgroundColor?: ResourceColor--><!--Device-AtomicServiceTabs-barBackgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barOverlap

```TypeScript
barOverlap?: boolean
```

set if need overlap, default value is true.

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-barOverlap?: boolean--><!--Device-AtomicServiceTabs-barOverlap?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TabsController
```

Provide methods for switching tabs.

**类型：** TabsController

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-controller?: TabsController--><!--Device-AtomicServiceTabs-controller?: TabsController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index?: number
```

Sets the index of tabs.

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-index?: number--><!--Device-AtomicServiceTabs-index?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutMode

```TypeScript
layoutMode?: LayoutMode
```

Sets the layout mode of the bottom tab bar

**类型：** LayoutMode

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-layoutMode?: LayoutMode--><!--Device-AtomicServiceTabs-layoutMode?: LayoutMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<number>
```

onChange callback of tabs when tabs changed.

**类型：** Callback&lt;number&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-onChange?: Callback<number>--><!--Device-AtomicServiceTabs-onChange?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onContentWillChange

```TypeScript
onContentWillChange?: OnContentWillChangeCallback
```

onContentWillChange callback of tabs when tabbar is clicked.

**类型：** OnContentWillChangeCallback

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-onContentWillChange?: OnContentWillChangeCallback--><!--Device-AtomicServiceTabs-onContentWillChange?: OnContentWillChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTabBarClick

```TypeScript
onTabBarClick?: Callback<number>
```

onTabBarClick callback of tabs when tabbar is clicked.

**类型：** Callback&lt;number&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-onTabBarClick?: Callback<number>--><!--Device-AtomicServiceTabs-onTabBarClick?: Callback<number>-End-->

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

The tabBar array of tabs.

**类型：** [     TabBarOptions,     TabBarOptions,     TabBarOptions?,     TabBarOptions?,     TabBarOptions?   ]

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-tabBarOptionsArray: [    TabBarOptions,    TabBarOptions,    TabBarOptions?,    TabBarOptions?,    TabBarOptions?  ]--><!--Device-AtomicServiceTabs-tabBarOptionsArray: [    TabBarOptions,    TabBarOptions,    TabBarOptions?,    TabBarOptions?,    TabBarOptions?  ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tabBarPosition

```TypeScript
tabBarPosition?: TabBarPosition
```

set the positions of tabbar.

**类型：** TabBarPosition

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-tabBarPosition?: TabBarPosition--><!--Device-AtomicServiceTabs-tabBarPosition?: TabBarPosition-End-->

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

The TabContent array of tabs.

**类型：** [      TabContentBuilder?,     TabContentBuilder?,     TabContentBuilder?,     TabContentBuilder?,     TabContentBuilder?   ]

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @BuilderParam

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceTabs-tabContents?: [     TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?  ]--><!--Device-AtomicServiceTabs-tabContents?: [     TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?,    TabContentBuilder?  ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

