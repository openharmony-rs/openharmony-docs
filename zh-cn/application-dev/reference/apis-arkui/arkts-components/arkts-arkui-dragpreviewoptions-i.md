# DragPreviewOptions

设置拖拽过程中预览图处理模式及数量角标的显示。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-unnamed-declare interface DragPreviewOptions--><!--Device-unnamed-declare interface DragPreviewOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DragPreviewMode | Array<DragPreviewMode>
```

表示拖拽过程中背板图处理模式。 默认值：DragPreviewMode.AUTO 当组件同时设置DragPreviewMode.AUTO和其它枚举值时，以DragPreviewMode.AUTO为准，其它枚举值设置无效。

**类型：** DragPreviewMode \| Array&lt;DragPreviewMode&gt;

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreviewOptions-mode?: DragPreviewMode | Array<DragPreviewMode>--><!--Device-DragPreviewOptions-mode?: DragPreviewMode | Array<DragPreviewMode>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## numberBadge

```TypeScript
numberBadge?: boolean | number
```

控制数量角标是否显示，或强制设置显示的数量。当设置数量角标时取值范围为[0，2\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_31\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_-1]，超过取值范围时会按默认状态处理。当设置为浮点数时，只显示整数部分。 **说明：** 在多选拖拽场景，需通过该接口设置拖拽对象的数量。 默认值：true。

**类型：** boolean \| number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreviewOptions-numberBadge?: boolean | number--><!--Device-DragPreviewOptions-numberBadge?: boolean | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sizeChangeEffect

```TypeScript
sizeChangeEffect?: DraggingSizeChangeEffect
```

用于选择长按浮起图与拖拽预览图过渡效果。 默认值：DraggingSizeChangeEffect.DEFAULT。

**类型：** DraggingSizeChangeEffect

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreviewOptions-sizeChangeEffect?: DraggingSizeChangeEffect--><!--Device-DragPreviewOptions-sizeChangeEffect?: DraggingSizeChangeEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

