# SegmentButtonItemOptions

分段按钮中的按钮选项。

**起始版本：** 11

<!--Device-unnamed-declare class SegmentButtonItemOptions--><!--Device-unnamed-declare class SegmentButtonItemOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CommonSegmentButtonOptions, SegmentButtonItemOptionsConstructorOptions, SegmentButtonIconTextItem, SegmentButtonItemOptions, SegmentButtonTextItem, CapsuleSegmentButtonOptions, SegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonItemTuple, SegmentButton, SegmentButtonItemArray, SegmentButtonItemOptionsArray, SegmentButtonIconItem, BorderRadiusMode, TabSegmentButtonConstructionOptions, TabSegmentButtonOptions, ItemRestriction, DimensionNoPercentage } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: SegmentButtonItemOptionsConstructorOptions)
```

构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonItemOptions-constructor(options: SegmentButtonItemOptionsConstructorOptions)--><!--Device-SegmentButtonItemOptions-constructor(options: SegmentButtonItemOptionsConstructorOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SegmentButtonItemOptionsConstructorOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsconstructoroptions-i.md) | 是 | 单个分段按钮的配置选项，包含图标、文本、无障碍属性等配置信息。 |

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

无障碍说明，为用户解释组件操作，设置详细解释文本，帮助用户理解操作后果。若组件有文本和无障碍说明，选中时先播报文本，再播报无障碍说明。

默认值：空字符串。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**默认值：** ""

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonItemOptions-accessibilityDescription?: ResourceStr--><!--Device-SegmentButtonItemOptions-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

无障碍重要性，控制当前组件是否可被无障碍辅助服务识别。

支持的值为:

"auto"：当前组件可被无障碍辅助服务所识别。

"yes"：当前组件可被无障碍辅助服务所识别。

"no"：当前组件不可被无障碍辅助服务所识别。

"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。

默认值："auto"

值为undefined时，按默认值处理。

**类型：** string

**默认值：** "auto"

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonItemOptions-accessibilityLevel?: string--><!--Device-SegmentButtonItemOptions-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

未选中态的按钮图标。

默认值：不显示未选中态的按钮图标。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonItemOptions-icon?: ResourceStr--><!--Device-SegmentButtonItemOptions-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconAccessibilityText

```TypeScript
iconAccessibilityText?: ResourceStr
```

未选中态按钮图标的无障碍文本。

默认值：空字符串。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**默认值：** ""

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonItemOptions-iconAccessibilityText?: ResourceStr--><!--Device-SegmentButtonItemOptions-iconAccessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIcon

```TypeScript
selectedIcon?: ResourceStr
```

选中态的按钮图标。

默认值：不显示选中态按钮图标。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonItemOptions-selectedIcon?: ResourceStr--><!--Device-SegmentButtonItemOptions-selectedIcon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIconAccessibilityText

```TypeScript
selectedIconAccessibilityText?: ResourceStr
```

选中态按钮图标的无障碍文本。

默认值：空字符串。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**默认值：** ""

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonItemOptions-selectedIconAccessibilityText?: ResourceStr--><!--Device-SegmentButtonItemOptions-selectedIconAccessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

按钮文本。

默认值：空字符串。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButtonItemOptions-text?: ResourceStr--><!--Device-SegmentButtonItemOptions-text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

