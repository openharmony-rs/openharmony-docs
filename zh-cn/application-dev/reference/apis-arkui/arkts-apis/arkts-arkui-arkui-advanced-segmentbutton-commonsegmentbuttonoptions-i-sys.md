# CommonSegmentButtonOptions

定义分段按钮组件的可自定义的属性。

**起始版本：** 11

<!--Device-unnamed-interface CommonSegmentButtonOptions--><!--Device-unnamed-interface CommonSegmentButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CommonSegmentButtonOptions, SegmentButtonItemOptionsConstructorOptions, SegmentButtonIconTextItem, SegmentButtonItemOptions, SegmentButtonTextItem, CapsuleSegmentButtonOptions, SegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonItemTuple, SegmentButton, SegmentButtonItemArray, SegmentButtonItemOptionsArray, SegmentButtonIconItem, BorderRadiusMode, TabSegmentButtonConstructionOptions, TabSegmentButtonOptions, ItemRestriction, DimensionNoPercentage } from '@kit.ArkUI';
```

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

分段按钮组件的背景板的系统材质。不同系统材质包含不同的属性影响效果。传入材质后，SegmentButton的动效发生改变。对于胶囊类多选按钮（即type为"capsule"且multiply为true），该属性不生效。默认值：无材质效果。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonSegmentButtonOptions-backgroundSystemMaterial?: uiMaterial.Material--><!--Device-CommonSegmentButtonOptions-backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

