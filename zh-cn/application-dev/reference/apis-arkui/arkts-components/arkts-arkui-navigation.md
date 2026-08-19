# Navigation

Navigation组件是路由导航的根视图容器，一般作为Page页面的根容器使用，其内部默认包含了标题栏、内容区和工具栏，其中内容区默认首页显示导航内容（Navigation的子组件）或非首页显示（ NavDestination的子组件），首页和非首页通过路由进行切换。 > **说明：** > - 该组件从API version 11开始默认支持安全区避让特性(默认值为：expandSafeArea( > [SafeAreaType.SYSTEM, SafeAreaType.KEYBOARD, SafeAreaType.CUTOUT], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]))，开发者可以重 > 写该属性覆盖默认行为，API version 11之前的版本需配合expandSafeArea属性实现安全区避让。 > > - [NavBar](arkts-arkui-navbar-t.md)嵌套使用Navigation时，内层NavDestination的生命周期不和外层NavDestination以及全模态的生命周期进行联动。 > > - Navigation未设置主副标题（title或subTitle）且 > hideBackButton属性设置为true时，不显示标题栏。 > > - Navigation的子页面切换时，新页面会主动请求焦点。 > > - 不建议在aboutToAppear中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

## 子组件 可以包含子组件。 从API version 9开始，推荐与NavRouter组件搭配使用。 从API version 10开始，推荐使用[NavPathStack](arkts-arkui-navpathstack-c.md)配合navDestination属 性进行页面路由。

## Navigation

```TypeScript
Navigation()
```

创建路由导航的根视图容器，适用于使用NavRouter组件进行页面路由。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInterface-(): NavigationAttribute--><!--Device-NavigationInterface-(): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack)
```

绑定导航控制器到Navigation组件，适用于使用[NavPathStack](arkts-arkui-navpathstack-c.md)配合 navDestination属性进行页面路由。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInterface-(pathInfos: NavPathStack): NavigationAttribute--><!--Device-NavigationInterface-(pathInfos: NavPathStack): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-arkui-navpathstack-c.md) | 是 | 导航控制器对象。 |

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack, homeDestination: HomePathInfo)
```

绑定路由栈到Navigation组件，指定一个NavDestination作为Navigation的导航页（主页），适用于使用[NavPathStack](arkts-arkui-navpathstack-c.md)配合 navDestination属性或者系统路由表进行页面路由。使用示例参考 [示例16（Navigation使用NavDestination作为导航页）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例16navigation使用navdestination作为导航页)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInterface-(pathInfos: NavPathStack, homeDestination: HomePathInfo): NavigationAttribute--><!--Device-NavigationInterface-(pathInfos: NavPathStack, homeDestination: HomePathInfo): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-arkui-navpathstack-c.md) | 是 | 路由栈信息。 |
| homeDestination | [HomePathInfo](arkts-arkui-homepathinfo-i.md) | 是 | 主页NavDestination信息。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [HomePathInfo](arkts-arkui-homepathinfo-i.md) | 主页NavDestination的信息。 |
| [MoreButtonOptions](arkts-arkui-morebuttonoptions-i.md) | 更多图标的菜单选项。设置后，可自定义更多按钮的背景模糊样式、背景效果等。 |
| [NavContentInfo](arkts-arkui-navcontentinfo-i.md) | 跳转Destination信息。 |
| [NavigationAnimatedTransition](arkts-arkui-navigationanimatedtransition-i.md) | 自定义转场动画协议，开发者需实现该协议来定义Navigation路由跳转的跳转动画。 |
| [NavigationCommonTitle](arkts-arkui-navigationcommontitle-i.md) | Navigation通用标题。 |
| [NavigationConfiguration](arkts-arkui-navigationconfiguration-i.md) | 导航配置选项。 |
| [NavigationCustomTitle](arkts-arkui-navigationcustomtitle-i.md) | Navigation自定义标题。 |
| [NavigationDividerStyle](arkts-arkui-navigationdividerstyle-i.md) | Navigation分割线颜色及上下边距。 |
| [NavigationInterception](arkts-arkui-navigationinterception-i.md) | Navigation跳转拦截对象。 |
| [NavigationMenuOptions](arkts-arkui-navigationmenuoptions-i.md) | 页面右上角菜单选项。 |
| [NavigationOptions](arkts-arkui-navigationoptions-i.md) | 路由栈操作选项。 |
| [NavigationToolbarOptions](arkts-arkui-navigationtoolbaroptions-i.md) | 工具栏选项。 |
| [NavigationTransitionProxy](arkts-arkui-navigationtransitionproxy-i.md) | 自定义转场动画代理对象。 |
| [PopInfo](arkts-arkui-popinfo-i.md) | 下一个页面返回的回调信息载体。 |
| [ScrollEffectOptions](arkts-arkui-scrolleffectoptions-i.md) | 定义标题栏的滑动模糊效果选项。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InterceptionCallback](arkts-arkui-interceptioncallback-t.md) | Navigation页面跳转前的拦截回调。 |
| [InterceptionModeCallback](arkts-arkui-interceptionmodecallback-t.md) | Navigation单双栏显示状态发生变更时的拦截回调。 |
| [InterceptionShowCallback](arkts-arkui-interceptionshowcallback-t.md) | Navigation页面跳转前和页面跳转后的拦截回调。 |
| [Material](arkts-arkui-material-t.md) | 导入用于Navigation组件的材质类型。 |
| [NavBar](arkts-arkui-navbar-t.md) | Navigation首页名字。 |
| [SystemBarStyle](arkts-arkui-systembarstyle-t.md) | 状态栏的属性。在设置页面级状态栏属性时使用。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BarStyle](arkts-arkui-barstyle-e.md) | 标题栏或工具栏的布局样式。NavDestination的工具栏不支持设置该属性。 |
| [LaunchMode](arkts-arkui-launchmode-e.md) | 路由栈操作模式。 |
| [NavBarPosition](arkts-arkui-navbarposition-e.md) | 导航页位置。 |
| [NavigationMode](arkts-arkui-navigationmode-e.md) | 导航页显示模式。Navigation处于分栏显示状态时，导航页和内容区之间会显示分割线。 |
| [NavigationOperation](arkts-arkui-navigationoperation-e.md) | 页面跳转类型。 |
| [NavigationTitleMode](arkts-arkui-navigationtitlemode-e.md) | 标题栏显示模式。 |
| [ScrollEffectType](arkts-arkui-scrolleffecttype-e.md) | 滑动模糊效果类型。 |
| [ToolbarItemStatus](arkts-arkui-toolbaritemstatus-e.md) | 工具栏单个选项的状态。 |

