# NavDestinationContext

NavDestination上下文信息。

**起始版本：** 11

<!--Device-unnamed-declare interface NavDestinationContext--><!--Device-unnamed-declare interface NavDestinationContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getConfigInRouteMap

```TypeScript
getConfigInRouteMap(): RouteMapConfig | undefined
```

获取当前NavDestination的路由配置信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationContext-getConfigInRouteMap(): RouteMapConfig | undefined--><!--Device-NavDestinationContext-getConfigInRouteMap(): RouteMapConfig | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouteMapConfig](arkts-arkui-nav-destination-routemapconfig-i.md) | Routing configuration of the current page.<br> **undefined** is returned when the page is not configured through the route table. |

## mode

```TypeScript
mode?: NavDestinationMode
```

当前NavDestination的类型。默认值：NavDestinationMode.Standard。

**类型：** NavDestinationMode

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationContext-mode?: NavDestinationMode--><!--Device-NavDestinationContext-mode?: NavDestinationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

当前NavDestination的唯一ID，由系统自动生成，和组件通用属性id无关。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationContext-navDestinationId?: string--><!--Device-NavDestinationContext-navDestinationId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pathInfo

```TypeScript
pathInfo: NavPathInfo
```

跳转NavDestination时指定的参数。

**类型：** NavPathInfo

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationContext-pathInfo: NavPathInfo--><!--Device-NavDestinationContext-pathInfo: NavPathInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pathStack

```TypeScript
pathStack: NavPathStack
```

当前NavDestination所处的导航控制器。

**类型：** NavPathStack

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationContext-pathStack: NavPathStack--><!--Device-NavDestinationContext-pathStack: NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

