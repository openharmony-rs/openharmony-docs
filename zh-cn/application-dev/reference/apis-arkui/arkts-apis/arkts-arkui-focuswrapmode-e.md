# FocusWrapMode

交叉轴方向键走焦模式枚举。

**起始版本：** 20

<!--Device-unnamed-declare enum FocusWrapMode--><!--Device-unnamed-declare enum FocusWrapMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

交叉轴方向键不允许换行。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FocusWrapMode-DEFAULT = 0--><!--Device-FocusWrapMode-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WRAP_WITH_ARROW

```TypeScript
WRAP_WITH_ARROW = 1
```

交叉轴方向键允许换行。

不规则单元格场景下，交叉轴方向键走焦时优先走到同一行的可获焦item。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FocusWrapMode-WRAP_WITH_ARROW = 1--><!--Device-FocusWrapMode-WRAP_WITH_ARROW = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

