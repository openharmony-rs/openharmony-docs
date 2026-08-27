# CapsuleSegmentButtonConstructionOptions

用于构建胶囊类的SegmentButtonOptions对象。继承[CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md)。

**继承/实现关系：** CapsuleSegmentButtonConstructionOptions extends [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons: SegmentButtonItemTuple
```

按钮信息。

**类型：** [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiply

```TypeScript
multiply?: boolean
```

是否可以多选。默认值：false值为undefined时，按默认值处理。true表示可以多选，false表示不可以多选。

**类型：** boolean

**默认值：** false

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
