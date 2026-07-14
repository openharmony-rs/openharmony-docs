# NavRouter

导航组件，默认提供点击响应处理，不需要开发者自定义点击事件逻辑。


## NavRouter

```TypeScript
NavRouter()
```

创建NavRouter。

**起始版本：** 9

**废弃版本：** 13

**替代接口：** <!--SUBSTITUTE_API-->NavDestinationAttribute<!--/SUBSTITUTE_API-->

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

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

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RouteInfo | 是 | 路由信息。 |

## 汇总

- [RouteInfo](arkts-arkui-navrouter-routeinfo-i.md)
- [NavRouteMode](arkts-arkui-navrouter-navroutemode-e.md)
