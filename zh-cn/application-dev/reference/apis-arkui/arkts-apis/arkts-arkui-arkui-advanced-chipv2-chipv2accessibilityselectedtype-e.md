# ChipV2AccessibilitySelectedType

ChipV2AccessibilitySelectedType是ChipV2可指定的选中态类型，用于控制无障碍辅助服务如何向用户传达组件的选中状态。不同的选中态类型提供了不同的语义和用户体验。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare enum ChipV2AccessibilitySelectedType--><!--Device-unnamed-export declare enum ChipV2AccessibilitySelectedType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CLICKED

```TypeScript
CLICKED = 0
```

单击型。组件不向无障碍辅助服务报告任何选中状态，仅作为可单击组件使用。适用于执行某个操作但不保持状态的场景，如普通按钮。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2AccessibilitySelectedType-CLICKED = 0--><!--Device-ChipV2AccessibilitySelectedType-CLICKED = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CHECKED

```TypeScript
CHECKED = 1
```

复选型。组件通过accessibilityChecked属性向无障碍辅助服务报告选中状态。适用于多选场景，如标签筛选、属性选择等。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2AccessibilitySelectedType-CHECKED = 1--><!--Device-ChipV2AccessibilitySelectedType-CHECKED = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELECTED

```TypeScript
SELECTED = 2
```

单选型。组件通过accessibilitySelected属性向无障碍辅助服务报告选中状态。适用于表示当前选中项的场景，如导航栏标签、单选列表 项等。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2AccessibilitySelectedType-SELECTED = 2--><!--Device-ChipV2AccessibilitySelectedType-SELECTED = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

