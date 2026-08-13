# AtomicServiceNavigation

作为Page页面的根容器使用，其内部默认包含了标题栏、内容区。其中，内容区在首页默认显示导航内容，在非首页显示 NavDestination的子组件，首页和非首页通过路由进行切换。 > **说明：** > > 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export declare struct AtomicServiceNavigation--><!--Device-unnamed-export declare struct AtomicServiceNavigation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gradientBackground

```TypeScript
@Prop
  gradientBackground?: GradientBackground
```

渐变背景色选项。设置时各字段的默认值见GradientBackground。

**类型：** [GradientBackground](arkts-arkui-atomicservice-atomicservicenavigation-gradientbackground-i.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  gradientBackground?: GradientBackground--><!--Device-AtomicServiceNavigation-@Prop  gradientBackground?: GradientBackground-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hideTitleBar

```TypeScript
@Prop
  hideTitleBar?: boolean
```

设置是否隐藏标题栏。默认为false。false表示显示标题栏，true表示隐藏标题栏。

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  hideTitleBar?: boolean--><!--Device-AtomicServiceNavigation-@Prop  hideTitleBar?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menus

```TypeScript
@BuilderParam
  menus?: CustomBuilder | Array<NavigationMenuItem>
```

宽屏场景下用户自定义插入的布局样式。默认值为空，不显示任何样式。屏幕宽度低于600vp为非宽屏场景，大于等于600vp为宽屏场景。

**类型：** CustomBuilder \| Array&lt;NavigationMenuItem&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@BuilderParam  menus?: CustomBuilder | Array<NavigationMenuItem>--><!--Device-AtomicServiceNavigation-@BuilderParam  menus?: CustomBuilder | Array<NavigationMenuItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minContentWidth

```TypeScript
@Prop
  minContentWidth?: Dimension
```

设置导航栏内容区最小宽度（双栏模式下生效）。默认值为360vp。

**类型：** Dimension

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  minContentWidth?: Dimension--><!--Device-AtomicServiceNavigation-@Prop  minContentWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
@Prop
  mode?: NavigationMode
```

设置导航栏的显示模式。默认值为Auto。支持Stack、Split与Auto模式。

**类型：** NavigationMode

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  mode?: NavigationMode--><!--Device-AtomicServiceNavigation-@Prop  mode?: NavigationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modeChangeCallback

```TypeScript
modeChangeCallback?: Callback<NavigationMode>
```

当Navigation首次显示或者单双栏状态发生变化时触发该回调。默认值为空。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;NavigationMode&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-modeChangeCallback?: Callback<NavigationMode>--><!--Device-AtomicServiceNavigation-modeChangeCallback?: Callback<NavigationMode>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navBarWidth

```TypeScript
@Prop
  navBarWidth?: Length
```

设置导航栏宽度。默认值为240vp。仅在Navigation组件分栏时生效。

**类型：** Length

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  navBarWidth?: Length--><!--Device-AtomicServiceNavigation-@Prop  navBarWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navBarWidthRange

```TypeScript
@Prop
  navBarWidthRange?: [
    Dimension,
    Dimension
  ]
```

设置导航栏最小和最大宽度（双栏模式下生效）。 默认值：最小为240vp，最大为组件宽度的40%，且不大于432vp，如果只设置一个值，则未设置的值按照默认值计算。单位：vp。

**类型：** [     Dimension,     Dimension   ]

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  navBarWidthRange?: [    Dimension,    Dimension  ]--><!--Device-AtomicServiceNavigation-@Prop  navBarWidthRange?: [    Dimension,    Dimension  ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationBuilder

```TypeScript
@BuilderParam
  navDestinationBuilder?: NavDestinationBuilder
```

创建NavDestination组件所需要的Builder数据。默认值为空，即无内容展示。

**类型：** [NavDestinationBuilder](arkts-arkui-navdestinationbuilder-t.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@BuilderParam  navDestinationBuilder?: NavDestinationBuilder--><!--Device-AtomicServiceNavigation-@BuilderParam  navDestinationBuilder?: NavDestinationBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navPathStack

```TypeScript
@State
  navPathStack?: NavPathStack
```

路由栈信息。默认值为new NavPathStack()。

**类型：** NavPathStack

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@State  navPathStack?: NavPathStack--><!--Device-AtomicServiceNavigation-@State  navPathStack?: NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navigationContent

```TypeScript
@BuilderParam
  navigationContent?: Callback<void>
```

Navigation容器内容。默认值为空，无内容展示。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@BuilderParam  navigationContent?: Callback<void>--><!--Device-AtomicServiceNavigation-@BuilderParam  navigationContent?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sideBarContent

```TypeScript
@BuilderParam
  sideBarContent?: Callback<void>
```

侧边栏的内容。默认值为空。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@BuilderParam  sideBarContent?: Callback<void>--><!--Device-AtomicServiceNavigation-@BuilderParam  sideBarContent?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sideBarOptions

```TypeScript
@Prop
  sideBarOptions?: SideBarOptions
```

侧边栏的功能选项。 默认值为 { sideBarBackground: \$r('sys.color.ohos_id_color_sub_background'), sideBarIcon: \$r('sys.symbol.open_sidebar') }。

**类型：** [SideBarOptions](arkts-arkui-atomicservice-atomicservicenavigation-sidebaroptions-i.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  sideBarOptions?: SideBarOptions--><!--Device-AtomicServiceNavigation-@Prop  sideBarOptions?: SideBarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateChangeCallback

```TypeScript
stateChangeCallback?: Callback<boolean>
```

导航栏显示状态切换时触发该回调。true表示导航栏显示，false表示导航栏隐藏。默认值为空。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-stateChangeCallback?: Callback<boolean>--><!--Device-AtomicServiceNavigation-stateChangeCallback?: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
@Prop
  title?: ResourceStr
```

设置页面标题。默认值为空字符串。当titleOptions的titleBarType字段设置为TitleBarType.ROUND_ICON或者TitleBarType.SQUARED_ICON， 且设置了titleIcon时，title标题内容将不会显示。

**类型：** ResourceStr

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  title?: ResourceStr--><!--Device-AtomicServiceNavigation-@Prop  title?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleOptions

```TypeScript
@Prop
  titleOptions?: TitleOptions
```

标题栏选项。默认值为{ isBlurEnabled: true }。当titleBarType字段设置为TitleBarType.ROUND_ICON或者TitleBarType.SQUARED_ICON， 且设置了titleIcon时，title标题内容将不会显示。

**类型：** [TitleOptions](arkts-arkui-atomicservice-atomicservicenavigation-titleoptions-i.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceNavigation-@Prop  titleOptions?: TitleOptions--><!--Device-AtomicServiceNavigation-@Prop  titleOptions?: TitleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

