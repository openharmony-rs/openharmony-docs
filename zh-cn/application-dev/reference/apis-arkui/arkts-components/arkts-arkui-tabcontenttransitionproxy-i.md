# TabContentTransitionProxy

Tabs自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画的起始和目标页面信息，同时，也可以通过调用该对象的finishTransition接口通知Tabs组件自定义动画已结束。

**起始版本：** 11

<!--Device-unnamed-declare interface TabContentTransitionProxy--><!--Device-unnamed-declare interface TabContentTransitionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="finishtransition"></a>
## finishTransition

```TypeScript
finishTransition(): void
```

通知Tabs组件，此页面的自定义动画已结束。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TabContentTransitionProxy-finishTransition(): void--><!--Device-TabContentTransitionProxy-finishTransition(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: number
```

自定义动画起始页面对应的index值，索引从0开始。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TabContentTransitionProxy-from: number--><!--Device-TabContentTransitionProxy-from: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: number
```

自定义动画目标页面对应的index值，索引从0开始。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TabContentTransitionProxy-to: number--><!--Device-TabContentTransitionProxy-to: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

