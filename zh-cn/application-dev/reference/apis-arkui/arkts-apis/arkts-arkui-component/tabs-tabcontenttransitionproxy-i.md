# TabContentTransitionProxy

Tabs自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画的起始和目标页面信息，同时，也可以通过调用该对象的finishTransition接口通知Tabs组件自定义动画已结束。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TabContentTransitionProxy--><!--Device-unnamed-export declare interface TabContentTransitionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## finishTransition

```TypeScript
finishTransition(): void
```

通知Tabs组件，此页面的自定义动画已结束。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabContentTransitionProxy-finishTransition(): void--><!--Device-TabContentTransitionProxy-finishTransition(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: int
```

自定义动画起始页面对应的index值，索引从0开始。 取值范围为全体整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabContentTransitionProxy-from: int--><!--Device-TabContentTransitionProxy-from: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: int
```

自定义动画目标页面对应的index值，索引从0开始。 取值范围为全体整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabContentTransitionProxy-to: int--><!--Device-TabContentTransitionProxy-to: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

