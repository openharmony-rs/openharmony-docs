# Navigation

Navigation组件是路由导航的根视图容器，一般作为Page页面的根容器使用，其内部默认包含了标题栏、内容区和工具栏，其中内容区默认首页显示导航内容（Navigation的子组件）或非首页显示（
[NavDestination]{@link nav_destination}的子组件），首页和非首页通过路由进行切换。

> **说明：**

> - 该组件从API version 11开始默认支持安全区避让特性(默认值为：expandSafeArea(
> [SafeAreaType.SYSTEM, SafeAreaType.KEYBOARD, SafeAreaType.CUTOUT], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]))，开发者可以重
> 写该属性覆盖默认行为，API version 11之前的版本需配合[expandSafeArea]{@link CommonMethod#expandSafeArea}属性实现安全区避让。
>
> - [NavBar]{@link NavBar}嵌套使用Navigation时，内层NavDestination的生命周期不和外层NavDestination以及[全模态]{@link common}的生命周期进行联动。
>
> - Navigation未设置主副标题（[title]{@link NavigationAttribute#title}或[subTitle]{@link NavigationAttribute#subTitle}）且
> [hideBackButton]{@link NavigationAttribute#hideBackButton}属性设置为true时，不显示标题栏。
>
> - Navigation的子页面切换时，新页面会主动请求焦点。
>
> - 不建议在[aboutToAppear]{@link BaseCustomComponent#aboutToAppear}中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。


## Navigation

```TypeScript
Navigation()
```

创建路由导航的根视图容器，适用于使用[NavRouter]{@link nav_router}组件进行页面路由。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack)
```

绑定导航控制器到Navigation组件，适用于使用[NavPathStack]{@link NavPathStack}配合
[navDestination]{@link NavigationAttribute#navDestination}属性进行页面路由。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | NavPathStack | 是 | 导航控制器对象。 |

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack, homeDestination: HomePathInfo)
```

绑定路由栈到Navigation组件，并且指定一个NavDestination作为Navigation的导航页（主页），适用于使用[NavPathStack]{@link NavPathStack}配合
[navDestination]{@link NavigationAttribute#navDestination}属性或者系统路由表进行页面路由。使用示例参考
[示例16（Navigation使用NavDestination作为导航页）](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例16navigation使用navdestination作为导航页)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | NavPathStack | 是 | 路由栈信息。 |
| homeDestination | HomePathInfo | 是 | 主页NavDestination信息。 |

## 汇总

- [HomePathInfo](arkts-arkui-navigation-homepathinfo-i.md)
- [MoreButtonOptions](arkts-arkui-navigation-morebuttonoptions-i.md)
- [NavContentInfo](arkts-arkui-navigation-navcontentinfo-i.md)
- [NavigationAnimatedTransition](arkts-arkui-navigation-navigationanimatedtransition-i.md)
- [NavigationCommonTitle](arkts-arkui-navigation-navigationcommontitle-i.md)
- [NavigationConfiguration](arkts-arkui-navigation-navigationconfiguration-i.md)
- [NavigationCustomTitle](arkts-arkui-navigation-navigationcustomtitle-i.md)
- [NavigationDividerStyle](arkts-arkui-navigation-navigationdividerstyle-i.md)
- [NavigationInterception](arkts-arkui-navigation-navigationinterception-i.md)
- [NavigationMenuItem](arkts-arkui-navigation-navigationmenuitem-i.md)
- [NavigationMenuOptions](arkts-arkui-navigation-navigationmenuoptions-i.md)
- [NavigationOptions](arkts-arkui-navigation-navigationoptions-i.md)
- [NavigationTitleOptions](arkts-arkui-navigation-navigationtitleoptions-i.md)
- [NavigationToolbarOptions](arkts-arkui-navigation-navigationtoolbaroptions-i.md)
- [NavigationTransitionProxy](arkts-arkui-navigation-navigationtransitionproxy-i.md)
- [PopInfo](arkts-arkui-navigation-popinfo-i.md)
- [ScrollEffectOptions](arkts-arkui-navigation-scrolleffectoptions-i.md)
- [ToolbarItem](arkts-arkui-navigation-toolbaritem-i.md)
- [InterceptionCallback](arkts-arkui-navigation-interceptioncallback-t.md)
- [InterceptionModeCallback](arkts-arkui-navigation-interceptionmodecallback-t.md)
- [InterceptionShowCallback](arkts-arkui-navigation-interceptionshowcallback-t.md)
- [Material](arkts-arkui-navigation-material-t.md)
- [NavBar](arkts-arkui-navigation-navbar-t.md)
- [SystemBarStyle](arkts-arkui-navigation-systembarstyle-t.md)
- [BarStyle](arkts-arkui-navigation-barstyle-e.md)
- [LaunchMode](arkts-arkui-navigation-launchmode-e.md)
- [NavBarPosition](arkts-arkui-navigation-navbarposition-e.md)
- [NavigationMode](arkts-arkui-navigation-navigationmode-e.md)
- [NavigationOperation](arkts-arkui-navigation-navigationoperation-e.md)
- [NavigationTitleMode](arkts-arkui-navigation-navigationtitlemode-e.md)
- [ScrollEffectType](arkts-arkui-navigation-scrolleffecttype-e.md)
- [ToolbarItemStatus](arkts-arkui-navigation-toolbaritemstatus-e.md)
