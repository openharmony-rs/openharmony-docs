# InterceptionCallback

```TypeScript
export type InterceptionCallback = (from: NavPathInfo | NavBar, to: NavPathInfo | NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void
```

Navigation页面跳转前的拦截回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type InterceptionCallback = (from: NavPathInfo | NavBar, to: NavPathInfo | NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void--><!--Device-unnamed-export type InterceptionCallback = (from: NavPathInfo | NavBar, to: NavPathInfo | NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) \| [NavBar](arkts-na-navbar-t.md) | 是 | Navigation页面跳转前的拦截回调。 <br>取值约束:参数值为navBar，则表示跳转前的页面为Navigation首页。 |
| to | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) \| [NavBar](arkts-na-navbar-t.md) | 是 | Navigation页面跳转前的拦截回调。 <br>取值约束:参数值为navBar，则表示跳转前的页面为Navigation首页。 |
| pathStack | [NavPathStack](arkts-na-navigation-navpathstack-c.md) | 是 | 页面栈。 |
| operation | [NavigationOperation](arkts-na-navigation-navigationoperation-e.md) | 是 | 当前页面跳转类型。 |
| isAnimated | boolean | 是 | 页面跳转是否有动画。 |

