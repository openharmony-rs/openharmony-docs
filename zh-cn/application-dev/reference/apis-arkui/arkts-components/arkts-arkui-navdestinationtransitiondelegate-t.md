# NavDestinationTransitionDelegate

```TypeScript
declare type NavDestinationTransitionDelegate =
    (operation: NavigationOperation, isEnter: boolean) => Array<NavDestinationTransition> | undefined
```

NavDestination自定义转场动画的代理函数。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operation | NavigationOperation | 是 | 当前页面转场的操作类型。 |
| isEnter | boolean | 是 | 当前页面是否为入场页面。<br/>true：当前页面是入场页面；false：当前页面不是入场页面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;NavDestinationTransition&gt; \| undefined | Array of custom animations for the **NavDestination** page.If **undefined** is returned, the default system animation is used. |

