# NavDestinationBuildFunction

```TypeScript
declare type NavDestinationBuildFunction = (name: string, param?: object) => void
```

MultiNavigation用以加载NavDestination的方法。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 路由页面的标识符。 |
| param | object | 否 | 路由跳转创建页面时传递的参数。 |

