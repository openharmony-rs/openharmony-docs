# CutEvent

定义用户剪切事件。

**起始版本：** 12

<!--Device-unnamed-declare interface CutEvent--><!--Device-unnamed-declare interface CutEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## preventDefault

```TypeScript
preventDefault?: Callback<void>
```

阻止系统默认剪切事件。

省略时，执行系统默认剪切行为。

**类型：** Callback<void>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CutEvent-preventDefault?: Callback<void>--><!--Device-CutEvent-preventDefault?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

