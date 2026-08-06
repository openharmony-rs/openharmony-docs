# Navigation

Navigation组件是路由导航的根视图容器，一般作为Page页面的根容器使用，其内部默认包含了标题栏、内容区和工具栏，其中内容区默认首页显示导航内容（Navigation的子组件）或非首页显示（ [NavDestination]{@link nav_destination}的子组件），首页和非首页通过路由进行切换。 > **说明：** > - 该组件从API version 11开始默认支持安全区避让特性(默认值为：expandSafeArea( > [SafeAreaType.SYSTEM, SafeAreaType.KEYBOARD, SafeAreaType.CUTOUT], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]))，开发者可以重 > 写该属性覆盖默认行为，API version 11之前的版本需配合[expandSafeArea]{@link CommonMethod#expandSafeArea}属性实现安全区避让。 > > - [NavBar]{@link NavBar}嵌套使用Navigation时，内层NavDestination的生命周期不和外层NavDestination以及[全模态]{@link common}的生命周期进行联动。 > > - Navigation未设置主副标题（[title]{@link NavigationAttribute#title}或[subTitle]{@link NavigationAttribute#subTitle}）且 > [hideBackButton]{@link NavigationAttribute#hideBackButton}属性设置为true时，不显示标题栏。 > > - Navigation的子页面切换时，新页面会主动请求焦点。 > > - 不建议在[aboutToAppear]{@link BaseCustomComponent#aboutToAppear}中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

## 子组件 可以包含子组件。 从API version 9开始，推荐与[NavRouter]{@link nav_router}组件搭配使用。 从API version 10开始，推荐使用[NavPathStack]{@link NavPathStack}配合[navDestination]{@link NavigationAttribute#navDestination}属 性进行页面路由。

## Navigation

```TypeScript
Navigation()
```

创建路由导航的根视图容器，适用于使用[NavRouter]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_组件进行页面路由。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInterface-(): NavigationAttribute--><!--Device-NavigationInterface-(): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack)
```

绑定导航控制器到Navigation组件，适用于使用[NavPathStack]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_配合 [navDestination]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_属性进行页面路由。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInterface-(pathInfos: NavPathStack): NavigationAttribute--><!--Device-NavigationInterface-(pathInfos: NavPathStack): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 导航控制器对象。  |

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack, homeDestination: HomePathInfo)
```

绑定路由栈到Navigation组件，指定一个NavDestination作为Navigation的导航页（主页），适用于使用[NavPathStack]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_配合 [navDestination]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_属性或者系统路由表进行页面路由。使用示例参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationInterface-(pathInfos: NavPathStack, homeDestination: HomePathInfo): NavigationAttribute--><!--Device-NavigationInterface-(pathInfos: NavPathStack, homeDestination: HomePathInfo): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 路由栈信息。  |
| homeDestination | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 主页NavDestination信息。  |

## 汇总

