# HandednessFollowMode

```TypeScript
export enum HandednessFollowMode
```

表示对话框跟随惯用手的方式。

**起始版本：** 26.1.0

<!--Device-unnamed-export enum HandednessFollowMode--><!--Device-unnamed-export enum HandednessFollowMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_ANCHOR

```TypeScript
FOLLOW_ANCHOR = 1
```

对话框跟随触发它的组件（最近交互的组件）的位置。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-HandednessFollowMode-FOLLOW_ANCHOR = 1--><!--Device-HandednessFollowMode-FOLLOW_ANCHOR = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_GRIP_HAND

```TypeScript
FOLLOW_GRIP_HAND = 2
```

对话框跟随握持手（握持设备的手，区别于与屏幕交互的操作手）。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-HandednessFollowMode-FOLLOW_GRIP_HAND = 2--><!--Device-HandednessFollowMode-FOLLOW_GRIP_HAND = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

不适配。对话框保持当前布局。默认值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-HandednessFollowMode-NONE = 0--><!--Device-HandednessFollowMode-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
