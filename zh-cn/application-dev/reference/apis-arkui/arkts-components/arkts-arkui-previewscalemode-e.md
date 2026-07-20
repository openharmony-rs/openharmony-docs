# PreviewScaleMode

预览图的缩放方式。

**起始版本：** 20

<!--Device-unnamed-declare enum PreviewScaleMode--><!--Device-unnamed-declare enum PreviewScaleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

预览图根据[Placement](../arkts-apis/arkts-arkui-placement-e.md)自动调整预览图宽高及缩放。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewScaleMode-AUTO = 0--><!--Device-PreviewScaleMode-AUTO = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONSTANT

```TypeScript
CONSTANT = 1
```

预览图不缩放，大小保持不变。最终仍会受到安全区的限制而出现压缩、裁剪。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewScaleMode-CONSTANT = 1--><!--Device-PreviewScaleMode-CONSTANT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MAINTAIN

```TypeScript
MAINTAIN = 2
```

预览图缩放时保持宽高比。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewScaleMode-MAINTAIN = 2--><!--Device-PreviewScaleMode-MAINTAIN = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

