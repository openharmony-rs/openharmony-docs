# BlendApplyType

指示如何将指定的混合模式应用于视图的内容。

**起始版本：** 12

<!--Device-unnamed-declare enum BlendApplyType--><!--Device-unnamed-declare enum BlendApplyType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FAST

```TypeScript
FAST = 0
```

在目标图像上按顺序混合视图的内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendApplyType-FAST = 0--><!--Device-BlendApplyType-FAST = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN

```TypeScript
OFFSCREEN = 1
```

将此组件和子组件内容绘制到离屏画布上，然后整体进行混合。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendApplyType-OFFSCREEN = 1--><!--Device-BlendApplyType-OFFSCREEN = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

