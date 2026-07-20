# InterceptionShowCallback

```TypeScript
declare type InterceptionShowCallback = (from: NavDestinationContext|NavBar, to: NavDestinationContext|NavBar, operation: NavigationOperation, isAnimated: boolean) => void
```

Navigation页面跳转前和页面跳转后的拦截回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type InterceptionShowCallback = (from: NavDestinationContext|NavBar, to: NavDestinationContext|NavBar, operation: NavigationOperation, isAnimated: boolean) => void--><!--Device-unnamed-declare type InterceptionShowCallback = (from: NavDestinationContext|NavBar, to: NavDestinationContext|NavBar, operation: NavigationOperation, isAnimated: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | [NavDestinationContext](arkts-arkui-navdestinationcontext-i.md) \| NavBar | 是 | 页面跳转之前的栈顶页面信息。参数值为navBar，则表示跳转前的页面为Navigation首页。  |
| to | [NavDestinationContext](arkts-arkui-navdestinationcontext-i.md) \| NavBar | 是 | 页面跳转之前的栈顶页面信息。参数值为navBar，则表示跳转前的页面为Navigation首页。  |
| operation | [NavigationOperation](arkts-arkui-navigationoperation-e.md) | 是 | 当前页面跳转类型。  |
| isAnimated | boolean | 是 | 页面跳转是否有动画。<br/>true：页面跳转有动画。<br/>false：页面跳转没有动画。  |

