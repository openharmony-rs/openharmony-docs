# NavRouter

导航组件，默认提供点击响应处理，不需要开发者自定义点击事件逻辑。

## 子组件

必须包含两个子组件，其中第二个子组件必须为[NavDestination]{@link nav_destination}。

> **说明：**  
>  
> 子组件个数异常时：  
>  
> 1. 有且仅有1个时，触发路由到NavDestination的能力失效。  
>  
> 2. 有且仅有1个时，且使用NavDestination场景下，不进行路由。  
>  
> 3. 大于2个时，后续的子组件不显示。  
>  
> 4. 第二个子组件不为NavDestination时，触发路由功能失效。

## NavRouter

```TypeScript
NavRouter()
```

创建NavRouter。

**起始版本：** 9

**废弃版本：** 13

**替代接口：** <!--SUBSTITUTE_API-->NavDestinationAttribute<!--/SUBSTITUTE_API-->

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavRouterInterface-(): NavRouterAttribute--><!--Device-NavRouterInterface-(): NavRouterAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NavRouter

```TypeScript
NavRouter(value: RouteInfo)
```

提供路由信息，指定点击NavRouter时，要跳转的NavDestination页面。

**起始版本：** 10

**废弃版本：** 13

**替代接口：** <!--SUBSTITUTE_API-->Navigation#NavPathInfo<!--/SUBSTITUTE_API-->

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavRouterInterface-(value: RouteInfo): NavRouterAttribute--><!--Device-NavRouterInterface-(value: RouteInfo): NavRouterAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RouteInfo](arkts-arkui-routeinfo-i.md) | 是 | 路由信息。  |

## 汇总

- [RouteInfo](arkts-arkui-navrouter-routeinfo-i.md)
- [NavRouteMode](arkts-arkui-navrouter-navroutemode-e.md)
