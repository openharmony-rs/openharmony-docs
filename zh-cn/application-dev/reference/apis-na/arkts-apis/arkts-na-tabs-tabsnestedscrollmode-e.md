# TabsNestedScrollMode

Tabs组件和父组件的嵌套滚动模式枚举。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export declare enum TabsNestedScrollMode--><!--Device-unnamed-export declare enum TabsNestedScrollMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELF_ONLY

```TypeScript
SELF_ONLY = 0
```

滚动效果只会在Tabs组件内发生，不会发生其他的嵌套滚动行为，也就是说，当内层组件滚动达到边界时，父容器不会随之滚动。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabsNestedScrollMode-SELF_ONLY = 0--><!--Device-TabsNestedScrollMode-SELF_ONLY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELF_FIRST

```TypeScript
SELF_FIRST = 1
```

Tabs组件首先滚动，当它到达边界时，父容器开始滚动。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabsNestedScrollMode-SELF_FIRST = 1--><!--Device-TabsNestedScrollMode-SELF_FIRST = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

