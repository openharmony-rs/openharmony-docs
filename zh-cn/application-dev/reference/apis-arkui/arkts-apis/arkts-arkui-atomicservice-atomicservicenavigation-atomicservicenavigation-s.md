# AtomicServiceNavigation

作为Page页面的根容器使用，其内部默认包含了标题栏、内容区，其中内容区默认首页显示导航内容或非首页显示（ [NavDestination]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子组件），首页和非首页通过路由进行切换。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct AtomicServiceNavigation--><!--Device-unnamed-export declare struct AtomicServiceNavigation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gradientBackground

```TypeScript
gradientBackground?: GradientBackground
```

设置导航栏渐变色背景，作用区域包含标题栏和内容栏。

**类型：** GradientBackground

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-gradientBackground?: GradientBackground--><!--Device-AtomicServiceNavigation-gradientBackground?: GradientBackground-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hideTitleBar

```TypeScript
hideTitleBar?: boolean
```

Hide navigation title bar.

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-hideTitleBar?: boolean--><!--Device-AtomicServiceNavigation-hideTitleBar?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menus

```TypeScript
menus?: CustomBuilder | Array<NavigationMenuItem>
```

The layout style users defined and inserted.

**类型：** CustomBuilder \| Array&lt;NavigationMenuItem&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @BuilderParam

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-menus?: CustomBuilder | Array<NavigationMenuItem>--><!--Device-AtomicServiceNavigation-menus?: CustomBuilder | Array<NavigationMenuItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minContentWidth

```TypeScript
minContentWidth?: Dimension
```

Sets the minimum width of content.

**类型：** Dimension

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-minContentWidth?: Dimension--><!--Device-AtomicServiceNavigation-minContentWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: NavigationMode
```

Sets the mode of navigation.

**类型：** NavigationMode

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-mode?: NavigationMode--><!--Device-AtomicServiceNavigation-mode?: NavigationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modeChangeCallback

```TypeScript
modeChangeCallback?: Callback<NavigationMode>
```

Trigger callback when navigation mode changes.

**类型：** Callback&lt;NavigationMode&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-modeChangeCallback?: Callback<NavigationMode>--><!--Device-AtomicServiceNavigation-modeChangeCallback?: Callback<NavigationMode>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navBarWidth

```TypeScript
navBarWidth?: Length
```

Sets the width of navigation bar.

**类型：** Length

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-navBarWidth?: Length--><!--Device-AtomicServiceNavigation-navBarWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navBarWidthRange

```TypeScript
navBarWidthRange?: [
    Dimension,
    Dimension
  ]
```

Sets the minimum width and the maximum width of navigation bar.

**类型：** [     Dimension,     Dimension   ]

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-navBarWidthRange?: [    Dimension,    Dimension  ]--><!--Device-AtomicServiceNavigation-navBarWidthRange?: [    Dimension,    Dimension  ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationBuilder

```TypeScript
navDestinationBuilder?: NavDestinationBuilder
```

The builder of navDestination.

**类型：** NavDestinationBuilder

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @BuilderParam

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-navDestinationBuilder?: NavDestinationBuilder--><!--Device-AtomicServiceNavigation-navDestinationBuilder?: NavDestinationBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navPathStack

```TypeScript
navPathStack?: NavPathStack
```

the information of route page.Providers methods for controlling destination page in the stack.

**类型：** NavPathStack

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @State

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-navPathStack?: NavPathStack--><!--Device-AtomicServiceNavigation-navPathStack?: NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navigationContent

```TypeScript
navigationContent?: Callback<void>
```

the content of Navigation.

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @BuilderParam

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-navigationContent?: Callback<void>--><!--Device-AtomicServiceNavigation-navigationContent?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sideBarContent

```TypeScript
sideBarContent?: Callback<void>
```

Set side bar content.

**类型：** Callback&lt;void&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @BuilderParam

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-sideBarContent?: Callback<void>--><!--Device-AtomicServiceNavigation-sideBarContent?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sideBarOptions

```TypeScript
sideBarOptions?: SideBarOptions
```

Set side bar options.

**类型：** SideBarOptions

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-sideBarOptions?: SideBarOptions--><!--Device-AtomicServiceNavigation-sideBarOptions?: SideBarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateChangeCallback

```TypeScript
stateChangeCallback?: Callback<boolean>
```

Trigger callback when the visibility of navigation bar change.

**类型：** Callback&lt;boolean&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-stateChangeCallback?: Callback<boolean>--><!--Device-AtomicServiceNavigation-stateChangeCallback?: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

Sets the Navigation title.

**类型：** ResourceStr

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-title?: ResourceStr--><!--Device-AtomicServiceNavigation-title?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleOptions

```TypeScript
titleOptions?: TitleOptions
```

The color of Navigation's TitleBar.

**类型：** TitleOptions

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-titleOptions?: TitleOptions--><!--Device-AtomicServiceNavigation-titleOptions?: TitleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

