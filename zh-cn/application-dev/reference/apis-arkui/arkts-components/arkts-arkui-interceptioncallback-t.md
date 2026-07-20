# InterceptionCallback

```TypeScript
declare type InterceptionCallback = (from: NavPathInfo|NavBar, to: NavPathInfo|NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void
```

Navigation页面跳转前的拦截回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type InterceptionCallback = (from: NavPathInfo|NavBar, to: NavPathInfo|NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void--><!--Device-unnamed-declare type InterceptionCallback = (from: NavPathInfo|NavBar, to: NavPathInfo|NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | [NavPathInfo](arkts-arkui-navpathinfo-c.md) \| NavBar | 是 | 退场页面信息。参数值为navBar，则表示跳转前的页面为Navigation首页。  |
| to | [NavPathInfo](arkts-arkui-navpathinfo-c.md) \| NavBar | 是 | 进场页面信息。参数值为navBar，则表示跳转的目标页面为Navigation首页。  |
| pathStack | [NavPathStack](arkts-arkui-navpathstack-c.md) | 是 | 页面栈。  |
| operation | [NavigationOperation](arkts-arkui-navigationoperation-e.md) | 是 | 当前页面跳转类型。  |
| isAnimated | boolean | 是 | 页面跳转是否有动画。<br/>true：页面跳转有动画。<br/>false：页面跳转没有动画。  |

