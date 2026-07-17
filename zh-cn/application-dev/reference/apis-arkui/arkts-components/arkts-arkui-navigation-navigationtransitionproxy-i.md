# NavigationTransitionProxy

自定义转场动画代理对象。

**起始版本：** 11

<!--Device-unnamed-declare interface NavigationTransitionProxy--><!--Device-unnamed-declare interface NavigationTransitionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelTransition

```TypeScript
cancelTransition?(): void
```

取消本次交互转场，恢复到页面跳转前的路由栈(不支持取消不可交互转场动画)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTransitionProxy-cancelTransition?(): void--><!--Device-NavigationTransitionProxy-cancelTransition?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## finishTransition

```TypeScript
finishTransition(): void
```

结束本次自定义转场动画，开发者需要主动触发该方法来结束本次转场，否则系统会在timeout的时间后结束本次转场。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTransitionProxy-finishTransition(): void--><!--Device-NavigationTransitionProxy-finishTransition(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateTransition

```TypeScript
updateTransition?(progress: number): void
```

更新交互转场动画进度(不可交互动画不支持动画进度设置)。

> **说明：**  
>  
> 不建议在[aboutToAppear](arkts-arkui-common-basecustomcomponent-c.md#abouttoappear-1)中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTransitionProxy-updateTransition?(progress: number): void--><!--Device-NavigationTransitionProxy-updateTransition?(progress: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | number | 是 | 设置交互转场动画进度百分比。取值范围：[0, 1] |

## from

```TypeScript
from: NavContentInfo
```

退场页面信息。

**类型：** NavContentInfo

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTransitionProxy-from: NavContentInfo--><!--Device-NavigationTransitionProxy-from: NavContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isInteractive

```TypeScript
isInteractive?: boolean
```

本次转场动画是否为可交互转场。

true：本次转场动画是可交互转场；false：本次转场动画不是可交互转场。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTransitionProxy-isInteractive?: boolean--><!--Device-NavigationTransitionProxy-isInteractive?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: NavContentInfo
```

进场页面信息。

**类型：** NavContentInfo

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTransitionProxy-to: NavContentInfo--><!--Device-NavigationTransitionProxy-to: NavContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

