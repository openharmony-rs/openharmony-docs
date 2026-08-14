# NavDestinationContext

NavDestination上下文信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface NavDestinationContext--><!--Device-unnamed-export declare interface NavDestinationContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getConfigInRouteMap

```TypeScript
getConfigInRouteMap(): RouteMapConfig | undefined
```

获取当前NavDestination的路由配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationContext-getConfigInRouteMap(): RouteMapConfig | undefined--><!--Device-NavDestinationContext-getConfigInRouteMap(): RouteMapConfig | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouteMapConfig](arkts-na-navdestination-routemapconfig-i.md) |  |

## mode

```TypeScript
mode?: NavDestinationMode
```

当前NavDestination的类型。

**类型：** [NavDestinationMode](arkts-na-navdestination-navdestinationmode-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationContext-mode?: NavDestinationMode--><!--Device-NavDestinationContext-mode?: NavDestinationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

当前NavDestination的唯一ID，由系统自动生成，和组件通用属性id无关。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationContext-navDestinationId?: string--><!--Device-NavDestinationContext-navDestinationId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pathInfo

```TypeScript
pathInfo: NavPathInfo
```

跳转NavDestination时指定的参数。

**类型：** [NavPathInfo](../../apis-arkui/arkts-components/arkts-arkui-navpathinfo-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationContext-pathInfo: NavPathInfo--><!--Device-NavDestinationContext-pathInfo: NavPathInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pathStack

```TypeScript
pathStack: NavPathStack
```

当前NavDestination所处的导航控制器。

**类型：** [NavPathStack](../../apis-arkui/arkts-components/arkts-arkui-navpathstack-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationContext-pathStack: NavPathStack--><!--Device-NavDestinationContext-pathStack: NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

