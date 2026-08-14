# NavPathInfo

路由页面信息。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare class NavPathInfo--><!--Device-unnamed-declare class NavPathInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(name: string, param: unknown, onPop?: import('../api/@ohos.base').Callback<PopInfo>, isEntry?: boolean)
```

创建NavPathInfo对象。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathInfo-constructor(name: string, param: unknown, onPop?: import('../api/@ohos.base').Callback<PopInfo>, isEntry?: boolean)--><!--Device-NavPathInfo-constructor(name: string, param: unknown, onPop?: import('../api/@ohos.base').Callback<PopInfo>, isEntry?: boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。该名称匹配开发者设置的路由表中的name，包括以下两种：&lt;br/&gt;1. 自定义路由表，开发者通过 navDestination方法传递。&lt;br/&gt;2. 系统路由表，通过routerMap中的name设置，可参考 [示例2](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例2使用导航控制器方法)。 |
| param | unknown | 是 | 开发者设置的NavDestination页面详细参数，unknown可以是用户自定义的类型。 |
| onPop | import('../api/@ohos.base').Callback&lt;[PopInfo](arkts-arkui-popinfo-i.md)&gt; | 否 | NavDestination页面触发 [pop](arkts-arkui-navpathstack-c.md#pop)、 [popToName](arkts-arkui-navpathstack-c.md#popToName)、 [popToIndex](arkts-arkui-navpathstack-c.md#popToIndex)时返回的回调。仅 [pop](arkts-arkui-navpathstack-c.md#pop)、 [popToName](arkts-arkui-navpathstack-c.md#popToName)、 [popToIndex](arkts-arkui-navpathstack-c.md#popToIndex)中设置result参数后触 发。<br>**起始版本：** 11 |
| isEntry | boolean | 否 | 标记NavDestination是否为入口页面。&lt;br/&gt;true：NavDestination是入口页面；false：NavDestination不是入口页面。&lt;br/ &gt;默认值：false &lt;br/&gt;标记清理时机：1. 在当前navDestination页面触发一次全局返回事件。2. 应用退至后台。&lt;br/&gt;**说明：**&lt;br/&gt;入口NavDestination不响应应用内的全局 back事件，直接触发应用间的全局back事件。<br>**起始版本：** 12 |

## isEntry

```TypeScript
isEntry?: boolean
```

标记NavDestination是否为入口页面。 true：NavDestination是入口页面；false：NavDestination不是入口页面。 默认值：false 标记清理时机：1. 在当前navDestination页面触发一次全局back事件。2. 应用退至后台。 **说明：** 入口NavDestination不响应应用内的全局back事件，直接触发应用间的全局back事件。

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathInfo-isEntry?: boolean--><!--Device-NavPathInfo-isEntry?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

NavDestination页面名称。该名称匹配开发者设置的路由表中的name，包括以下两种： 1. 自定义路由表，开发者通过navDestination方法传递。 2. 系统路由表，通过routerMap中的name设置，可参考[示例2](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例2使用导航控制器方法)。

**类型：** string

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathInfo-name: string--><!--Device-NavPathInfo-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

NavDestination页面唯一标识符，该id由系统默认生成且全局唯一，通过[getPathStack](arkts-arkui-navpathstack-c.md#getPathStack)接口可读取，但不可以主动赋新值。

**类型：** string

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathInfo-navDestinationId?: string--><!--Device-NavPathInfo-navDestinationId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPop

```TypeScript
onPop?: import('../api/@ohos.base').Callback<PopInfo>
```

NavDestination页面触发[pop](arkts-arkui-navpathstack-c.md#pop)、 [popToName](arkts-arkui-navpathstack-c.md#popToName)、 [popToIndex](arkts-arkui-navpathstack-c.md#popToIndex)时返回的回调。仅 [pop](arkts-arkui-navpathstack-c.md#pop)、 [popToName](arkts-arkui-navpathstack-c.md#popToName)、 [popToIndex](arkts-arkui-navpathstack-c.md#popToIndex)中设置result参数后触发。

**类型：** import('../api/@ohos.base').Callback&lt;[PopInfo](arkts-arkui-popinfo-i.md)&gt;

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathInfo-onPop?: import('../api/@ohos.base').Callback<PopInfo>--><!--Device-NavPathInfo-onPop?: import('../api/@ohos.base').Callback<PopInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param?: unknown
```

开发者设置的NavDestination页面详细参数，unknown可以是用户自定义的类型。

**类型：** unknown

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathInfo-param?: unknown--><!--Device-NavPathInfo-param?: unknown-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

