# TextSelectableMode

```TypeScript
declare enum TextSelectableMode
```

文本可选择、可获焦状态。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELECTABLE_UNFOCUSABLE

```TypeScript
SELECTABLE_UNFOCUSABLE = 0
```

文本可选择，但不可获焦，设置属性selection、bindSelectionMenu、copyOption不影响当前行为。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELECTABLE_FOCUSABLE

```TypeScript
SELECTABLE_FOCUSABLE = 1
```

文本可选择，可获焦并Touch后获得焦点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UNSELECTABLE

```TypeScript
UNSELECTABLE = 2
```

文本不可选择，不可获焦，设置属性selection、bindSelectionMenu、copyOption均不生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
