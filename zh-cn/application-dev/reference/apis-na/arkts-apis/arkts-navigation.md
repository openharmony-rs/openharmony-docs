# navigation

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [Navigation](arkts-na-navigation-navigation-f.md#Navigation) | 绑定导航控制器到Navigation组件，适用于使用[NavPathStack](arkts-na-navigation-navpathstack-c.md#NavPathStack)配合 [navDestination](arkts-na-navigation-navigationattribute-i.md#navDestination)属性进行页面路由。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | 路由页面信息。 |
| [NavPathStack](arkts-na-navigation-navpathstack-c.md) | Navigation导航控制器，以栈的数据结构管理Navigation中所有的子页面，并提供栈操作的方法用于控制Navigation中子页面的切换。 从API version 12开始，NavPathStack允许被继承，派生类对象可以替代基类NavPathStack对象使用。使用示例参见 示例10。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [HomePathInfo](arkts-na-navigation-homepathinfo-i.md) | 主页NavDestination的信息。 |
| [MoreButtonOptions](arkts-na-navigation-morebuttonoptions-i.md) | 更多图标的菜单选项。 |
| [NavContentInfo](arkts-na-navigation-navcontentinfo-i.md) | 跳转Destination信息。 |
| [NavigationAnimatedTransition](arkts-na-navigation-navigationanimatedtransition-i.md) | 自定义转场动画协议，开发者需实现该协议来定义Navigation路由跳转的跳转动画。 |
| [NavigationAttribute](arkts-na-navigation-navigationattribute-i.md) | 除支持通用属性外，还支持以下属性： |
| [NavigationCommonTitle](arkts-na-navigation-navigationcommontitle-i.md) | Navigation通用标题。 |
| [NavigationCustomTitle](arkts-na-navigation-navigationcustomtitle-i.md) | Navigation自定义标题。 |
| [NavigationDividerStyle](arkts-na-navigation-navigationdividerstyle-i.md) | Navigation分割线颜色及上下边距。 |
| [NavigationInterception](arkts-na-navigation-navigationinterception-i.md) | Navigation跳转拦截对象。 |
| [NavigationMenuItem](arkts-na-navigation-navigationmenuitem-i.md) | 导航菜单项，包括菜单图标和菜单信息。 |
| [NavigationMenuOptions](arkts-na-navigation-navigationmenuoptions-i.md) | 页面右上角菜单选项。 |
| [NavigationModuleInfo](arkts-na-navigation-navigationmoduleinfo-i.md) | Navigation的模块信息。 |
| [NavigationOptions](arkts-na-navigation-navigationoptions-i.md) | 路由栈操作选项。 |
| [NavigationTitleOptions](arkts-na-navigation-navigationtitleoptions-i.md) | 标题栏选项。 |
| [NavigationToolbarOptions](arkts-na-navigation-navigationtoolbaroptions-i.md) | 工具栏选项。 |
| [NavigationTransitionProxy](arkts-na-navigation-navigationtransitionproxy-i.md) | 自定义转场动画代理对象。 |
| [PopInfo](arkts-na-navigation-popinfo-i.md) | 下一个页面返回的回调信息载体。 |
| [ScrollEffectOptions](arkts-na-navigation-scrolleffectoptions-i.md) | 标题栏滑动效果类型。 |
| [ToolbarItem](arkts-na-navigation-toolbaritem-i.md) | 工具栏可配置参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BarStyle](arkts-na-navigation-barstyle-e.md) | 标题栏或工具栏的布局样式。NavDestination的工具栏不支持设置该属性。 |
| [LaunchMode](arkts-na-navigation-launchmode-e.md) | 路由栈操作模式。 |
| [NavBarPosition](arkts-na-navigation-navbarposition-e.md) | 导航页位置。 |
| [NavigationMode](arkts-na-navigation-navigationmode-e.md) | 导航页显示模式。Navigation处于分栏显示状态时，导航页和内容区之间会显示分割线。 |
| [NavigationOperation](arkts-na-navigation-navigationoperation-e.md) | 页面跳转类型。 |
| [NavigationTitleMode](arkts-na-navigation-navigationtitlemode-e.md) | 标题栏显示模式。 |
| [ScrollEffectType](arkts-na-navigation-scrolleffecttype-e.md) | 标题栏滑动模糊效果类型。 |
| [ToolbarItemStatus](arkts-na-navigation-toolbaritemstatus-e.md) | 工具栏单个选项的状态。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InterceptionCallback](arkts-na-interceptioncallback-t.md) | Navigation页面跳转前的拦截回调。 |
| [InterceptionModeCallback](arkts-na-interceptionmodecallback-t.md) | Navigation单双栏显示状态发生变更时的拦截回调。 |
| [InterceptionShowCallback](arkts-na-interceptionshowcallback-t.md) | Navigation页面跳转前和页面跳转后的拦截回调。 |
| [NavBar](arkts-na-navbar-t.md) | Navigation首页名字。 |
| [SystemBarStyle](arkts-na-systembarstyle-t.md) | 状态栏的属性。在设置页面级状态栏属性时使用。 |
| [UpdateTransitionCallback](arkts-na-updatetransitioncallback-t.md) | 交互转场动画进度。 |

