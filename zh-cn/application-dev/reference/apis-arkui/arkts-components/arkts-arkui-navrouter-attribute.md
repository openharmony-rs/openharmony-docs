# NavRouter属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** NavRouterAttribute extends [CommonMethod<NavRouterAttribute>](CommonMethod<NavRouterAttribute>)

**起始版本：** 9

**废弃版本：** 13

**替代接口：** NavPathStack

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode(mode: NavRouteMode)
```

设置指定点击NavRouter跳转到NavDestination页面时，使用的路由模式。

**起始版本：** 10

**废弃版本：** 13

**替代接口：** LaunchMode

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | NavRouteMode | 是 | 指定点击NavRouter跳转到NavDestination页面时，使用的路由模式。<br/>默认值：NavRouteMode.PUSH_WITH_RECREATE |

## onStateChange

```TypeScript
onStateChange(callback: (isActivated: boolean) => void)
```

组件激活状态切换时触发该回调。开发者点击激活NavRouter，加载对应的NavDestination子组件时，回调onStateChange(true)。NavRouter对应的NavDestination子组件不再显示时，回调
onStateChange(false)。

**起始版本：** 9

**废弃版本：** 13

**替代接口：** onShown

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isActivated: boolean) =&gt; void | 是 | isActivated为true时表示激活，为false时表示未激活。 |

