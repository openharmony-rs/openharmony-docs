# GestureActionPhase

表示触发的手势回调阶段的枚举类型，对应 the action callbacks defined in gesture.d.ts. Therefore, not all gesture types have all the following phase definitions. For example, SwipeGesture only has one callback named onAction, so it also only has one enumeration type, which is WILL_START.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export const enum GestureActionPhase--><!--Device-unnamed-export const enum GestureActionPhase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WILL_START

```TypeScript
WILL_START = 0
```

手势已被系统成功识别，action-start/action回调即将被触发。 executed immediately.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureActionPhase-WILL_START = 0--><!--Device-GestureActionPhase-WILL_START = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WILL_END

```TypeScript
WILL_END = 1
```

表示手势已确定为结束，通常发生在用户抬起手指时， fingers, ending the entire interaction, and the action-end callback will be executed immediately.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureActionPhase-WILL_END = 1--><!--Device-GestureActionPhase-WILL_END = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

