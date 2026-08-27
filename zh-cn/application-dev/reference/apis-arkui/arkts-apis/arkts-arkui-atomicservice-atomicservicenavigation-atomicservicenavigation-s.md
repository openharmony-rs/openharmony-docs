# AtomicServiceNavigation

作为Page页面的根容器使用，其内部默认包含了标题栏、内容区。其中，内容区在首页默认显示导航内容，在非首页显示 NavDestination的子组件，首页和非首页通过路由进行切换。

> **说明：**
> 
> 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceNavigation, NavDestinationBuilder, MixMode, GradientAlpha, BackgroundTheme, TitleBarType, SideBarOptions, TitleOptions, GradientBackground } from '@kit.ArkUI';
```

## navDestinationBuilder

```TypeScript
navDestinationBuilder?: NavDestinationBuilder
```

创建NavDestination组件所需要的Builder数据。默认值为空，即无内容展示。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gradientBackground

```TypeScript
gradientBackground?: GradientBackground
```

渐变背景色选项。设置时各字段的默认值见GradientBackground。

**类型：** [GradientBackground](arkts-arkui-atomicservice-atomicservicenavigation-gradientbackground-i.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hideTitleBar

```TypeScript
hideTitleBar?: boolean
```

设置是否隐藏标题栏。默认为false。false表示显示标题栏，true表示隐藏标题栏。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menus

```TypeScript
menus?: CustomBuilder | Array<NavigationMenuItem>
```

宽屏场景下用户自定义插入的布局样式。默认值为空，不显示任何样式。屏幕宽度低于600vp为非宽屏场景，大于等于600vp为宽屏场景。

**类型：** [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| Array&lt;[NavigationMenuItem](../arkts-components/arkts-arkui-navigationmenuitem-i.md)&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minContentWidth

```TypeScript
minContentWidth?: Dimension
```

设置导航栏内容区最小宽度（双栏模式下生效）。默认值为360vp。

**类型：** [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: NavigationMode
```

设置导航栏的显示模式。默认值为Auto。支持Stack、Split与Auto模式。

**类型：** [NavigationMode](../arkts-components/arkts-arkui-navigationmode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modeChangeCallback

```TypeScript
modeChangeCallback?: Callback<NavigationMode>
```

当Navigation首次显示或者单双栏状态发生变化时触发该回调。默认值为空。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavigationMode](../arkts-components/arkts-arkui-navigationmode-e.md)&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navBarWidth

```TypeScript
navBarWidth?: Length
```

设置导航栏宽度。默认值为240vp。仅在Navigation组件分栏时生效。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navBarWidthRange

```TypeScript
navBarWidthRange?: [
    Dimension,
    Dimension
  ]
```

设置导航栏最小和最大宽度（双栏模式下生效）。 默认值：最小为240vp，最大为组件宽度的40%，且不大于432vp，如果只设置一个值，则未设置的值按照默认值计算。单位：vp。

**类型：** [     Dimension,     Dimension   ]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navigationContent

```TypeScript
navigationContent?: Callback<void>
```

Navigation容器内容。默认值为空，无内容展示。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navPathStack

```TypeScript
navPathStack?: NavPathStack
```

路由栈信息。默认值为new NavPathStack()。

**类型：** [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sideBarContent

```TypeScript
sideBarContent?: Callback<void>
```

侧边栏的内容。默认值为空。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sideBarOptions

```TypeScript
sideBarOptions?: SideBarOptions
```

侧边栏的功能选项。 默认值为 { sideBarBackground: \$r('sys.color.ohos_id_color_sub_background'), sideBarIcon: \$r('sys.symbol.open_sidebar') }。

**类型：** [SideBarOptions](arkts-arkui-atomicservice-atomicservicenavigation-sidebaroptions-i.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateChangeCallback

```TypeScript
stateChangeCallback?: Callback<boolean>
```

导航栏显示状态切换时触发该回调。true表示导航栏显示，false表示导航栏隐藏。默认值为空。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

设置页面标题。默认值为空字符串。当titleOptions的titleBarType字段设置为TitleBarType.ROUND_ICON或者TitleBarType.SQUARED_ICON， 且设置了titleIcon时，title标题内容将不会显示。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleOptions

```TypeScript
titleOptions?: TitleOptions
```

标题栏选项。默认值为{ isBlurEnabled: true }。当titleBarType字段设置为TitleBarType.ROUND_ICON或者TitleBarType.SQUARED_ICON， 且设置了titleIcon时，title标题内容将不会显示。

**类型：** [TitleOptions](arkts-arkui-atomicservice-atomicservicenavigation-titleoptions-i.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
