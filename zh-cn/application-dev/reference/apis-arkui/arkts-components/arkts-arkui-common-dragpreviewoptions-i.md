# DragPreviewOptions

设置拖拽过程中预览图处理模式及数量角标的显示。

**起始版本：** 11

<!--Device-unnamed-declare interface DragPreviewOptions--><!--Device-unnamed-declare interface DragPreviewOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DragPreviewMode | Array<DragPreviewMode>
```

表示拖拽过程中背板图处理模式。

默认值：DragPreviewMode.AUTO

当组件同时设置DragPreviewMode.AUTO和其它枚举值时，以DragPreviewMode.AUTO为准，其它枚举值设置无效。

**类型：** DragPreviewMode | Array<DragPreviewMode>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreviewOptions-mode?: DragPreviewMode | Array<DragPreviewMode>--><!--Device-DragPreviewOptions-mode?: DragPreviewMode | Array<DragPreviewMode>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modifier

```TypeScript
modifier?: ImageModifier
```

用于配置拖拽背板图的样式Modifier对象，可使用图片组件所支持的属性和样式来配置背板图样式（参考示例6），当前支持透明度，阴影，背景模糊度，圆角，材质效果。文本拖拽只支持默认效果，不支持通过modifier进行自定义。

1.透明度。

通过[opacity](arkts-arkui-common-commonmethod-c.md#opacity-1)设置不透明度，不透明度的取值范围为0-1。设置0或不设置时采用背板图透明度的默认值0.95，设置1或异常值时不透明。

2.阴影。

通过[shadow](arkts-arkui-common-commonmethod-c.md#shadow-1)设置阴影。

3.背景模糊度。

通过[backgroundEffect](arkts-arkui-common-commonmethod-c.md#backgroundeffect-1)或[backgroundBlurStyle](arkts-arkui-common-commonmethod-c.md#backgroundblurstyle-1)设置背景模糊度，如果两者同时设置，以后设置的属性为准。

4.圆角。

通过[border](arkts-arkui-common-commonmethod-c.md#border-1)或[borderRadius](arkts-arkui-common-commonmethod-c.md#borderradius-1)设置圆角，当同时在mode和modifier中设置圆角，mode设置的圆角显示优先级低于modifier设置。

5.材质效果，从API版本26.0.0开始支持。

通过[systemMaterial](arkts-arkui-common-commonmethod-c.md#systemmaterial-1)设置系统材质效果。

默认值：空，拖拽背板不设置背板图样式。

**说明：**

1.若节点已设置背景模糊或材质效果，直接用作拖拽预览会导致截图包含这些效果，与拖拽modifier属性冲突。建议使用[dragPreview](arkts-arkui-common-commonmethod-c.md#dragpreview-1)自定义不包含背景模糊和材质效果的预览。

2.[ImmersiveMaterial](@ohos.arkui.uiMaterial:ImmersiveMaterial#immersivematerial)的[colorInvert](@ohos.arkui.uiMaterial:ImmersiveOptions#colorInvert)参数在拖拽中不生效。

**类型：** ImageModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreviewOptions-modifier?: ImageModifier--><!--Device-DragPreviewOptions-modifier?: ImageModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## numberBadge

```TypeScript
numberBadge?: boolean | number
```

控制数量角标是否显示，或强制设置显示的数量。当设置数量角标时取值范围为[0，2<sup>31</sup>-1]，超过取值范围时会按默认状态处理。当设置为浮点数时，只显示整数部分。

**说明：**

在多选拖拽场景，需通过该接口设置拖拽对象的数量。

默认值：true。

**类型：** boolean | number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreviewOptions-numberBadge?: boolean | number--><!--Device-DragPreviewOptions-numberBadge?: boolean | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sizeChangeEffect

```TypeScript
sizeChangeEffect?: DraggingSizeChangeEffect
```

用于选择长按浮起图与拖拽预览图过渡效果。

默认值：DraggingSizeChangeEffect.DEFAULT。

**类型：** DraggingSizeChangeEffect

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreviewOptions-sizeChangeEffect?: DraggingSizeChangeEffect--><!--Device-DragPreviewOptions-sizeChangeEffect?: DraggingSizeChangeEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

