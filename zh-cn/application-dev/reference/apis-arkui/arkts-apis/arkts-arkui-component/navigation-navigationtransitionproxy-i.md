# NavigationTransitionProxy

自定义转场动画代理对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface NavigationTransitionProxy--><!--Device-unnamed-export declare interface NavigationTransitionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## finishTransition

```TypeScript
finishTransition(): void
```

结束本次自定义转场动画，开发者需要主动触发该方法来结束本次转场，否则系统会在timeout的时间后结束本次转场。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTransitionProxy-finishTransition(): void--><!--Device-NavigationTransitionProxy-finishTransition(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelTransition

```TypeScript
cancelTransition?: VoidCallback
```

取消本次交互转场，恢复到页面跳转前的路由栈(不支持取消不可交互转场动画)。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTransitionProxy-cancelTransition?: VoidCallback--><!--Device-NavigationTransitionProxy-cancelTransition?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: NavContentInfo
```

退场页面信息。

**类型：** NavContentInfo

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTransitionProxy-from: NavContentInfo--><!--Device-NavigationTransitionProxy-from: NavContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isInteractive

```TypeScript
isInteractive?: boolean
```

本次转场动画是否为可交互转场。 true：本次转场动画是可交互转场；false：本次转场动画不是可交互转场。 默认值： false。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTransitionProxy-isInteractive?: boolean--><!--Device-NavigationTransitionProxy-isInteractive?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: NavContentInfo
```

进场页面信息。

**类型：** NavContentInfo

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTransitionProxy-to: NavContentInfo--><!--Device-NavigationTransitionProxy-to: NavContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateTransition

```TypeScript
updateTransition?: UpdateTransitionCallback
```

更新交互转场动画进度(不可交互动画不支持动画进度设置)。

**类型：** UpdateTransitionCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTransitionProxy-updateTransition?: UpdateTransitionCallback--><!--Device-NavigationTransitionProxy-updateTransition?: UpdateTransitionCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

