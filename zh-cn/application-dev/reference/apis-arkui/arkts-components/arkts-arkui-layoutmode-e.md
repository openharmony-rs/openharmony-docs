# LayoutMode

页签内容排布方式枚举。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare enum LayoutMode--><!--Device-unnamed-declare enum LayoutMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

若页签宽度大于104vp，页签内容为左右排布（图标在左，文字在右），否则页签内容为上下排布（图标在上，文字在下）。仅TabBar为垂直模式或Fixed水平模式时有效。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LayoutMode-AUTO = 0--><!--Device-LayoutMode-AUTO = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## VERTICAL

```TypeScript
VERTICAL = 1
```

页签内容上下排布，图标在上，文字在下。适用于页签宽度有限、需要节省空间的场景。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LayoutMode-VERTICAL = 1--><!--Device-LayoutMode-VERTICAL = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HORIZONTAL

```TypeScript
HORIZONTAL = 2
```

页签内容左右排布，图标在左，文字在右。适用于页签宽度充足、需要展示更多内容的场景。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LayoutMode-HORIZONTAL = 2--><!--Device-LayoutMode-HORIZONTAL = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

