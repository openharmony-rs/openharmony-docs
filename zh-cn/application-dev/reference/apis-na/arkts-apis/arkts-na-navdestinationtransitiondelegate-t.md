# NavDestinationTransitionDelegate

```TypeScript
export type NavDestinationTransitionDelegate = (operation: NavigationOperation, isEnter: boolean) => (Array<NavDestinationTransition> | undefined)
```

NavDestination自定义转场动画的代理函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type NavDestinationTransitionDelegate = (operation: NavigationOperation, isEnter: boolean) => (Array<NavDestinationTransition> | undefined)--><!--Device-unnamed-export type NavDestinationTransitionDelegate = (operation: NavigationOperation, isEnter: boolean) => (Array<NavDestinationTransition> | undefined)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operation | [NavigationOperation](../../apis-arkui/arkts-components/arkts-arkui-navigationoperation-e.md) | 是 | 当前页面转场的操作类型。 |
| isEnter | boolean | 是 | 当前页面是否为入场页面。 <br>true：当前页面是入场页面； false：当前页面不是入场页面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| (Array&lt;[NavDestinationTransition](arkts-na-navdestination-navdestinationtransition-i.md)&gt; \| undefined) | user-set custom navDestination transitions. |

