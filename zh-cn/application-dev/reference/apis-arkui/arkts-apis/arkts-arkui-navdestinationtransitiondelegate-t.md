# NavDestinationTransitionDelegate

```TypeScript
export type NavDestinationTransitionDelegate = (operation: NavigationOperation, isEnter: boolean) => (Array<NavDestinationTransition> | undefined)
```

NavDestination自定义转场动画的代理函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type NavDestinationTransitionDelegate = (operation: NavigationOperation, isEnter: boolean) => (Array<NavDestinationTransition> | undefined)--><!--Device-unnamed-export type NavDestinationTransitionDelegate = (operation: NavigationOperation, isEnter: boolean) => (Array<NavDestinationTransition> | undefined)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operation | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前页面转场的操作类型。  |
| isEnter | boolean | 是 | 当前页面是否为入场页面。 \_\_\_HTML\_TAG\_USD\_0\_\_\_true：当前页面是入场页面； false：当前页面不是入场页面。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| (Array&lt;NavDestinationTransition&gt; \| undefined) | user-set custom navDestination transitions. |

