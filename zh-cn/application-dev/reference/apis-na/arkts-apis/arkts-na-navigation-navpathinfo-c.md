# NavPathInfo

路由页面信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class NavPathInfo--><!--Device-unnamed-export declare class NavPathInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(name: string, param: Object | null | undefined, onPop?: Callback<PopInfo>, isEntry?: boolean)
```

创建NavPathInfo对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathInfo-constructor(name: string, param: Object | null | undefined, onPop?: Callback<PopInfo>, isEntry?: boolean)--><!--Device-NavPathInfo-constructor(name: string, param: Object | null | undefined, onPop?: Callback<PopInfo>, isEntry?: boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。该名称匹配开发者设置的路由表中的name，包括以下两种：&lt;br/&gt;1. 自定义路由表，开发者通过 [navDestination](arkts-na-navigation-navigationattribute-i.md#navDestination)方法传递。&lt;br/&gt;2. 系统路由表，通过routerMap中的name设置，可参考 示例2。 |
| param | Object \| null \| undefined | 是 | 开发者设置的NavDestination页面详细参数，unknown可以是用户自定义的类型。&lt;br/&gt;取值为undefined时，页面信 息无效。 |
| onPop | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[PopInfo](arkts-na-navigation-popinfo-i.md)&gt; | 否 | NavDestination页面触发 [pop](arkts-na-navigation-navpathstack-c.md#pop)、 [popToName](arkts-na-navigation-navpathstack-c.md#popToName)、 [popToIndex](arkts-na-navigation-navpathstack-c.md#popToIndex)时返回的回调。仅 [pop](arkts-na-navigation-navpathstack-c.md#pop)、 [popToName](arkts-na-navigation-navpathstack-c.md#popToName)、 [popToIndex](arkts-na-navigation-navpathstack-c.md#popToIndex)中设置result参数后触发。 |
| isEntry | boolean | 否 | 标记NavDestination是否为入口页面。&lt;br/&gt;true：NavDestination是入口页面；false：NavDestination不是入口页面。&lt; br/&gt;默认值：false &lt;br/&gt;标记清理时机：1. 在当前navDestination页面触发一次全局返回事件。2. 应用退至后台。&lt;br/&gt;**说明：**&lt;br/&gt;入口NavDestination不响应应用内的 全局back事件，直接触发应用间的全局back事件 |

