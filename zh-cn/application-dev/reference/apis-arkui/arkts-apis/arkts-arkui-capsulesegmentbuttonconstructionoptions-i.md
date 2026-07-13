# CapsuleSegmentButtonConstructionOptions

用于构建胶囊类的SegmentButtonOptions对象。

继承[CommonSegmentButtonOptions](arkts-arkui-commonsegmentbuttonoptions-i.md)。

**继承/实现关系：** CapsuleSegmentButtonConstructionOptions extends [CommonSegmentButtonOptions](arkts-arkui-commonsegmentbuttonoptions-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons: SegmentButtonItemTuple
```

按钮信息。

**类型：** SegmentButtonItemTuple

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiply

```TypeScript
multiply?: boolean
```

是否可以多选。

默认值：false

值为undefined时，按默认值处理。

true表示可以多选，false表示不可以多选。

**类型：** boolean

**默认值：** false

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

