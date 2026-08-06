# InterceptionCallback

```TypeScript
export type InterceptionCallback = (from: NavPathInfo | NavBar, to: NavPathInfo | NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void
```

Navigation页面跳转前的拦截回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type InterceptionCallback = (from: NavPathInfo | NavBar, to: NavPathInfo | NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void--><!--Device-unnamed-export type InterceptionCallback = (from: NavPathInfo | NavBar, to: NavPathInfo | NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| NavBar | 是 | Navigation页面跳转前的拦截回调。 \_\_\_HTML\_TAG\_USD\_0\_\_\_取值约束:参数值为navBar，则表示跳转前的页面为Navigation首页。  |
| to | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| NavBar | 是 | Navigation页面跳转前的拦截回调。 \_\_\_HTML\_TAG\_USD\_0\_\_\_取值约束:参数值为navBar，则表示跳转前的页面为Navigation首页。  |
| pathStack | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 页面栈。  |
| operation | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前页面跳转类型。  |
| isAnimated | boolean | 是 | 页面跳转是否有动画。  |

