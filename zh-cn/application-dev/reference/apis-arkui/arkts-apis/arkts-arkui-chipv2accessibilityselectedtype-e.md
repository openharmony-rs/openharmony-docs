# ChipV2AccessibilitySelectedType

AccessibilitySelectedType是Chip可指定的选中态类型，用于控制无障碍服务如何向用户传达组件的选中状态。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CLICKED

```TypeScript
CLICKED = 0
```

单击型。组件不向无障碍服务报告任何选中状态，仅作为可单击组件使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CHECKED

```TypeScript
CHECKED = 1
```

复选型。组件通过 accessibilityChecked 属性向无障碍服务报告选中状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELECTED

```TypeScript
SELECTED = 2
```

单选型。组件通过 accessibilitySelected 属性向无障碍服务报告选中状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

